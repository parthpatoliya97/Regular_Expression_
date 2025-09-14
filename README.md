### Regular_Expression

#### Meta Characters :-
- []	A set of characters	
- \	Signals a special sequence (can also be used to escape special characters)		
- .	Any character (except newline character)	
- ^	Starts with		
- $	Ends with		
- *	Zero or more occurrences	
- +	One or more occurrences		
- ?	Zero or one occurrences		
- {}Exactly the specified number of occurrences		
- |	Either or

#### 1.Find all lower case characters alphabetically between "a" and "m":
```python
txt = "The rain in Spain"
x = re.findall("[a-m]", txt)
print(x)
```


#### 2.Find all digit characters:
```python
txt = "That will be 59 dollars"
x = re.findall("\d", txt)
print(x)
```

#### 3.Search for a sequence that starts with "he", followed by two (any) characters, and an "o":
```python
txt = "hello planet"
x = re.findall("he..o", txt)
print(x)
```

#### 4.Check if the string starts with 'hello':
```python
txt = "hello planet"
x = re.findall("^hello", txt)
if x:
  print("Yes, the string starts with 'hello'")
else:
  print("No match")
```

#### 5.Check if the string ends with 'planet':
```python
txt = "hello planet"
x = re.findall("planet$", txt)
if x:
  print("Yes, the string ends with 'planet'")
else:
  print("No match")
```


#### 6.Search for a sequence that starts with "he", followed by 0 or more  (any) characters, and an "o":
```python
txt = "hello planet"
x = re.findall("he.*o", txt)
print(x)
```

#### 7.Search for a sequence that starts with "he", followed by 1 or more  (any) characters, and an "o":
```python
txt = "hello planet"
x = re.findall("he.+o", txt)
print(x)
```

# 8.Search for a sequence that starts with "he", followed by 0 or 1  (any) character, and an "o":
- This time we got no match, because there were not zero, not one, but two characters between "he" and the "o"
```python
txt = "hello planet"
x = re.findall("he.?o", txt)
print(x)
```


#### 9.Search for a sequence that starts with "he", followed excactly 2 (any) characters, and an "o":
```python
txt = "hello planet"
x = re.findall("he.{2}o", txt)
print(x)
```

#### 10.Check if the string contains either "falls" or "stays":
```python
txt = "The rain in Spain falls mainly in the plain!"
x = re.findall("falls|stays", txt)

print(x)
if x:
  print("Yes, there is at least one match!")
else:
  print("No match")
```

#### 1.mobile number starts with 8 or 9 and total digits=10
```regex
 [89][0-9]{9}
```

#### 2.first character uppercase,contains lowercase alphabets only one digits allowed in between
```regex
 [A-Z][a-z]*[0-9][a-z]*
 ```

#### 3.E-mail ID(abcd123@gmail.com)
```regex
 [a-z0-9_\-\.]+[@][a-z]+[\.][a-z]{2,3}
```
 
#### 4.Indian mobile number (starts with 6–9, 10 digits):
```regex
 ^[6-9][0-9]{9}$
```

#### 5.International format (+CountryCode followed by 10 digits):
```regex
 ^\+[1-9][0-9]{1,3}[0-9]{10}$
```

#### 6.Simple email validation
```regex
 ^[a-z0-9.\-\_]+@[a-z0-9]+\.[a-z]{2,}$
 ```

#### 7.Corporate email (must end with @company.com)
```regex
 ^[a-z0-9.-_]+@company\.com$
```

#### 8.First name (only alphabets, capital first letter)
```regex
^[A-Z][a-z]+$
```

#### 9.Full name (first + last, capital first letters):
```regex
^[A-Z][a-z]+ [A-Z][a-z]+$
```

#### 10.Username (5–15 chars, alphanumeric + underscore)
```regex
^[a-zA-Z0-9_]{5,15}$
```

#### 8.Strong password (min 8, at least 1 upper, 1 lower, 1 digit, 1 special)

-  ?=: This is the magic phrase that means "look ahead and check if this exists."

-  .*: This means "any character (.) zero or more times (*)." It's like saying "scan forward through the password, no matter what's in it."

-  [a-z]: This means "find one lowercase letter between a and z."

-  It starts at the beginning (^).

-  It calls the first lookahead guard: (?=.*[a-z]). This guard looks through the whole string and reports if it finds a lowercase letter. If not, the password fails immediately.

-  It calls the second guard: (?=.*[A-Z]). Does it find an uppercase letter?

-  It calls the third guard: (?=.*\d)`. Does it find a number?

-  It calls the fourth guard: (?=.*[@$!%*?&]). Does it find a special symbol?

-  If all four guards give a thumbs-up, the computer finally moves to the main rule.

-  The main rule [A-Za-z\d@$!%*?&]{8,}$ checks two things:

-  Are ALL the characters in the password from the allowed list? (No spaces or other weird symbols).

-  Is the password at least 8 characters long?

-  If both these are true, and the computer has reached the end of the string ($), the password is VALID!
```regex
^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$
```

#### 9.Date (DD/MM/YYYY)

- Option 1: 0[1-9]

-  0: The character must be a 0.
-  [1-9]: The next character must be a digit from 1 to 9.
-  What it matches: 01, 02, 03, ... 09 (the 1st through the 9th).
-  The robot thinks: "Is the day a number between 01 and 09?"

-  Option 2: [12][0-9]

-  [12]: The first character must be either a 1 or a 2.
-  [0-9]: The next character must be any digit from 0 to 9.
-  What it matches: 10, 11, 12, ... 29 (the 10th through the 29th).
-  The robot thinks: "Is the day a number between 10 and 29?"

-  Option 3: 3[01]

-  3: The first character must be a 3.
-  [01]: The next character must be either a 0 or a 1.
-  What it matches: 30, 31 (the 30th and 31st).
-  The robot thinks: "Is the day the 30th or the 31st?"
```regex
^(0[1-9]|[12][0-9]|3[01])/(0[1-9]|1[0-2])/[0-9]{4}$
```

#### 10.Time (HH:MM 24-hour)
```regex
[01][0-9][02][0-3]:[0-5][0-9]
```

#### 11.File with .pdf extension
```regex
^.*\.pdf$
```

#### 12.Image files (jpg|jpeg|png|gif)
```regex
%.*\.(jpg|jpeg|png|gif)$
```

#### 13.CSV or Excel files:
```regex
^.*\.(csv|xls|xlsx)$
```

#### 14.Integer (positive or negative)
```regex
^-?\[0-9]+$
```

#### 15.Decimal number (with 2 decimal places)
```regex
^[0-9]+\.[0-9]{2}$
```

#### 16.Currency (₹, $, €, followed by numbers)
```regex
^[₹$€]\[0-9]+(\.[0-9])?$
```
  
#### 17.PAN card (ABCDE1234F format)
```regex
^[A-Z]{5}[0-9]{4}[A-Z]{1}$
```

#### 18.Aadhaar number (12 digits)
```regex
^[0-9]{12}$
```

#### 19.Passport number (Indian, 1 letter + 7 digits)
```regex
^[A-Z][0-9]{7}$
```

#### 20.Pin code (India, 6 digits)
```regex
^[1-9][0-9]{5}$
```

#### 21.Credit card number (16 digits, grouped by 4)
```regex
^(\d{4}[- ]?){3}\d{4}$
```

#### 22.GST number (15 chars, alphanumeric)
```regex
^[0-9]{2}[A-Z]{5}[0-9]{4}[A-Z]{1}[1-9A-Z]{1}Z[0-9A-Z]{1}$
```

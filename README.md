# 🐍 Python & Data Analytics Quick Reference

A highly scannable cheat sheet for data cleaning, text transformation, and validation syntax. Built for quick reference during coding sessions and data pipeline development.

---

## 1. Types & Inspection

### `type()`
* **Definition:** A built-in function that returns the data type of an object.
* **Use Case:** Debugging data pipelines when a column contains unexpected mixed data types (like integers mixed with strings).
* **Example:**
  ```python
  value = "100"
  print(type(value))  # Output: <class 'str'>

### `str()`
* **Definition:** Converts a given value into a string data type.
* **Use Case:** Typecasting numerical IDs or ZIP codes into strings so you can perform string operations on them (like concatenation or checking length).
* **Example:**
  ```python
  zip_code = 92101
  print(str(zip_code))  # Output: "92101"

## 2. Math

### `len()`
* **Definition:** Returns the number of items (characters) in a string or elements in a list.
* **Use Case:** Validating data constraints, like checking if a password meets a minimum length or if a phone number has the correct number of digits.
* **Example:**
  ```python
  username = "olsen_wu"
  print(len(username))  # Output: 8

### `count()`
* **Definition:** Counts how many times a specific substring appears in a string.
* **Use Case:** Parsing text data to find the frequency of specific characters, tags, or keywords.
* **Example:**
  ```python
  log_entry = "ERROR: Connection failed. ERROR: Timeout."
  print(log_entry.count("ERROR"))  # Output: 2

## 3. Transformations

### `replace()`
* **Definition:** Replaces all occurrences of a specified substring with another substring.
* **Use Case:** Standardizing text or removing unwanted characters from financial data (like removing dollar signs or commas from a price column).
* **Example:**
  ```python
  price = "$1,250.00"
  clean_price = price.replace("$", "").replace(",", "")
  print(clean_price)  # Output: "1250.00"

### `split()`
* **Definition:** Breaks a string into a list of substrings based on a specified delimiter (default is whitespace).
* **Use Case:** Parsing delimited data strings, like separating a full name into first and last components.
* **Example:**
  ```python
  full_name = "Olsen Wu"
  print(full_name.split(" "))  # Output: ['Olsen', 'Wu']

## 4. Cleaning

### `lstrip()`
* **Definition:** Removes leading characters (whitespace by default) from the left side of a string.
* **Use Case:** Cleaning text alignment issues from imported files.
* **Example:**
  ```python
  text = "   Data Analyst"
  print(text.lstrip())  # Output: "Data Analyst"

### `rstrip()`
* **Definition:** Removes trailing characters (whitespace by default) from the right side of a string.
* **Use Case:** Stripping hidden newline characters (\n) or trailing spaces from rows read from a text file.
* **Example:**
  ```python
  text = "Snowflake \n"
  print(text.rstrip())  # Output: "Snowflake"

### `strip()`
* **Definition:** Removes both leading and trailing whitespace/characters from a string.
* **Use Case:** A "must-use" method when cleaning user input or database text fields to ensure accidental spaces don't ruin table joins or filters.
* **Example:**
  ```python
  dirty_input = "  dbt  "
  print(dirty_input.strip())  # Output: "dbt"

### `lower()`
* **Definition:** Converts all uppercase characters in a string to lowercase.
* **Use Case:** Standardizing strings before comparison or filtering, since Python text matching is case-sensitive ("Python" != "python").
* **Example:**
  ```python
  email = "Olsen.Wu@CNB.com"
  print(email.lower())  # Output: "olsen.wu@cnb.com"

### `upper()`
* **Definition:** Converts all lowercase characters in a string to uppercase.
* **Use Case:** Standardizing state abbreviations, currency codes (USD, EUR), or stock tickers.
* **Example:**
  ```python
  ticker = "btc"
  print(ticker.upper())  # Output: "BTC"

## 5. Search

### `startswith()`
* **Definition:** Returns True if a string begins with a specified prefix; otherwise, returns False.
* **Use Case:** Filtering logs or URLs (e.g., checking if a URL is secure by verifying it starts with https).
* **Example:**
  ```python
  url = "[https://github.com](https://github.com)"
  print(url.startswith("https"))  # Output: True

### `endswith()`
* **Definition:** Returns True if a string ends with a specified suffix; otherwise, returns False.
* **Use Case:** Scanning a file directory to find all files of a specific format (like .csv or .sql).
* **Example:**
  ```python
  filename = "monthly_active_users.sql"
  print(filename.endswith(".sql"))  # Output: True

### `find()`
* **Definition:** Searches a string for a specified substring and returns the starting index of its first position. Returns -1 if the text is not found.
* **Use Case:** Locating specific marker keywords within raw text fields when you don't need a heavy regex pattern.
* **Example:**
  ```python
  comment = "Excellent data pipeline project."
  print(comment.find("data"))  # Output: 10

## 6. Validation

### `isalpha()`
* **Definition:** Returns True if all characters in the string are alphabetic letters (A-Z) and there is at least one character.
* **Use Case:** Validating names or alphabetic codes to ensure they don't contain accidental numbers or punctuation.
* **Example:**
  ```python
  name = "Olsen"
  print(name.isalpha())  # Output: True

### `isnumeric()`
* **Definition:** Returns True if all characters in the string are numeric unicode characters (0-9).
* **Use Case:** Validating text fields that should only contain digits (like account numbers or IDs) before trying to convert them to integers.
* **Example:**
  ```python
  account_str = "4457765"
  print(account_str.isnumeric())  # Output: True

---

## 7. Single Value Conversion

### `int()`
* **Definition:** Converts a number or a valid numeric string into an integer (whole number), truncating any decimal parts.
* **Use Case:** Converting floating-point metrics or numeric string IDs into integers for database key matching or clean counting.
* **Example:**
  ```python
  value = "4457765"
  print(int(value))  # Output: 4457765

### `float()`
* **Definition:** Converts an integer or a valid numeric string into a floating-point number (decimal).
* **Use Case:** Ensuring integer values (like transaction counts) are converted to decimals before division to prevent unintended integer truncation during financial calculations.
* **Example:**
  ```python
  amount = 250
  print(float(amount))  # Output: 250.0

### `complex()`
* **Definition:** Creates a complex number with a real and an imaginary part (written as real + imagj).
* **Use Case:** Used in advanced scientific calculations, signal processing, or complex spatial engineering algorithms.
* **Example:**
  ```python
  num = complex(3, 4)
  print(num)  # Output: (3+4j)

## 8. Rounding & Absolute Values

### `abs()`
* **Definition:** Returns the absolute (positive) value of a given number, removing any negative signs.
* **Use Case:** Finding the magnitude of variance or calculation errors between actual numbers and forecasts without letting negative differences cancel out positive ones.
* **Example:**
  ```python
  variance = -15.4
  print(abs(variance))  # Output: 15.4

### `round()`
* **Definition:** Rounds a floating-point number to a specified number of decimals (defaults to 0 decimals if not specified).
* **Use Case:** Cleaning up messy, multi-decimal float averages into presentation-ready KPIs or currency summaries.
* **Example:**
  ```python
  avg_price = 45.6782
  print(round(avg_price, 2))  # Output: 45.68

### `ceil()`
* **Definition:** Part of the math module; rounds a decimal number up to the nearest whole integer, no matter how small the decimal part is.
* **Use Case:** Determining pagination requirements or hardware allocation (e.g., if a process requires 4.1 servers, you must provision 5 servers).
* **Example:**
  ```python
  avg_price = 45.6782
  print(round(avg_price, 2))  # Output: 45.68

### `floor()`
* **Definition:** Part of the math module; rounds a decimal number down to the nearest whole integer.
* **Use Case:** Splitting assets or calculating full completed cycles (e.g., determining how many full blocks of items a user can afford with a specific budget).
* **Example:**
  ```python
  import math
  purchasable_items = 7.9
  print(math.floor(purchasable_items))  # Output: 7

### `trunc()`
* **Definition:** Part of the math module; cuts off all decimal digits, returning just the whole number integer part without rounding.
* **Use Case:** Isolating the base integer component of a calculation while ignoring any fractions or decimals, preserving negative structures cleanly.
* **Example:**
  ```python
  import math
  negative_value = -3.99
  print(math.trunc(negative_value))  # Output: -3

## 9. Random Number Generation

### `random()`
* **Definition:** Part of the random module; generates a random floating-point number between 0.0 and 1.0.
* **Use Case:** Simulating percentage probabilities, creating train/test data splits, or introducing variability in A/B testing frameworks.
* **Example:**
  ```python
  import random
  print(random.random())  # Example Output: 0.47281938

### `randint()`
* **Definition:** Part of the random module; generates a random floating-point number between 0.0 and 1.0.
* **Use Case:** Simulating percentage probabilities, creating train/test data splits, or introducing variability in A/B testing frameworks.
* **Example:**
  ```python
  import random
  print(random.random())  # Example Output: 0.47281938

## 10. Numerical Validation

### `is_integer()`
* **Definition:** A float method that returns True if a floating-point number is a whole number (has no fractional value).
* **Use Case:** Sanity-checking calculated data yields to verify if they represent clean units before converting them from floats to strict database integers.
* **Example:**
  ```python
  val_one = 15.0
  val_two = 15.5
  print(val_one.is_integer())  # Output: True
  print(val_two.is_integer())  # Output: False

### `isinstance()`
* **Definition:** Checks if an object belongs to a specified data type or class, returning True or False.
* **Use Case:** Writing resilient, defensive ETL code that checks data types at run-time before attempting execution methods that might crash the script.
* **Example:**
  ```python
  user_input = 500
  print(isinstance(user_input, int))  # Output: True

---

## 11. Boolean Evaluation

### `bool()`
* **Definition:** Converts a given value into a boolean (`True` or `False`). Empty items, `0`, `None`, and empty strings evaluate to `False`, while non-empty structures and non-zero numbers evaluate to `True`.
* **Use Case:** Sanity-checking if a list, dictionary, or text string pulled from an API contains actual data before triggering downstream processing steps.
* **Example:**
  ```python
  empty_list = []
  active_user = "olsen_wu"
  print(bool(empty_list))   # Output: False
  print(bool(active_user))  # Output: True

### `any()`
* **Definition:** Checks an iterable (like a list or tuple) and returns True if at least one element evaluates to True. If the iterable is completely empty, it returns False.
* **Use Case:** Flagging transactions or account activities where multiple compliance validation criteria are checked, and hitting even a single rule triggers an audit alert.
* **Example:**
  ```python
  # Checks if any log flags a high security risk
  security_flags = [False, False, True, False]
  print(any(security_flags))  # Output: True

### `all()`
* **Definition:** Checks an iterable and returns True only if every single element inside it evaluates to True (or if the iterable is completely empty).
* **Use Case:** Verifying mandatory database field requirements during data quality checks (e.g., ensuring all columns pass their non-null conditions before pushing a pipeline forward).
* **Example:**
  ```python
  row_data_valid = [True, True, True, True]
  print(all(row_data_valid))  # Output: True

---

## 12. Structural Pattern Matching

### `match case`
* **Definition:** A structural pattern matching feature (introduced in Python 3.10) that functions like a highly advanced switch-case statement. It matches a variable against multiple structural patterns until it finds a hit.
* **Use Case:** Replacing long, repetitive `if-elif-else` blocks when handling incoming pipeline events, API response status codes, or error logs that require different operational logic based on their text values.
* **Example:**
  ```python
  # Handling server response tracking status codes
  status_code = 404

  match status_code:
      case 200:
          print("Success: Data loaded cleanly.")
      case 400:
          print("Error: Bad API request pattern.")
      case 404:
          print("Error: Target database endpoint not found.")
      case 500 | 503: # The | symbol allows matching multiple conditions at once
          print("Error: Server infrastructure failure.")
      case _: # The underscore (_) acts as a wildcard catch-all (like 'else')
          print("Error: Encountered an unknown status tracking code.")
          
  # Output: "Error: Target database endpoint not found."

---

### `isalnum()`
* **Definition:** Returns `True` if all characters in the string are alphanumeric (either letters or numbers) and there is at least one character. It returns `False` if the string contains spaces, punctuation, symbols, or is completely empty.
* **Use Case:** Stripping or validating input strings (like usernames or raw identifiers) to ensure special characters or punctuation marks haven't slipped in, or checking the boundaries of an input field like an email's first and last characters.
* **Example:**
  ```python
  username = "olsenwu101"
  bad_username = "olsen_wu!"
  
  print(username.isalnum())      # Output: True
  print(bad_username.isalnum())  # Output: False (Contains '_' and '!')

### Advanced f-string Expressions
* **Definition:** You can perform inline math, variable modifications, or string manipulations directly inside the curly braces `{}` of an f-string.
* **Use Case:** Creating readable outputs where data needs to be modified on the fly (e.g., calculating percentages, capitalizing names, or getting string lengths) without saving them to separate variables first.
* **Example:**
  ```python
  first_name = "olsen"
  raw_password = "  Thugmansion22!  "
  
  # Evaluating logic directly inside the curly braces
  print(f"Welcome, {first_name.capitalize()}!") 
  print(f"Your cleaned password length is: {len(raw_password.strip())} characters.")
  
  # Output:
  # Welcome, Olsen!
  # Your cleaned password length is: 14 characters.

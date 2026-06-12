---
title: "Simple Python question: variables and functions"
date: 2017-09-23
forum: Programming Talk
---

### Post by Drone4four on 2017-09-23
Have a look at this code snippet:
```

# !/usr/bin/env python3
a = str(&#8216;My dog&#8217;s name is George&#8217;)
b = str(''My cat&#8217;s name is Cathy")
print a
b.print()

```
If I comment out b.print(), a prints.  But I&#8217;m expecting b to print too because I&#8217;ve seen in other people&#8217;s code that variables can be referenced in front of a function separated by a period.

Here is the actual output:
```

$ python3 printing-experimenting.py
My dog&#8217;s name is George
Traceback (most recent call last):
  File "printing-experimenting.py", line 6, in <module>
    b.print()
AttributeError: 'str' object has no attribute 'print'
$ 

```
I gather that Python here is saying the print statement needs the variable to be present within the parentheses, but my question is: why? I&#8217;ve seen variables specified prior to function names.

Thanks for your attention.

---

### Post by holiday2 on 2017-09-23
Given the code as posted, the given output is impossible. 
The parse will fail on the second line where you close the single quote with the possessive's apostrophe. You could fix by wrapping the string in double quotes but you run into trouble later on anyway with the print statement that is invalid in python 3. 

Have you posted the wrong code? 

Please check.

---

### Post by spjackson on 2017-09-24
+1
If you post code that isn't the same as what you are asking about, then you make it more difficult for people to help you.
```

# !/usr/bin/env python3

```
Here, and in several other examples you have given, you have a space between # and !. This is incorrect. See [https://en.wikipedia.org/wiki/Shebang_(Unix)](https://en.wikipedia.org/wiki/Shebang_(Unix))
> 
```

Traceback (most recent call last):
  File "printing-experimenting.py", line 6, in <module>
    b.print()
AttributeError: 'str' object has no attribute 'print'


```
I gather that Python here is saying the print statement needs the variable to be present within the parentheses, but my question is: why? I’ve seen variables specified prior to function names.

No that isn't what it is saying. Your syntax is attempting to call b's print method. However, b is an object of type str and str does not have a print method. Compare:
```

#!/usr/bin/env python3

b = str("My cat's name is Cathy")
c = b.upper()
print(c)


```
b.upper() is ok because str does have an upper() method.

---

### Post by Drone4four on 2017-09-24
> **holiday2 said:**
> Given the code as posted, the given output is impossible. 
The parse will fail on the second line where you close the single quote with the possessive's apostrophe. You could fix by wrapping the string in double quotes but you run into trouble later on anyway with the print statement that is invalid in python 3. 
Have you posted the wrong code? 

**@holiday**, yeah I did post the wrong code as I did a sloppy job transposing from my text editor to the forums here.   It won’t happen again and I apologize for the confusion.

> **spjackson said:**
> 
```

# !/usr/bin/env python3

```
Here, and in several other examples you have given, you have a space between # and !. This is incorrect. See [https://en.wikipedia.org/wiki/Shebang_(Unix)](https://en.wikipedia.org/wiki/Shebang_(Unix))

Duly noted. I have corrected my shebangs in my code.

> **spjackson said:**
> If you post code that isn't the same as what you are asking about, then you make it more difficult for people to help you.
Thank you both for your patience with my newb coding practices.

> **spjackson said:**
> +1
No that isn't what it is saying. Your syntax is attempting to call b's print method. However, b is an object of type str and str does not have a print method. Compare:
```

#!/usr/bin/env python3
b = str("My cat's name is Cathy")
c = b.upper()
print(c)

```
b.upper() is ok because str does have an upper() method.
This is instructive.  Thank you for the clarification, **@spjackson**.

---


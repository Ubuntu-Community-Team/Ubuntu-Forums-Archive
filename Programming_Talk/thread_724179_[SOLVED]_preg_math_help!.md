---
title: "[SOLVED] preg math help!"
date: 2008-03-14
forum: Programming Talk
---

### Post by shedokan on 2008-03-14
I want to check if the user has entered chars other than:
A-Z
a-z
0-9
_

is that possible? and how?

by the way I'm using php.

---

### Post by Keith Hedger on 2008-03-14
```
ctype.h

isalnum Checks whether a character is alphanumeric (A-Z, a-z, 0-9)

    isalpha 

    iscntrl Checks whether a character is a control character or delete ( decimal 0-31 and 127) 

    isdigit Checks whether a character is a digit (0-9) 

    isgraph Checks whether a character is a printable character, excluding the space (decimal 32) 

    islower Checks whether a character is a lower case letter (a-z). 

    isprint Checks whether a character is printable (decimal 32-126). 

    ispunct Checks whether a character is punctuation (decimal 32-47, 58-63, 91-96, 123-126) 

    isspace Checks whether a character is white space - space, CR HT VT NL, FF. 

    isupper Checks whether a character is an upper case letter (A-Z). 

    isxdigit Checks whether a character is hex digit (0-9, A-F, a-f)
```

---

### Post by mssever on 2008-03-14
> **shedokan said:**
> I want to check if the user has entered chars other than:
A-Z
a-z
0-9
_

is that possible? and how?

You didn't specify the language you're using. The following regular expression would work in many languages: ```
^[^a-zA-Z0-9]*$
``` Many languages support shortcuts which would shorten the regexp. But this would work if your language uses regexps.

---

### Post by hod139 on 2008-03-14
If C++: [http://www.parashift.com/c++-faq-lite/input-output.html#faq-15.3](http://www.parashift.com/c++-faq-lite/input-output.html#faq-15.3)

---

### Post by shedokan on 2008-03-15
Sorry forgot, I'm using php

---

### Post by smartbei on 2008-03-15
This should work for you:
[php]
<?php
$pattern = "/^[0-9a-zA-Z]*$/";
$string = "testing213211c";
echo "Number of Results found: ", preg_match($pattern, $string, $matches);
?>
[/php]

---

### Post by shedokan on 2008-03-15
actually I took what mssever said and did it exacly like you did but thanks anyway.

---


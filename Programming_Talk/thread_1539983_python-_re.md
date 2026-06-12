---
title: "python- re"
date: 2010-07-27
forum: Programming Talk
---

### Post by ukripper on 2010-07-27
Guys need some help with forming regular expression in python 2.7. Below are lines from text file i need regular expression to replace matching strings to blanks, I want to replace "JACK PETER", "MIKE MR" and "PATRICK SNOW" to " " and shouldn't replace 101,AGH and 630:

```
000185 JACK Peter     101     15107.50          -            -       15107.50	
000481 MIKE MR        AGH     24790.51      8909.91          -       33700.42	
000647 PATRICK SNOW   630     10244.54          -            -       10244.54	
```


Thanks

---

### Post by simeon87 on 2010-07-27
I don't know about regular expressions but what's the regularity here? Is it always the case that the second and third items needs to be replaced? Or can there also be names that consist of one word or three or more words?

---

### Post by ghostdog74 on 2010-07-27
here's a reference. Its not Python, but you can adapt the regex pattern into Python re. 

```

$ cat file
000185 JACK Peter     101     15107.50          -            -       15107.50
000481 MIKE MR        AGH     24790.51      8909.91          -       33700.42
000647 PATRICK SNOW   630     10244.54          -            -       10244.54

$ sed -r 's/(.[^ \t]* )(.*)([ \t]+[0-9A-Z]{3}[ \t]+.*)/\1\3/' file
000185  101     15107.50          -            -       15107.50
000481  AGH     24790.51      8909.91          -       33700.42
000647  630     10244.54          -            -       10244.54


```

---

### Post by ukripper on 2010-07-27
> **ghostdog74 said:**
> here's a reference. Its not Python, but you can adapt the regex pattern into Python re. 

```

$ cat file
000185 JACK Peter     101     15107.50          -            -       15107.50
000481 MIKE MR        AGH     24790.51      8909.91          -       33700.42
000647 PATRICK SNOW   630     10244.54          -            -       10244.54

$ sed -r 's/(.[^ \t]* )(.*)([ \t]+[0-9A-Z]{3}[ \t]+.*)/\1\3/' file
000185  101     15107.50          -            -       15107.50
000481  AGH     24790.51      8909.91          -       33700.42
000647  630     10244.54          -            -       10244.54


```


nice work will try that.

Thanks

---

### Post by ukripper on 2010-07-27
> **simeon87 said:**
> I don't know about regular expressions but what's the regularity here? Is it always the case that the second and third items needs to be replaced? Or can there also be names that consist of one word or three or more words?

Regularity is any word (no digits) longer than 3 alphabets and can have space between letters

---

### Post by ukripper on 2010-07-27
> **ghostdog74 said:**
> here's a reference. Its not Python, but you can adapt the regex pattern into Python re. 

```

$ cat file
000185 JACK Peter     101     15107.50          -            -       15107.50
000481 MIKE MR        AGH     24790.51      8909.91          -       33700.42
000647 PATRICK SNOW   630     10244.54          -            -       10244.54

$ sed -r 's/(.[^ \t]* )(.*)([ \t]+[0-9A-Z]{3}[ \t]+.*)/\1\3/' file
000185  101     15107.50          -            -       15107.50
000481  AGH     24790.51      8909.91          -       33700.42
000647  630     10244.54          -            -       10244.54


```

Sorry sed regex in my test string didn't work with python.
here is the test case:
```

import re
testString = '000185 JACK Peter          630     15107.50          -            -       15107.50'
testReg = re.sub("s/(.[^ \t]* )(.*)([ \t]+[0-9A-Z]{3}[ \t]+.*)/\1\3/", " ",testString)
print testReg    

```

---

### Post by ghostdog74 on 2010-07-27
that's because of the syntax, not the regex. In Python's re, there is not s/// syntax, so remove them. I will give it to you this time. 

```

>>> import re
>>> testString = '000185 JACK Peter          630     15107.50          -            -       15107.50'
>>> re.sub("(.[^ \t]* )(.*)([ \t]+[0-9A-Z]{3}[ \t]+.*)", "\\1\\3",testString)
'000185  630     15107.50          -            -       15107.50'


```

please read up on regex and Python docs from now on.

---

### Post by ukripper on 2010-07-27
> **ghostdog74 said:**
> that's because of the syntax, not the regex. In Python's re, there is not s/// syntax, so remove them. I will give it to you this time. 

```

>>> import re
>>> testString = '000185 JACK Peter          630     15107.50          -            -       15107.50'
>>> re.sub("(.[^ \t]* )(.*)([ \t]+[0-9A-Z]{3}[ \t]+.*)", "\\1\\3",testString)
'000185  630     15107.50          -            -       15107.50'


```

please read up on regex and Python docs from now on.

Thank you very much. It seems to have worked.
I have been reading python docs but i am in learning stage so hopefully will get someday there and master re module:)

---


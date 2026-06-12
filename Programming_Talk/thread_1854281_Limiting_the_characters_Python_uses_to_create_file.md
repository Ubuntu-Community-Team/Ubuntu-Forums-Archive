---
title: "Limiting the characters Python uses to create files and directories"
date: 2011-10-04
forum: Programming Talk
---

### Post by fuzzman54 on 2011-10-04
I'm working on porting a xbmc plugin to the xbmc4xbox, and because the xbox uses fatx, it has some crippling limitations on what characters are allowed for filenames and directories. Basically what I want to do is change this code:

```
def CleanFileName(s, remove_year, use_encoding = False, use_blanks = True): 
    if remove_year: 
        s = s[0:len(s)-7] 
    s = s.replace(' (Eng subs)', '') 
    s = s.replace(' (eng subs)', '') 
    s = s.replace(' (English subs)', '') 
    s = s.replace(' (english subs)', '') 
    s = s.replace(' (Eng Subs)', '') 
    s = s.replace(' (English Subs)', '') 
    s = s.replace('&#x26;', '&') 
    s = s.replace('&#x27;', '\'') 
    s = s.replace('&#xC6;', 'AE') 
    s = s.replace('&#xC7;', 'C') 
    s = s.replace('&#xF4;', 'o') 
    s = s.replace('&#xE9;', 'e') 
    s = s.replace('&#xEB;', 'e') 
    s = s.replace('&#xED;', 'i') 
    s = s.replace('&#xEE;', 'i') 
    s = s.replace('&#xA2;', 'c') 
    s = s.replace('&#xE2;', 'a') 
    s = s.replace('&#xEF;', 'i') 
    s = s.replace('&#xE1;', 'a') 
    s = s.replace('&#xE8;', 'e') 
    s = s.replace('%2E', '.') 
    if use_encoding: 
        s = s.replace('"', '%22') 
        s = s.replace('*', '%2A') 
        s = s.replace('/', '%2F') 
        s = s.replace(':', '%3A') 
        s = s.replace('<', '%3C') 
        s = s.replace('>', '%3E') 
        s = s.replace('?', '%3F') 
        s = s.replace('\\', '%5C') 
        s = s.replace('|', '%7C') 
        s = s.replace('&frac12;', '%BD') 
        s = s.replace('&#xBD;', '%BD') #half character 
        s = s.replace('&#xB3;', '%B3') 
        s = s.replace('&#xB0;', '%B0') #degree character         
    if use_blanks: 
        s = s.replace('"', ' ') 
        s = s.replace('*', ' ') 
        s = s.replace('/', ' ') 
        s = s.replace(':', ' ') 
        s = s.replace('<', ' ') 
        s = s.replace('>', ' ') 
        s = s.replace('?', ' ') 
        s = s.replace('\\', ' ') 
        s = s.replace('|', ' ') 
        s = s.replace('&frac12;', ' ') 
        s = s.replace('&#xBD;', ' ') #half character 
        s = s.replace('&#xB3;', ' ') 
        s = s.replace('&#xB0;', ' ') #degree character 
    s = s.strip() 
    return s
```


To instead of replacing the dirty names, only allowing it to use these characters

```
 ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789!#$%&'()-.@[]^_`{}~**(SPACE)**
```

And replace anything that isn't one of those characters with a space, and also limit the number of characters to 35. Anyone wanna point me in the right direction? :D

---

### Post by ofnuts on 2011-10-04
> **fuzzman54 said:**
> [/CODE]
To instead of replacing the dirty names, only allowing it to use these characters

```
 ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789!#$%&'()-.@[]^_`{}~**(SPACE)**
```And replace anything that isn't one of those characters with a space, and also limit the number of characters to 35. Anyone wanna point me in the right direction? :D
You can use excluding regexps in re.sub:
```

>>> import re
>>> print re.sub('[^a-z]','!','ab3cd6ef')
[I][B]ab!cd!ef
[/B][/I]
```

---

### Post by StephenF on 2011-10-06
```

from urllib import quote

while 1:
    print quote(raw_input(), safe=" ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789!#$%&'()-.@[]^_`{}~")

```
See also: urllib.unquote

---


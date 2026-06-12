---
title: "Python Removing characters, terminal output"
date: 2008-05-31
forum: Programming Talk
---

### Post by mevets on 2008-05-31
I'm having my python script run
```
compiz-check > output.txt
```
This way it writes all its output to a file instead of the screen. My problem is that compiz-check use colors and bold font in its output. This is expressed weird characters when its written to a file. For example,
```


Gathering information about your system...

 Distribution:          [1mUbuntu 8.04[0m
 Desktop environment:   [1mGNOME[0m
 Graphics chip:         [1mIntel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)[0m
 Driver in use:         [1mintel[0m
 Rendering method:      [1mAIGLX[0m

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ [1;32mOK[0m ]
 Checking for non power of two support...          [ [1;32mOK[0m ]
 Checking for composite extension...               [ [1;32mOK[0m ]
 Checking for FBConfig...                          [ [1;32mOK[0m ]
 Checking for hardware/setup problems...           [ [1;32mOK[0m ]

```
Is there a way to easily remove these characters?

---

### Post by ghostdog74 on 2008-05-31
remove the color options from the compiz script itself. Try changing these variables to NOT output color.
```

# Coloured output (there are other emphases hardcoded in the script, so
# it would  be pretty useless changing those here)
UNKNOWN="\033[1;31mUnknown\033[0m"
OK=" \033[1;32mOK\033[0m "
FAIL="\033[1;31mFAIL\033[0m"
SKIPPING="\033[33mSKIP\033[0m"
WARN="\033[33mWARN\033[0m"


```

---

### Post by mevets on 2008-05-31
Oh, thanks. I credit the author for organizing it this way.

---

### Post by Forlong on 2008-05-31
Every emphasis in bash is started by `\033[` followed by one or two numbers separated by a semicolon and finally a `m`

Thus, you should be able to remove any of those, using this sed command:
```
sed 's/\\033\[[0-9;m]*//g'
```


P.S. may I ask what you are trying to do with my script? :)

---

### Post by mevets on 2008-05-31
Thanks, I building a gui around it in order to start learning about how to use glade to make guis

---

### Post by geirha on 2008-05-31
If you are using python, you might as well remove the ansi-codes in python. Using a slight modification of Forlong's regexp:

[php]
import os, re

r= re.compile("\033\[[0-9;]+m")
p= os.popen("compiz-check")
data= p.read()
p.close()
data= r.sub("", data)   # replaces all matches of the regexp in data with an empty string
[/php]

or if you prefer a more compact version
[php]
import os, re
data= re.sub("\033\[[0-9;]+m", "", os.popen("compiz-check").read())
[/php]

---

### Post by mevets on 2008-05-31
Thanks geirha. I'd been trying to translate that regex post by forlong into python and it was taking me quiet a long time. Ive never used them in python.

---


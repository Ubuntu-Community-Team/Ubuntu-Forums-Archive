---
title: "Help: doubleclick executable script gives warning."
date: 2007-07-17
forum: Programming Talk
---

### Post by Golyadkin on 2007-07-17
I am programming some application in Python, and made a BASH script to execute it: 

chmod +x PyBookcase
```

#!/usr/bin/bash 

python PyBookcase-gui.py

```

Running it from the console works perfectly. But when I browse to the directory with Nautilus where the files are, and double click it, Nautilus warns me and asks if I want to open or display the file. How do I get rid of this?  I want my end users to be able to just double click the script to start the program...

---

### Post by po0f on 2007-07-17
Golyadkin,

Open up gconf-editor and navigate to apps->nautilus->preferences.  Change 'executable_text_activation' from 'ask' to 'launch' and you should be good to go.

Or, open up a nautilus window and navigate to edit->preferences.  Click the behavior tab and check "Run executable text files when they are clicked".

---

### Post by Golyadkin on 2007-07-17
Thanks for the reply po0f, but is there no way to change this for the file and not for all files? Because I can't make this change on someone else's computer :)

---

### Post by syxbit on 2007-07-18
no, it has to do with how nautilus treats it.
it's still a script

---


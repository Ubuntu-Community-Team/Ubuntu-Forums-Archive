---
title: "Python help:Windows commands with python"
date: 2010-08-13
forum: Programming Talk
---

### Post by blithen on 2010-08-13
This is the script I'm trying to use
```
import os
selection = raw_input("Press one to enable two disable the screen saver")
elif selection == 1:
    os.system(nircmd.exe regsetval sz "HKCU\control panel\desktop" "ScreenSaveActive" 1)
if selection == 2:
    os.system(nircmd.exe regsetval sz "HKCU\control panel\desktop" "ScreenSaveActive" 0)


```
It's says there's an invalid syntax with "regsetval" how do i make sure it's seeing the whole thing as one command rather then separate ones?

---

### Post by Bachstelze on 2010-08-13
[http://docs.python.org/library/os.html#os.system](http://docs.python.org/library/os.html#os.system)

os.system takes a single string as argument, so:

```
import os
selection = raw_input("Press one to enable two disable the screen saver")
elif selection == 1:
    os.system('nircmd.exe regsetval sz "HKCU\control panel\desktop" "ScreenSaveActive" 1')
if selection == 2:
    os.system('nircmd.exe regsetval sz "HKCU\control panel\desktop" "ScreenSaveActive" 0')
```

You might also need to escape the blackslashes.

---

### Post by blithen on 2010-08-13
Thanks man.

---

### Post by blithen on 2010-08-13
Now it's saying that it's an invalid syntax at the first colon. Also here's the updated code, I switched from os.system, to subprocess.Popen.
```
import subprocess
selection = int(raw_input("Press one to enable and two disable the screen saver: ")
if selection == 1:
    subprocess.Popen('nircmd.exe regsetval sz "HKCU\control panel\desktop" "ScreenSaveActive" 1')
elif selection == 2:
    subprocess.Popen('nircmd.exe regsetval sz "HKCU\control panel\desktop" "ScreenSaveActive" 0')


```

---

### Post by Bachstelze on 2010-08-13
```
selection = int(raw_input("Press one to enable and two disable the screen saver: ")
```

Two opening parentheses, one closing. An editor with decent syntax highlighting would have helped you catch this.

subprocess.Popen doesn't work the same way, it takes a list of strings (the command and its arguments). If you want to use it, it's:

```
subprocess.Popen(['nircmd.exe', 'regsetval', 'sz', 'HKCU\\control panel\\desktop', 'ScreenSaveActive', '1'])

```

Or something along those lines, maybe it's a bit different on Windows.

---

### Post by blithen on 2010-08-13
Oh wow, thanks for the info, and yeah I'm downloading a text editor now that I look like a noob. >_>

---


---
title: "Scripts"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by subaruwrc01 on 2008-10-19
I want to create a script that will open the terminal and run the following code.

```
padsp wine .wine/drive_c/Pro*/Inf*/R*/rct2.exe
```

How do I go about creating this script?  I have no experience with scripts.  So, what would be the code?  What would I save the file as and where would I save it?

Running Hardy.

---

### Post by subaruwrc01 on 2008-10-19
Bump

---

### Post by Pro-reason on 2008-10-19
Sounds like you need a launcher.

Paste this into a file

```

[Desktop Entry]                                         
Exec=padsp wine .wine/drive_c/Pro*/Inf*/R*/rct2.exe                                            
Icon=terminal                                           
StartupNotify=true
Terminal=true
TerminalOptions=\s--noclose
Type=Application

```

Save it as ~/Desktop/RCT2.desktop.

---

### Post by subaruwrc01 on 2008-10-19
It doesn't work because I need the terminal to stay open.

---

### Post by cardinals_fan on 2008-10-19
Paste this into a blank text file:```
#!/bin/sh
padsp wine /home/[COLOR="Red"]yourusername[/COLOR]/.wine/drive_c/Pro*/Inf*/R*/rct2.exe
```Save the text file as ".winelaunch" in your home directory.  To execute it, enter this:```
chmod +x .winelaunch
./.winelaunch
```
Edit everything red to match your setup.

---

### Post by subaruwrc01 on 2008-10-19
Thank you!  Works great!

---

### Post by cardinals_fan on 2008-10-19
> **subaruwrc01 said:**
> Thank you!  Works great!
No problem :)

---

### Post by kerry_s on 2008-10-19
never mind

---


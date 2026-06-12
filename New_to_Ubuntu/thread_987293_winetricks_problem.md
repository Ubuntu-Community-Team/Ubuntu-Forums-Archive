---
title: "winetricks problem"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by mormor on 2008-11-19
winetricks seems to pull tricks on me.

When trying to install DirectX9, and two other packages from winetricks I get this feedback from terminal:

> marius@tobor:~$ sh winetricks
Warning: could not find DOS drive for current working directory '/home/marius', starting in the Windows directory.
Warning: could not find DOS drive for current working directory '/home/marius', starting in the Windows directory.
Executing wine /home/marius/.winetrickscache/vcrun2005sp1/vcredist_x86.exe
Warning: could not find DOS drive for current working directory '/home/marius', starting in the Windows directory.
wine: cannot find '/home/marius/.winetrickscache/vcrun2005sp1/vcredist_x86.exe'
Note: command 'wine /home/marius/.winetrickscache/vcrun2005sp1/vcredist_x86.exe' returned status 2.  Aborting.


Any idea how to fix this?

---

### Post by almigi on 2008-11-29
What version of Wine are you using?  Your best bet with Winetricks is to always use the newest version of Wine...

If you are using the newest version of Wine (1.1.9) and this is happening, let me know and we'll dig a bit deeper...

---

### Post by binbash on 2008-11-29
do you have .wine directory ?

---

### Post by Earl_Maroon on 2009-04-04
I had the same problem as you.

I think you need Wine configured to recognise your ~/.winetrickscache as in a drive, so either configure ~ as a drive (could make you vulnerable to Windows viruses) or set ~/.winetrickscache as a drive.

It worked for me at least.

---

### Post by Cypher1101 on 2010-01-21
> **Earl_Maroon said:**
> I had the same problem as you.

I think you need Wine configured to recognise your ~/.winetrickscache as in a drive, so either configure ~ as a drive (could make you vulnerable to Windows viruses) or set ~/.winetrickscache as a drive.

It worked for me at least.
TYVM! Finally, winetricks works!

---

### Post by jaredlundqu on 2010-04-18
What worked for me was setting "/" as a drive (without quotes). Also, you can probably use your home directory (/home/user) where user is your username.

[_Problems with Wine directories_]("http://ubuntuforums.org/showthread.php?t=1337166")

---

### Post by d3v1150m471c on 2010-04-18
It could be your version of wine. There is an alternative to direct x 9 that I believe winetricks informs the user of you should try.

---


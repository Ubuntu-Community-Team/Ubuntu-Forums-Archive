---
title: "unrar have tried everything"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by misswham on 2008-10-28
i have just reinstalled ubuntu and with the prior installation rar worked fine but now i that i have reinstalled ubuntu, rar keeps giving me an error message

Read error in the file /home/aretha/Documents/Chris.Rock.Kill.The.Messenger.INTERNAL.HDTV.XviD-aAF/aaf-chris.rock.kill.the.messenger.hdtv.r01_FILES [R]etry, [A]bort
Read error in the file /home/aretha/Documents/Chris.Rock.Kill.The.Messenger.INTERNAL.HDTV.XviD-aAF/aaf-chris.rock.kill.the.messenger.hdtv.r01_FILES
Inappropriate ioctl for device

i have gone through other posts and tried all of the other things like run in terminal 

sudo apt-get install rar

sudo apt-get update
sudo apt-get install unrar

I have run those commands and rebooted and still the same error.  Can anyone help?

---

### Post by LowSky on 2008-10-28
so what your saying is RAR wont install?

dont forget to enable the other repos

go to software source under System>>Admin

---

### Post by misswham on 2008-10-28
This is the message I get when I try to reinstall the command

desktop:~$ sudo apt-get install unrar
[sudo] password for doris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
unrar is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by drakeman007 on 2008-10-28
> **misswham said:**
> This is the message I get when I try to reinstall the command

desktop:~$ sudo apt-get install unrar
[sudo] password for doris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
unrar is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


What command are u using to unrar the file?```
 unrar -e <filename>
```

---

### Post by Paqman on 2008-10-28
Have you tried it on another archive? Could be a dodgy download.

---

### Post by drakeman007 on 2008-10-28
> **misswham said:**
> i have just reinstalled ubuntu and with the prior installation rar worked fine but now i that i have reinstalled ubuntu, rar keeps giving me an error message

Read error in the file /home/aretha/Documents/Chris.Rock.Kill.The.Messenger.INTERNAL.HDTV.XviD-aAF/aaf-chris.rock.kill.the.messenger.hdtv.r01_FILES [R]etry, [A]bort
Read error in the file /home/aretha/Documents/Chris.Rock.Kill.The.Messenger.INTERNAL.HDTV.XviD-aAF/aaf-chris.rock.kill.the.messenger.hdtv.r01_FILES
Inappropriate ioctl for device

i have gone through other posts and tried all of the other things like run in terminal 

sudo apt-get install rar

sudo apt-get update
sudo apt-get install unrar

I have run those commands and rebooted and still the same error.  Can anyone help?

Try with this solution, 
```
http://ubuntuforums.org/showthread.php?t=620670
```

---


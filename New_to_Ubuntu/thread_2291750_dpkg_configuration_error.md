---
title: "dpkg configuration error"
date: 2015-08-22
forum: New to Ubuntu
---

### Post by bohicaman on 2015-08-22
I upgraded my dual boot from Windows7 to 10 and kept Ubuntu the same at 14.04. However, it did not change the Grub menu. After reading a bit, I tried to download the grub-customizer so I could make the needed changes. After Ubuntu showed a valid download, I could not get the program to open when I clicked the icon. I also tried from a terminal - nothing. So I tried to remove the program. After I entered my password to do so, I got an error message that stated:

"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem."

I am almost a fresh start beginner with Ubuntu. I have no idea what that error message means, or how to correct the problem. I am very well versed in Windows and have worked on that system for years, built my own computer, and do some programming. If some one can explain, point me to an answer, or provide the code to fix this, I'd really appreciate it!!

System: ASUS x99-A, i7 5820, 64Bit, 16GB RAM, Windows 10/Ubuntu 14.04
Thanks!

---

### Post by Frogs Hair on 2015-08-22
The error indicates the package was not configured properly. First , make sure that the application is will work on your Ubuntu version and it should if running 14.04. The command presented in the error message will attempt to reconfigure the package. ```
sudo dpkg --configure -a
``` When you have some time you can read the man page in the terminal  which explains package commands.```
 man dpkg

``` The manual pages are also available on the web.   [http://manpages.ubuntu.com/manpages/lucid/man1/dpkg.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/dpkg.1.html)

---

### Post by bohicaman on 2015-08-22
I tried the configuration command earlier and it didn't work. Tried it again now and it apparently worked. I'm also in process of readying man dpkg. Thanks!

---


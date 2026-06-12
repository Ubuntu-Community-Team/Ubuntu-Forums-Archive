---
title: "Black screen after reboot"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by ioueoirueou56465674 on 2008-11-16
Hello, just installed 8.10 on dual-boot.
It ran fine for a few days... 
After a normal shutdown and a few days, just can´t start it anymore. 
After the Ubuntu logo and load bar, got a black screen.
I can get to safe mode, but don´t know what to look for.
Thanks if anyone has any clues...
Regrds

---

### Post by Scene on 2008-11-16
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

Try that.
It tells you how to back up your system and how to restore your system.

Maybe restore your system to a date where it was working?

---

### Post by mapes12 on 2008-11-16
The backup suggestion wouldn't work because your system is already broken. So you have no backup tar to restore. The backup tar should have been created BEFORE attempting an upgrade.

If you can get to a Terminal try:
```

sudo apt-get install ubunut-desktop
```

---

### Post by prshah on 2008-11-16
> **ioueoirueou56465674 said:**
> 
I can get to safe mode, but don´t know what to look for.
anyone has any clues...

When the logo is loading (or at the black screen), press Ctrl+Alt+F8; this will show you the actual boot progress. Post back the last few lines shown in that.

Also, if you can manage it, the last few lines of the system log, and /var/log/Xorg.0.log, /var/log/Xorg.1.log ```

dmesg | tail > ~/dmesglog.log
tar -cf test.tar /var/log/Xorg.[0,1].log ~/dmesglog.log

``` The above commands will create a file called "test.tar" with the required log information; can you manage to post that file here?

---

### Post by ioueoirueou56465674 on 2008-11-16
Thank you guys very much.
Just dont know what happened... When I tried to reboot to collect the info requested, the system booted up normally (?), after the 3 unsuccessful attempts that led me to this forum. Working normally so far. 
I'll try to see if anything unusual comes up and let you know.
Ubuntu upgraded itself, maybe it will help.
Thanks again for all the help!
Cheers!

---

### Post by ioueoirueou56465674 on 2008-11-18
Same problem again... 
This time I could manage to get a shell and collect the files you requested.
Thanks for any help!
Regards.

---


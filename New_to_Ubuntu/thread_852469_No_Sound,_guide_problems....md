---
title: "No Sound, guide problems..."
date: 2008-07-07
forum: New to Ubuntu
---

### Post by Aezik on 2008-07-07
I'm a right newbie to Linux in general and have been introduced to Ubuntu today by almost pure accident but I now have to work with it as I can't get back on to windows.

So far I've managed to successfully install wine, flash and get other basics sorted but with the upgrades earlier today I have now lost sound; and I have found this 

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade)

However, I've found it difficult to follow the first set of instructions and I seem to receive the following error after typing in the first line:

"****@dell-desktop:~$ sudo dpkg -r hsfmodem
dpkg - warning: ignoring request to remove hsfmodem, only the config
 files of which are on the system.  Use --purge to remove them too."

Any assistance would be appreciated.

Many thanks,

Aezik

---

### Post by webofunni on 2008-07-08
Hello Aezik,

  You are getting that error because the hsfmodem modem driver does not exist in your system. You can ignore that. 

  What is the result of following commands : 

```
sudo aplay -l
speaker-test
```

---


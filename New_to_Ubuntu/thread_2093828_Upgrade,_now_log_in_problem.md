---
title: "Upgrade, now log in problem"
date: 2012-12-11
forum: New to Ubuntu
---

### Post by ke7fck on 2012-12-11
Hello,

When I bought my new computer a couple of years ago I decided to put Ubuntu on it. It's an MSI mobo w/ AMD Athalon II X4 640. I installed 10.04 (32) and OpenOffice and was happy.

Then I created a new USB bootable with 12.04 (64) and installed that. I chose the "upgrade" option, rather than the fresh install option. It asked me who I was and for a password, so I gave a new one.

Upon installation completion I rebooted and all went well, the login window appeared.  It asked for my new password and I gave it. An error window appears showing that I do not have permissions to write to the password file (not exactly what it says, but you get the drift I hope).

None of my previous passwords work either (root, guest and family usernames all had unique passwords).

I logged on now as an unprotected guest and have no permissions to do anything.

help.

---

### Post by Mr. Hibba on 2012-12-12
EDIT: Before attempting anything, it's important that you have a working backup, too!  If possible, ensure that you backup any important files (preferably to an external drive) before continuing.

I'm not sure if I've ever tried Ubuntu's USB installer option... I'm more familiar with the LiveCDs.  If they are similar, though, does it give you the option to "Try Ubuntu" when you boot from USB?  If it does, select it, then open a terminal...

EDIT AGAIN:  Sorry, forgot to mention that some of the following terminal commands should be run with administrator rights.... I have changed the commands below to run as administrator.  

Type in something like ```
sudo mkdir /mnt/Ubuntu
``` and then mount the partition holding your / directory there: ```
sudo mount /dev/sda1 /mnt/Ubuntu
``` NOTE:  Your partition may be named differently, depending on  how your computer is set up.  

Now, type ```
sudo chroot /mnt/Ubuntu
``` which should let you back into your Ubuntu install.  Once in there, type ```
passwd username
```, where username is the account that you want to set the password for.  If you are unsure of what the exact username would be, something like ```
ls /home/
``` should list your username(s).  

And now, just type ```
exit
``` to cleanly exit the chroot, and then ```
sudo umount /mnt/Ubuntu
```.  Finally, reboot the computer and boot from your hard disk.  

Hope this helps :D

---

### Post by squakie on 2012-12-13
Most of us would most heartedly tell you to back things up, then INSTALL 12.04, not upgrade.  I don't think you can directly upgrade from 10.x to 12.x, but I might be wrong there.  In the past there have been innumerable problems with doing an update to get to a new release, instead of backing everything up and just installing the new version.

That would be my suggestion.  ;)

---

### Post by DuckHook on 2012-12-13
> **ke7fck said:**
> ...It asked me who I was and for a password, so I gave a new one...I do not have permissions to write to the password file

You are probably now stuck in limbo because, by using a new name and password for the upgrade, you basically upgraded as an unauthorized user unknown to the old system. And yet, it is the old system that was charged with guarding against bad guys hijacking your data. Otherwise, it would be possible for anyone to gain access to your private files by the simple expedient of upgrading. Therefore, when upgrading, it is imperative to maintain continuity and use the name and password that you used for your original install.

> None of my previous passwords work either (root, guest and family usernames all had unique passwords). I logged on now as an unprotected guest and have no permissions to do anything.Just entering your old password won't work. You first have to tell the system that you want to login as the old user. Then the password will work for that user.

Please provide more info.

1. Do you get to a desktop or are you stuck at the terminal console?

2. If the desktop comes up, can you choose your old name at the login screen, or does it only offer the one choice of your new non-functioning name?

3. You say that you had a unique password for root. This implies that you activated your root account which, in Ubuntu, comes de-activated by default. Is this so? And if so, could you please briefly describe how you did this (want to make sure that it is indeed activated). An activated root account might actually make things easier in this case, but it is not generally recommended practice.

4. Do:

```
ls -n /home
```and post results back here.

---


---
title: "Reinstall 11.10? and not loose anything?"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by wapfu on 2011-10-16
looks like failed installation.
Cannot login - only as guest.
Cannot use the Xauthority fix.
Do not want to loose any files.
maybe if there is a bug fix I can down load in the guest desktop as administrator, sometime in the future, but cannot login under my profile, and this distribution will not shut down unless I soft boot.

I have no recovery facility either in grub as it gives me a blank screen.
Who screwed up this one?

Is there anyone out there?

---

### Post by Lisiano on 2011-10-16
There are 2 routes you can go, restore Ubuntu or reinstall, please tell me which you prefer and I will provide the adequate instructions.

EDIT: Why do you think its a failed install? Did you upgrade from 11.04 or clean-install? If the later, did the installer say it was finished or did something happen like a blackout?

---

### Post by wapfu on 2011-10-16
Hi,
Upgraded from 11.04 to 11.10.
No power outage just let the install run its complete cycle.
I figure failed, as there is no recovery option - it sits in grub and only gives me a blank black screen, and also I cannot login  in any way - only as guest.
A reinstall is really preferable as a new install will take out any files existing for another user.
Thank you.
Kind Regards

---

### Post by Lisiano on 2011-10-16
So you prefer a reinstall then.
1 ) Download and burn a LiveCD/USB from [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
2 ) Boot with the CD/USB and select Install Ubuntu
3 ) When asked how you want to install, select "Something Else" or "Manual partitioning"
4 ) If you have only Ubuntu installed, you will probably see 1 large and 1 fairly small partition if you didn't do anything, if not, please reboot and select "Try Ubuntu", open a file manager, take a look at the available disks, click on them in turn and find the one with /bin, /lib, /etc, etc. Take a look at the top where the current folder name is and try to remember the name. Unmount (Press the eject button) near every partition EXCEPT the one you found /bin, /lib, /etc, etc in. Now open a Terminal (Ctrl+Alt+T) and type ```
mount
```Now try to find the line that has the same name after /media/
For example
```
/dev/sda7 on /media/<Big-string-of-numbers-and-letters> type ext4
```
Remember the name (/dev/sda7 in this case) and go back to the Installer by starting it from the Launcher. Now in Manual partitioning select partition you have ubuntu on and press Edit (If you had only 1 large and 1 small partition I noted above, pick the larger one), now select the partition filesystem (From the same place we found about the name), in this case EXT4 (Which is also the default), leave format ***_[COLOR="Red"][SIZE="4"]UNTICKED[/SIZE][/COLOR]_*** and in the white box bellow, select "/" (Without the quotes).
5 ) Continue the install as you would normally.
*Optional* 6) Get a cup of tea/coffee while installing, you earned it.
7 ) Wait until the installer prompts you to reboot, agree to the reboot
8 ) Let Ubuntu boot up and login
9 ) Use Ubuntu.

---

### Post by wapfu on 2011-10-16
Cheers Lisiano.
Will do.

Many thanks

---

### Post by Lisiano on 2011-10-16
I forgot to mention. Just incase of anything, please backup the data you think is most important to you (It is located under /home/username). While the process is straightforward and more or less safe (IF you **_don't_** tick the format checkbox), you are still advised to backup your data.

---


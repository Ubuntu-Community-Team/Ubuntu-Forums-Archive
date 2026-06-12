---
title: "Can't Login"
date: 2012-10-20
forum: New to Ubuntu
---

### Post by SuperFreak on 2012-10-20
While I ahve been using Ubuntu for awhile this is a beginner question because I am quite lost
I was trying to do a back up of files onto an external drive which had problems mounting. After that  I am unable to log in to my account. I can log into the Guest account but not my own. When I boot the computer normally it will log in automatically and go straight to my desk top; now it goes to the log in screen and clicking on my acount (admin account) just brings me back to the log in screen. I can log in to the guest account

---

### Post by mardybear on 2012-10-20
Hi SuperFreak.

Are you able to login as 'root' (username), using your regular password? This might allow you to get onto your computer to troubleshoot but be careful running as root.

If this doesn't work, you could also boot into an Ubuntu liveCD to change your user configuration files as needed.

mardybear

---

### Post by rburkartjo on 2012-10-20
super i know what you need to fix. you somehow need to access your home folder and delete a hidden file called .Xauthority. i just had to do that and it fixed my problem. ask someone here how to access this from the virtual terminal and delete it. i know that there is a way just dont know how. how i fixed was to log into my daughter account than ran gksudo nautilus,navigated to my home folder and deleted. rebooted and all was well.

---

### Post by robtygart on 2012-10-20
To access the terminal press ctrl+alt+F2

.... 
How to delete a directory 

[http://www.tuxfiles.org/linuxhelp/dirman.html](http://www.tuxfiles.org/linuxhelp/dirman.html)

To delete a directory 
```
rm -r "dir"
```

---

### Post by SuperFreak on 2012-10-20
I tried ```
cd home
``` in terminal(CTL-ALT-F1)
 followed by
```
rm -r .Xauthority
```
get output saying file/directory does not exist

---

### Post by robtygart on 2012-10-20
post output of ```
ls -al
```

---

### Post by SuperFreak on 2012-10-20
This may not be of much use as it is the output while in the guest account. If not how do I copy the out put from the admin account after CTL-ALT-F1

```
guest-qpittH@david-desktop:~$ ls -al
total 52
drwx------ 23 guest-qpittH guest-qpittH  680 Oct 20 19:25 .
drwxrwxrwt 14 root         root          320 Oct 20 19:32 ..
-rw-r--r--  1 guest-qpittH guest-qpittH  220 Oct 20 19:23 .bash_logout
-rw-r--r--  1 guest-qpittH guest-qpittH 3486 Oct 20 19:23 .bashrc
drwx------ 10 guest-qpittH guest-qpittH  240 Oct 20 19:32 .cache
drwxr-xr-x 12 guest-qpittH guest-qpittH  280 Oct 20 19:23 .config
drwx------  3 guest-qpittH guest-qpittH   60 Oct 20 19:23 .dbus
drwxr-xr-x  2 guest-qpittH guest-qpittH   40 Oct 20 19:23 Desktop
-rw-r--r--  1 guest-qpittH guest-qpittH   26 Oct 20 19:23 .dmrc
drwxr-xr-x  2 guest-qpittH guest-qpittH   40 Oct 20 19:23 Documents
drwxr-xr-x  2 guest-qpittH guest-qpittH   40 Oct 20 19:23 Downloads
-rw-r--r--  1 guest-qpittH guest-qpittH 8445 Oct 20 19:23 examples.desktop
drwx------  4 guest-qpittH guest-qpittH   80 Oct 20 19:23 .gconf
drwx------  6 guest-qpittH guest-qpittH  120 Oct 20 19:25 .gnome2
drwx------  2 guest-qpittH guest-qpittH   40 Oct 20 19:25 .gnome2_private
drwx------  2 guest-qpittH guest-qpittH   40 Oct 20 19:23 .gvfs
-rw-------  1 guest-qpittH guest-qpittH  346 Oct 20 19:23 .ICEauthority
drwxr-xr-x  3 guest-qpittH guest-qpittH   60 Oct 20 19:23 .local
drwx------  3 guest-qpittH guest-qpittH   60 Oct 20 19:23 .mission-control
drwx------  4 guest-qpittH guest-qpittH   80 Oct 20 19:25 .mozilla
drwxr-xr-x  2 guest-qpittH guest-qpittH   40 Oct 20 19:23 Music
drwxr-xr-x  2 guest-qpittH guest-qpittH   40 Oct 20 19:23 Pictures
-rw-r--r--  1 guest-qpittH guest-qpittH  675 Oct 20 19:23 .profile
drwxrwxr-x  2 guest-qpittH guest-qpittH   60 Oct 20 19:23 .psensor
drwxr-xr-x  2 guest-qpittH guest-qpittH   40 Oct 20 19:23 Public
drwx------  2 guest-qpittH guest-qpittH  160 Oct 20 19:23 .pulse
-rw-------  1 guest-qpittH guest-qpittH  256 Oct 20 19:23 .pulse-cookie
drwxr-xr-x  2 guest-qpittH guest-qpittH   40 Oct 20 19:23 Templates
drwx------  3 guest-qpittH guest-qpittH   60 Oct 20 19:23 .thumbnails
drwxr-xr-x  2 guest-qpittH guest-qpittH   40 Oct 20 19:23 Videos
-rw-------  1 guest-qpittH guest-qpittH   58 Oct 20 19:23 .Xauthority
-rw-r--r--  1 guest-qpittH guest-qpittH 1601 Oct 20 19:23 .Xdefaults
-rw-r--r--  1 guest-qpittH guest-qpittH   14 Oct 20 19:23 .xscreensaver
-rw-------  1 guest-qpittH guest-qpittH 3993 Oct 20 19:31 .xsession-errors

```


I believe my FSTAB may be the reason for the problems and I hhave a back up copy. Should I try replacing FSTAB with the back up. I would think I have to be in the Live CD to make it work?

---

### Post by SuperFreak on 2012-10-20
Thanks evryone for your help.
I replaced Fstab with my Back up and I am in business again

---

### Post by robtygart on 2012-10-21
Cool! I am glad you got it fixed.

---


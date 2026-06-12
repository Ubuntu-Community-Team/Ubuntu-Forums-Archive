---
title: "Files in Temp folder"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by richg on 2008-10-06
Anyone know what the files in the Temp folder might be used for? There is nothing on my descktop. I am on a cable modem. Browser is not open. Thanks.

Rich

---

### Post by matt1988 on 2008-10-06
All of those files inside of /tmp are just created by programs, for example the gconf-lexon directory was created by gconf.. I believe lexon is your user name. Shouldn't be anything to worry about.

Hope that helps :)

---

### Post by drubin on 2008-10-06
I was also worried a few days ago about the files in my /tmp folder. Yours all seem to be fine.

---

### Post by richg on 2008-10-06
Thanks all. I was just curious. When I use to run 98SE a few years ago, I use to have to clear the temp folders quite often and usually recognized suspicious files. I use to help friends clear their temp files, the files where so full. Now they pay someone to “clean up” the computers. Not so with Linux. I get a little uneasy when I see people talking about the security of Linux. I have been around long enough to know to never say never.

Rich

---

### Post by jerome1232 on 2008-10-06
/tmp is emptied every time you boot the system

---

### Post by OutOfReach on 2008-10-06
Generally, you don't have to worry about /tmp files since there are not many (very few, actually) and they get cleaned up at boot time.

---

### Post by richg on 2008-10-06
There are still files there everytime I boot and check. I remember NO files when I booted my old 98 PC if I cleaned them out before shutting down.

Rich

---

### Post by jerome1232 on 2008-10-06
That's because the programs put them there during the boot process. It is cleaned every boot. (I'm adding a random file there right now and rebooting just to see for sure since I've only heard it over and over never tested it)

---

### Post by jerome1232 on 2008-10-06
And yes they do get cleaned out here it is: notice files are missing and the numbers have changed and some files were deleted after the reboot
```
jeremy@direbane:~$ cd /tmp
jeremy@direbane:/tmp$ ls
fileJAd27n      plugtmp          seahorse-zPxGQH        virtual-jeremy.v2mFBi
filetxIEv9      pulse-jeremy     Tracker-jeremy.8714
keyring-BCRzF9  seahorse-J3TKIl  virtual-jeremy.9PdMB4
orbit-jeremy    seahorse-rpPHyt  virtual-jeremy.hdGEVI
jeremy@direbane:/tmp$ sudo touch randomfile
[sudo] password for jeremy: 
jeremy@direbane:/tmp$ ls
fileJAd27n               plugtmp          seahorse-zPxGQH
filetxIEv9               pulse-jeremy     Tracker-jeremy.8714
gedit.jeremy.1851906956  randomfile       virtual-jeremy.9PdMB4
keyring-BCRzF9           seahorse-J3TKIl  virtual-jeremy.hdGEVI
orbit-jeremy             seahorse-rpPHyt  virtual-jeremy.v2mFBi
jeremy@direbane:/tmp$ 

---after reboot----
jeremy@direbane:~$ cd /tmp
jeremy@direbane:/tmp$ ls
filepr58Do  keyring-Kn6Cfg  pulse-jeremy     Tracker-jeremy.6244
fileTT3XbT  orbit-jeremy    seahorse-688bMf  virtual-jeremy.uxCzyQ
```

---


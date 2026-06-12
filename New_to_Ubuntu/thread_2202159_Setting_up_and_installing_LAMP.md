---
title: "Setting up and installing LAMP"
date: 2014-01-27
forum: New to Ubuntu
---

### Post by Paul_Jeffreys on 2014-01-27
Hi, 

Sorry if this is in the wrong place but am a novice in terms of installing and using things...

I was following the Lynda.com tutorial on setting up and installing LAMP ("Up and Running with Linux for PHP Developers") and everything ran fine and then I tried to run a command: "***sudo mount /dev/cdrom /media/cdrom***" but I keep getting the following message: "***mount: no medium found on /dev/sr0***".

I don`t know what I have done wrong and I can`t continue on the course until I have worked out how to do things as the next command won`t work...

Do I need to reboot everything? Or something rediculously simple I have missed?

Pj.

---

### Post by mörgæs on 2014-01-27
Hi, welcome to the fora.

For installing LAMP you just have to run

```
sudo apt-get install lamp-server^
```

and yes, reboot after that.

---

### Post by Rick1971 on 2014-01-27
what is LAMP, is that on a cd rom?

---

### Post by Dave_L on 2014-01-27
> **Rick1971 said:**
> what is LAMP, is that on a cd rom?

[https://en.wikipedia.org/wiki/LAMP_%28software_bundle%29](https://en.wikipedia.org/wiki/LAMP_%28software_bundle%29)

It's installed from the repositories, using the command mörgæs posted above.

---

### Post by Paul_Jeffreys on 2014-01-27
Yeah, everything should be installed but even after a reboot of whole laptop, I am still getting the "mount: no medium found on /dev/sr0" message when I try and run "sudo mount /dev/cdrom /media/cdrom" part :(

---

### Post by tgalati4 on 2014-01-27
Depending on what version of linux you are running, the cdrom is mapped to device sr0:


tgalati4@tpad-Gloria7 /dev $ ls -la
total 4
drwxr-xr-x  16 root   root        4120 2014-01-27 16:05 .
drwxr-xr-x  21 root   root        4096 2013-08-30 14:24 ..
crw-rw----+  1 root   audio    14,  12 2014-01-25 13:03 adsp
crw-rw----+  1 root   audio    14,   4 2014-01-25 13:03 audio
drwxr-xr-x   2 root   root         640 2014-01-25 05:03 block
drwxr-xr-x   3 root   root          60 2014-01-25 05:03 bus
**lrwxrwxrwx   1 root   root           3 2014-01-25 05:03 cdrom -> sr0**
lrwxrwxrwx   1 root   root           3 2014-01-25 05:03 cdrw -> sr0
drwxr-xr-x   2 root   root        3560 2014-01-27 16:05 char
crw-------   1 root   root      5,   1 2014-01-26 13:25 console
lrwxrwxrwx   1 root   root          11 2014-01-25 05:03 core -> /proc/kcore
crw-rw----   1 root   root     10,  60 2014-01-25 05:03 cpu_dma_latency
drwxr-xr-x   6 root   root         120 2014-01-25 05:03 disk
drwxr-xr-x   2 root   root          60 2014-01-25 13:03 dri
crw-rw----+  1 root   audio    14,   3 2014-01-25 13:03 dsp
lrwxrwxrwx   1 root   root           3 2014-01-25 05:03 dvd -> sr0

Also, you can't mount the cdrom unless there is a proper, mountable cd in the tray.  Does your cdrom work?

---

### Post by Paul_Jeffreys on 2014-01-28
Ah, that may be the issue... The tray certainly works but I don`t have a cd in the tray. Is it that simple?

Also, I tried the mount statement with sr0 too and also didn`t work so very likely the above is the issue -:os

---

### Post by mastablasta on 2014-01-28
> **Paul_Jeffreys said:**
>  The tray certainly works but I don`t have a cd in the tray. Is it that simple?


yup. *** no medium *** = no CD/DVD [in tray]

---

### Post by Paul_Jeffreys on 2014-01-28
Hmmmm, and if I have a formatted disc in the try and the try works fine, and I STILL get this message, have I missed something? 

Also, do I have to mount to the disc? I have a folder on the desktop which was created during the setup (manually created by me I mean, not by process). Can I mount things to that insteasd of the cdrom or is the cdrom mount a required step usually in setting things up?

Also, as I just remembered... During the setup of things, the course I was following said to attach the Ubuntu .iso file to the "CD/DVD Drive IDE secondary Master" link. DOes this change what I do with the mount?

Apologies for all this, but trying to learn and this 1 step just defeating me lol

---

### Post by mastablasta on 2014-01-28
what does the course actually do? what are you trying to do? what do you want to achieve? are you trying to install ubuntu linux in a virtual mashcine like for example virtual box?

as mentioned in ubutnu all you need to do to install lamp is run that one command in terminal on server. after that you need to confirgure PHP database (i use PHPmyadmin for that) and some permissions for certain file folders. and then you are done.: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

if you don't want to mess with setting up LAMP and just want to do some work on PHP have a look at Turnkey Linux. it's super easy to use, has virtual  images with various stuff preisntalled if you want to run virtual server for example. it's debian stable based. i use it to test some things that i later introduce to my websites. you just start it it will ask a few things to configure (passwords, database names and such) and then you can just run it.

---


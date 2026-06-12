---
title: "graphics drivers (Nvidia)"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by georgeadey1 on 2008-07-20
I am using a Nvidia Geforce 7600gt, i am just installing ubuntu and when this has completed how easy will it be to install the drivers for the graphics card (i still have the original driver cd) and for sound ( i don't have any sound drivers on cd) what do i do ?

thanks

---

### Post by Sockerdrickan on 2008-07-20
it will be really easy to install gpu drivers trust me, ubuntu will tell you what to do

---

### Post by davbren on 2008-07-20
a little notice should pop up in the top right of the screen. This will rell you that there are new restricted drivers in use. click that and click "enable" in that box. This will install the nvidia drivers. :)

---

### Post by georgeadey1 on 2008-07-20
thanks guys, but what about the sound card, will i have to download the drivers from the internet and copy them to the computer running ububtu or will ubuntu recognise the sound card

---

### Post by soxs on 2008-07-20
Unless you are dualbooting, throw your driver cds away, they are useless for linux. Everything goes through the "allmighty web".
Sound should work pretty well, unless you own a X-fi card, which will need some further work and limtates you to OSS (Don't thiink about that unless you own one).
GPU drivers is the most easiest part in ubunt, just install ubuntu, and you will be more or less get guided tour "through the driver installation"

---

### Post by Alldan on 2008-07-20
when installation process is finished enable just enable your driver in system/adm./hardware drivers. your driver will be automatically downloaded and installed.
 I think that your soundcard will work out-of-the-box and no aditional driver will be needed.

---

### Post by georgeadey1 on 2008-07-20
kk thanks for the responses, ubuntu is currently installing onto the partition that did have windows xp. Currently i do not have a usb internet adapter. How much will i need the internet in the first few days of running ubuntu

---

### Post by soxs on 2008-07-20
> **georgeadey1 said:**
> kk thanks for the responses, ubuntu is currently installing onto the partition that did have windows xp. Currently i do not have a usb internet adapter. How much will i need the internet in the first few days of running ubuntu

Depends on your hardware and iyou you come across any problems, though internet is always usefull for updateing packages which fix (rare) security vulnerabilities and exceed the functionality of certain programs.

At least for the restriced driver manager I would suggest you to connect to the internet.

---

### Post by larry19l on 2008-07-20
> **davbren said:**
> a little notice should pop up in the top right of the screen. This will rell you that there are new restricted drivers in use. click that and click "enable" in that box. This will install the nvidia drivers. :)

Ok, this did happen and all was ok. Then a few days later I installed envyNG cuz someone here said it helped with wine.
Unfortunately...
1...it didn't help with wine.
2...wine doesn't seem to work anyway (can't get anything installed)
3...EnvyNG trashed (overwrote) my xorg.conf file (trashed wacom)

So now, I've completely removed envyNG which, because of #3, I recommend EVERYONE to avoid. Like the plague!

Next is to get HH to reinstall those restricted drivers like you describe. Is there a way to either install manually or better yet, a means of inducing the behavior you describe and which did occur when I did the original install from the liveCD ?

---

### Post by asmoore82 on 2008-07-20
> **larry19l said:**
> 
So now, I've completely removed envyNG which, because of #3, I recommend EVERYONE to avoid. Like the plague!

Here! Here!

An all-in-one tool like that leaves its users broken and helpless;
especially when Ubuntu Software Updates come around and
have to deal with the mess the tool left behind.

---

### Post by soxs on 2008-07-20
> **larry19l said:**
> Ok, this did happen and all was ok. Then a few days later I installed envyNG cuz someone here said it helped with wine.
Unfortunately...
1...it didn't help with wine.
2...wine doesn't seem to work anyway (can't get anything installed)
3...EnvyNG trashed (overwrote) my xorg.conf file (trashed wacom)

So now, I've completely removed envyNG which, because of #3, I recommend EVERYONE to avoid. Like the plague!

Next is to get HH to reinstall those restricted drivers like you describe. Is there a way to either install manually or better yet, a means of inducing the behavior you describe and which did occur when I did the original install from the liveCD ?

Plx post your xorg.conf in code tags. I'll fix it tomorrow..

Note: You can check if your ati fglrx driver is working via ```
fglrxinfo
```, as long it doesn't spit out something with mesa but ati inc everything is ok. When everything works, DO NOT MESS AROUND WITH ANY 3RD PARTY TOOLS!

---


---
title: "Xubuntu 6.06 dapper alternate install and Kubuntu Gui"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by petebarchetta on 2008-08-19
hello all,

I am trying to install a xubuntu 6.06 alternate on a toshiba tecra 520cdt running 98mb 166mhz P1 MMX.
The CD boots and gets to partitioning phase which it completes, the install then fails at the XFSProgs,Debootstrap  and initramfs-tools points of the install. Any ideas how to get round this? the CD likes the hardware, but it appears maybe something wrong, i have tried multiple burns to fail the CD out of the equation, so its up to the Ubuntu collective to assist
I have recently installed a Kubuntu 6.06 text version and thats installs happily, is there any way to get a Kubuntu Gui installed ever it as i would like to stay in the Ubuntu area
any help greatly appreciated.

---

### Post by halitech on 2008-08-19
to be honest, I have the 550cdt version which is a 266 with 96meg of ram and and even if you can get kubuntu installed (from the text install just run sudo aptitude kubuntu-desktop should do it) it will not run very well on only 96 meg of ram. You may want to look at DSL or puppy for that machine as its more in the range of those then full blown kubuntu.

---

### Post by petebarchetta on 2008-08-19
i have two tecra's both 520's
the other runs a full compliment of ram 160mb, xp,40gb travelstar HD, 6.8 bios and a teac DVD rom drive (the dvd drive likes the CD_RW disc whreas the original CDROM drive is naff.
If i can get the install to work i will try the command. just out of curiosity where will it get the aptitude desktop from the CDROM or Network connection?

thanks

---

### Post by aysiu on 2008-08-19
Multiple burns from the same .iso file won't help if the .iso got corrupted during download. It's also possible it got corrupted during the burn process if you burnt it at too fast a speed. Did you do a checksum on the .iso?

---

### Post by halitech on 2008-08-19
> **petebarchetta said:**
> i have two tecra's both 520's
the other runs a full compliment of ram 160mb, xp,40gb travelstar HD, 6.8 bios and a teac DVD rom drive (the dvd drive likes the CD_RW disc whreas the original CDROM drive is naff.
If i can get the install to work i will try the command. just out of curiosity where will it get the aptitude desktop from the CDROM or Network connection?

thanks

if you use the alt cd to install, it will probably grab it from the internet

---

### Post by aysiu on 2008-08-19
You're using the Xubuntu installation to *aptitude* add Kubuntu? If that's the case, *aptitude* will definitely use the network connection, as *kubuntu-desktop* won't be available to install from the Xubuntu CD.

---

### Post by petebarchetta on 2008-08-20
sorry, maybe i'm leading you down the wrong route.... i have formatted the drive on both occaisions to start witha  clean build. i tried the Kubuntu dapper and it installs, but onlt in text mode. i then wanted the gui hence going down the Xubuntu path. the xubuntu build had no luck in running or even completing the install, whereas the Kubuntu dapper alternate build worked and i can use the laptop albeit in text function. my theory now is to get kubuntu dapper non alternate iso and see if tht works as that i think has the gui? please correct me if i am wrong.

Halitech, what flavour are you running on the 550?

---

### Post by halitech on 2008-08-20
it's laptop 2 in my specs. The latest release of DSL 4.4.3 is running happily on it and my girlfriends son is using it and very pleased with it.

---

### Post by petebarchetta on 2008-08-20
one last shot with gutsy alternate, then maybe retry kubuntu 6.06 and if that dont work then its off to DSL 4.4.4with the tecra....keep you posted
Dont get me wrong i like ubuntu command line its just like other CMD linux brew's i'm just more at home with a gui (see lazy):)

---

### Post by petebarchetta on 2008-08-21
right! burnt myself a copy of ubuntulite gutsy, it took an age to chug through, but the only thing it failed on was the bootloader (grub / LILO) neither of these two would install properly. Not sure how to progress this now as i'm unkeen to fart around with the MBR manually :confused:and both the lilo and grub setups are not playing ball. When the install finished and rebooted the system gave "Grub error 17"
What is error17? 
Apart from that it was reasonably plain sailing bit uneventful really....like watching paint dry LOL:). Any help would be great.
have DSL waiting in the wings if this fails.......

---

### Post by petebarchetta on 2008-09-03
> **petebarchetta said:**
> right! burnt myself a copy of ubuntulite gutsy, it took an age to chug through, but the only thing it failed on was the bootloader (grub / LILO) neither of these two would install properly. Not sure how to progress this now as i'm unkeen to fart around with the MBR manually :confused:and both the lilo and grub setups are not playing ball. When the install finished and rebooted the system gave "Grub error 17"
What is error17? 
Apart from that it was reasonably plain sailing bit uneventful really....like watching paint dry LOL:). Any help would be great.
have DSL waiting in the wings if this fails.......

i cant beleive hat grub is the culprit of this ubuntu installation......, but when i ran DSL 4.4.4 it installed without as much as a stumble. seamless from start to finish, i expected the same grub or lilo to halt the proceedings, but not a bean. Is there anyone out there who has successfully run ubuntu on a tecra 520 / 550? Or has a working grub / Lilo i can look at to sort the error17:confused:

---

### Post by dmizer on 2008-09-03
Check your bios settings to make sure your Hard drive is NOT set to "auto".

Are you installing to an external drive?

As an asside, Kubuntu's probably too heavy for that computer. I suggest Xubuntu instead.

---


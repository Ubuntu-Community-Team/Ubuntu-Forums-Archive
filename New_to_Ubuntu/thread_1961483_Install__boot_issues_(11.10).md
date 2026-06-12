---
title: "Install / boot issues (11.10)"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by mortuk on 2012-04-19
Hello all

So having some issues doing a fresh install off USB. Have tried multiple USB sticks before someone mentions it

First I tried 12.04 but both the installer and the live boot both half loaded the interface and then stopped, however mouse was movable etc.

Then tried 11.10 where I managed to get it installed first time, but I wasn't getting a grub menu on boot, and played around with grub and broke it some more so decided to start fresh.

Since then whenever I install, once its rebooted I just get a flashing cursor + black screen. I have tried booting off all drives in the system rom the bios but it strangely does the same thing.

Also have tried setting the boot loader device to both /dev/sda, as well as /dev/sda1, both with the same effect

Any ideas whats going wrong? Have read multiple threads on here and none seem to have solutions / be exactly the same problem as I have

---

### Post by audiomick on 2012-04-19
It sounds like maybe Grub didn't get installed right.

You could try re-installing it, perhaps.

[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2")

---

### Post by sudodus on 2012-04-19
> **mortuk said:**
> Hello all

So having some issues doing a fresh install off USB. Have tried multiple USB sticks before someone mentions it

First I tried 12.04 but both the installer and the live boot both half loaded the interface and then stopped, however mouse was movable etc.

Then tried 11.10 where I managed to get it installed first time, but I wasn't getting a grub menu on boot, and played around with grub and broke it some more so decided to start fresh.

Since then whenever I install, once its rebooted I just get a flashing cursor + black screen. I have tried booting off all drives in the system rom the bios but it strangely does the same thing.
Have you tried the boot option ***nomodeset*** or some of the other boot options? See this link
[[COLOR="Red"]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")
> 
Also have tried setting the boot loader device to both /dev/sda, as well as /dev/sda1, both with the same effect

You should install grub into the beginning of the drive, that is
***/dev/sda***
otherwise it is not found by the bios during boot.

---

### Post by mortuk on 2012-04-19
ok thanks will try that now

also tried boot-repair, log - [http://paste.ubuntu.com/936951/](http://paste.ubuntu.com/936951/)

---

### Post by mortuk on 2012-04-19
> **sudodus said:**
> Have you tried the boot option ***nomodeset*** or some of the other boot options? See this link
[[COLOR="Red"]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

How do I do this? My live USB boot only gives me:
try without installing
install
check for defects

None of the other f1-6 options

---

### Post by audiomick on 2012-04-19
> **mortuk said:**
> How do I do this? My live USB boot only gives me:
try without installing
install
check for defects

None of the other f1-6 options

Did you read this section?
[https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options]("https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options")

It tells you how to get to those using the live CD / USB

---

### Post by mortuk on 2012-04-19
yes, for some reason i dont get that come up

i created my live USB using the startup disk creator, could that be causing it?

---

### Post by sudodus on 2012-04-19
> **mortuk said:**
> yes, for some reason i dont get that come up

i created my live USB using the startup disk creator, could that be causing it?

If it is still not working, try with unetbootin 
[[COLOR="red"]_http://ubuntuforums.org/showpost.php?p=11546560&postcount=5_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11546560&postcount=5") You can edit boot options after pressing the TAB key in the unetbootin menu.

or the method in this link
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1958073_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1958073") Here you should get the first menus (just like from a CD).

Good luck :-)

---

### Post by audiomick on 2012-04-19
> **mortuk said:**
> 
i created my live USB using the startup disk creator, could that be causing it?
I can't say for sure, but I wouldn't imagine so. The startup disk creator is the "official" way of doing this. It should work properly...

---

### Post by flurospar on 2012-04-19
Seems like you badly need Unetbootin, that thing works most of the time for me vs the startup disk creator but YMMV.

---


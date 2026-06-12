---
title: "usb  harddrive"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by dabazzman on 2008-08-06
I have 8.4 installed on my secondary [usb] harddrive and I know that it works somewhat as I'm running it right now. My problem is that every time I boot up Linux it wants to go into install. If I tell it to go ahead all it seems to look at is my primary harddrive, which isn't where it is. I somehow need to tell it to continue in the partitioned hd it is mounted on. Any ideas?

---

### Post by wolffangalchemist on 2008-08-06
how did you go about installing it on the usb drive did you make a ISO bootable from it or install it on the drive from the cd?
i installed it on a usb drive from the cd fine just had to disconnect my internal hard drives so not to mess up my MBR on them.
i boot it from the bios boot menu(press F10 for me it's diff on some pc's).

---

### Post by s3kt0r on 2008-08-06
hi, i think i understand your problem. but there's something i don't,  is if you are running it right now, and ubuntu asks you to install the whole thing again (right?), over and over, how the installer and/or grub don't recognize the partition? did you try to disconnect your first hdd and then run the installation?
i have several disks and somehow, sometimes, the hdds don't show up in POST, and because of that, grub fails to boot (i had same problem with windows, mobo must be in it's final days, i guess :D )
wish you luck, greetings

---

### Post by firejeep on 2008-08-06
i think i can help you.. dont load the live image on the usb hard drive. go into ur bios change the boot order cd rom 1st usb device 2nd and ur primary hard drive 3rd this will make it so u can burn the linux ISO or IMG or what ever format it is to a cd (i suggest if u have an XP box to use a program like ultra iso or alcohol 120% to burn the image then place it in ur box with the USB drive on it then boot it off the cd then install it to the usb drive the best way to insure its going to only the usb device is to disconnect the primary drives then after the install reconnect everything and plug in the usb drive this should boot the usb device first before the primary drive and ur linux OS will boot as if it were on an internal drive this is how i am running my laptop and its the only way i can run it being that the laptop will not recognize the internal drives (alienware M7700) if you have any questions please e mail me at [email]firejeep@hotmail.com[/email]


 FireJeep

---

### Post by dabazzman on 2008-08-06
I burned the iso to a cd and installed it. I was asked what size partition I wanted to use, and since my largest option was 30gb [I wanted 100gb] that's what I went with. If I look at my usb hd using windoze XP it shows that there is Unbuntu using 30gb on it. Wierd, it dual boots no prob without the cd but then starts into install mode.I cancel the boot and it seems to fire up. Firefox works, open office works, and i have my soundcard working now.
I never disconected the primary hd when I installed it.

---


---
title: "unmounting problem"
date: 2013-07-20
forum: New to Ubuntu
---

### Post by Elysnoz on 2013-07-20
Sorry for the noob question, just switched from windows and never used any kind of linux before.

So I finally got Ubuntu 12.04 installed and working (despite having broken optical drive and failing at the usb method) but now I want to get rid of windows 7. Downloaded Gparted Partition Editor and I "Think" Sda2 is the one I need to wipe but it is mounted and when I try to unmount it through Gparted I get:
**Could not unmount /dev/sda2**
umount: /host: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

So then /I figured out how to open terminal and I have been trying various commands but nothing seems to be working.

I type in: # unmount /dev/sda2
no response

# unmount -l /dev/sda2
no response

Tried various combos with fuser, sudo, -f, -m, ect but nothing seems to unmount it which means Gparted won't let me kill it and windows 7 remains there taunting me. -.-

Obviously I have absolutely no idea what I am doing.. Please forgive my noobiness but could someone please help me to get rid of windows? I have been reading around trying to get all this done for about the past 15 hours straight and starting to get a headache lol.

Thanks a bunch for your time. ^,^

---

### Post by deadflowr on 2013-07-20
Your running WUBI, as the /host line means.
Wubi installs Ubuntu inside Windows, so trying to remove it would also remove Ubuntu.
Look at this for true dual boot
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

And go here to get the full Ubuntu installation disk
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Read the full installation instructions per version you choose.

---

### Post by Elysnoz on 2013-07-20
Hmm, those instructions involve using a disk and unfortunately my optical drive is dead. I do have a 4gig thumb drive but not sure how to get that to work. Any way around needing the disc that will let me delete windows after I install the ubuntu os?

When I tried to install with usb before it seemed to be working but then step 2 it asked to to enter the registry path or something and I couldn't figure out what to type in.

---

### Post by deadflowr on 2013-07-20
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

---

### Post by Impavidus on 2013-07-20
You could try migrating wubi to a partition of its own and then removing the windows partition: [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

---


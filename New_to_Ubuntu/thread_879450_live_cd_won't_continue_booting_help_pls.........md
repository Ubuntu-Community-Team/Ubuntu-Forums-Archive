---
title: "live cd won't continue booting help pls........"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by co_reynald on 2008-08-04
i'm a newbie in ubuntu and i'm really interested to try ubuntu. the problem is the live cd won't work on my laptop.. after i choce the first option run ubuntu without etc your computer it will just turn into black and the computer will just continue on blinking i wait for almost 20mins and nothing happen...
i tried to use the same cd to other laptop and it work fine... i tried looking for solution on this forum but nothing seems to work... anyway my pc is a asus a6rp  tnx alot

---

### Post by jualin on 2008-08-04
Try running the LiveCD on Safe Graphics Mode. When you get to the menu of "Install Ubuntu" and "Try Ubuntu without making any changes" press F4 and switch to "Safe Graphics Mode. This will likely solve your problem.

---

### Post by mcduck on 2008-08-04
Try the safe graphics mode option from the live-cd's boot menu.

The black screen sounds like Ubuntu is booting fine but because of compatibility issues with your graphics card uses a resoulution that your display doesn't support. If the safe graphics mode works you should be aböle to install Ubuntu, and then after that install the correct driver for your graphics card (or just try to get correct resolution with the driver included).

---

### Post by jualin on 2008-08-04
If that doesn't work then you may need to add some command to the boot line. [Check this website]("https://help.ubuntu.com/community/BootOptions") for instructions of how to do this step. Common commands that should help are listed on the link. > Example: Adding the vga=771 option
noapic  Hope this helps!

---

### Post by co_reynald on 2008-08-04
tnx for the quick reply i'll try it ryt away and tell you guys what happen....:)

---

### Post by co_reynald on 2008-08-04
ok here what happen
boot option   file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quite splash --
i add vga=771
boot option   file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quite splash -- vga=771
the kernel loaded then turn black blick a couple of times then it turns black total without the blinking icon anymore
i tried adding noapic
boot option   file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quite splash -- vga=771 noapic
same result... is there something wrong with what i did?? i also tried pressing F4 a go to safe mode nothing happens also.... it just turn black... the thing is i'm not installing it yet i just want to try the live cd... do i need to install it? tnx again......

---

### Post by co_reynald on 2008-08-04
i don't know if this is the problem.. well i found out that ati radeon 200m card don't work very well with ubuntu? i don't know if this is true>>> pls anyone need help....
tnx in advance

---

### Post by jualin on 2008-08-05
You shouldn't have a video problem if you run in Safe Graphics Mode since it loads a "universal" driver called "vesa" so it should be another problem. Have you check the LiveCD for errors? Maybe the image you downloaded is corrupt. Do an md5sum check on the disk and maybe try downloading again and burning the CD on a lower speed. Many errors are usually caused for having a LiveCD with defects. Hope this helps!

---

### Post by hotrod6657 on 2008-08-05
> **jualin said:**
> You shouldn't have a video problem if you run in Safe Graphics Mode since it loads a "universal" driver called "vesa" so it should be another problem. Have you check the LiveCD for errors? Maybe the image you downloaded is corrupt. Do an md5sum check on the disk and maybe try downloading again and burning the CD on a lower speed. Many errors are usually caused for having a LiveCD with defects. Hope this helps!

Error check or varifying the md5sum is what i would recommend too.  I've have a lot of iso images not burn right, probably a combination of the optical drive and software i use.  If you just select the check CD for errors option it will run through a test, might take some time so try and be patient.  At the end it will either say that the CD passed or that there's something wrong with it.  If there's something wrong with it then you'll have to re-burn, or maybe re-download the iso image.

hotrod

---

### Post by co_reynald on 2008-08-05
tnx for the reply.
i tried both my live cd's at home ubunto and sabayon using my desktop and they both work fine. the only problem is i can't use it on my laptop. i tried the safe mode then after loading kernel my monitor turn black and nothing happen. i don't know what is wrong... tried looking in the internet and found out that there are some issue about ati radeon 200m when ur using ubunto or sabayon

by the way im trying to dual boot my desktop and found out many instruction on doing it here are two of them
[http://www.youtube.com/watch?v=oVOsHrYF9XI](http://www.youtube.com/watch?v=oVOsHrYF9XI)

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1)

they are almost similar the only difference is in the partition part where one use manual i think and the other one use guided. which one do you think is better. and thus this step also works on sabayon mini? cause when i use those 2 live cd they look alike so i'm guessing that same procedure applies... tnx agian for the support

---

### Post by hotrod6657 on 2008-08-05
if you use guided it will give you a slider that you can use to tell it what percent of your drive you want used for Ubuntu.  It will take care of setting up your swap and mount point.

If you use manual you'll have to do it yourself.  It's pretty easy.  Just say that you want to make one partition for you install and choose how large and make it ext 3 for the format, and set the mount point to /.  Then make another partition, about a gig, and format that to swap.  You should be able to do that within the installer so you won't need to use a partitioner or anything.

you may want to try the alternate CD to install on your system.  It will install the same thing, you just don't get the Live CD part of it.

---

### Post by tuxerman on 2008-08-06
I always recommend using the manual option during partitioning, especially if you want to be sure of what you are doing, and more so if you have important data on your disks. You can see what exaclty will happen and where the OS is gonna be, etc.

---

### Post by hotrod6657 on 2008-08-06
Very true.  The first few times i did installs i didn't, just because i wanted to make sure i knew what partitions i should make but once that was laid out for me manual was the way to go.

---

### Post by fuzzyk.k on 2008-08-06
maybe there is a problem with your cd /dvd drive ?

---

### Post by jualin on 2008-08-06
> **co_reynald said:**
> tnx for the reply.
ried looking in the internet and found out that there are some issue about ati radeon 200m when ur using ubunto or sabayon



I have seen many replies saying that your video card was supported by the xorg driver so it shouldn't be a problem. One thing that you can try is installing Ubuntu using the "Alternate CD" (text installer) which would install Ubuntu without needing drivers for your video card.

---


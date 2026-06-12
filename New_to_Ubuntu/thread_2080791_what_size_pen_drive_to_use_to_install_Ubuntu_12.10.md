---
title: "what size pen drive to use to install Ubuntu 12.10?"
date: 2012-11-05
forum: New to Ubuntu
---

### Post by MWSwhip on 2012-11-05
If i wanted to start ubuntu 12.10 from a pen drive, what would be the best size to buy?

I understand that you need an empty drive to burn an Iso image of Ubuntu 12.10 onto it.  And conversely once you have it burnt into the pen drive it cannot be used to upload other files , folders or other software into it even if you had empty space left.

Am I correct?

---

### Post by Abhinav Kumar on 2012-11-05
> **MWSwhip said:**
> If i wanted to start ubuntu 12.10 from a pen drive, what would be the best size to buy?

I understand that you need an empty drive to burn an Iso image of Ubuntu 12.10 onto it.  And conversely once you have it burnt into the pen drive it cannot be used to upload other files , folders or other software into it even if you had empty space left.

Am I correct?
Hi
I think a 2GB pendrive would be sufficient.

For making pendrive bootable, you generally have to format it.
So, if I correctly get your question, you want to store some files in the pendrive after it has been made bootable.  You can store some files in that pendrive.:)

Regards ,
Abhinav

---

### Post by Jeffreytooker on 2012-11-05
> **Abhinav Kumar said:**
> Hi
I think a 2GB pendrive would be sufficient.

For making pendrive bootable, you generally have to format it.
So, if I correctly get your question, you want to store some files in the pendrive after it has been made bootable.  You can store some files in that pendrive.:)

Regards ,
Abhinav

The recommendation for 12.04 is 4G stick.  I would think that would also be sufficient for 12.10.  

Jeffrey

---

### Post by mastablasta on 2012-11-05
yes you can add files to it. i have Xubuntu 12.04 on 4 GB drive (which takes about 700MB), portable virtual box, some personal data and plenty portable windows applicaitons. all together is 3GB. which still leaves me 1GB for various data. e.g for a divx movie...

---

### Post by gridd on 2012-11-05
> **mastablasta said:**
> yes you can add files to it. i have Xubuntu 12.04 on 4 GB drive (which takes about 700MB), portable virtual box, some personal data and plenty portable windows applicaitons. all together is 3GB. which still leaves me 1GB for various data. e.g for a divx movie...

how do you achieve this I have tried to burn it to a cd but the file is too large.I tried pendrive linux but I may have a faulty flash drive it didnt work is there a how to anywhere? I have looked but I cant find a recent one that covers 12.10 thanks.

---

### Post by SBMN7 on 2012-11-05
Bro, 2GB is enough for it.

---

### Post by newb85 on 2012-11-05
> **gridd said:**
> how do you achieve this I have tried to burn it to a cd but the file is too large.I tried pendrive linux but I may have a faulty flash drive it didnt work is there a how to anywhere? I have looked but I cant find a recent one that covers 12.10 thanks.

Yes, Ubuntu 12.10 is the first release that will not fit onto a 700MB CD.  You either need a flash drive or a DVD.

When you say setting up your flash drive with pendrivelinux didn't work, what specifically didn't work?

---

### Post by mastablasta on 2012-11-05
what operating system do you use? try unetbootin instead of pendrive linux. also it seems some good USB driver do not get recognised by BIOS so you can not boot from them (a workarround is to use CD or floppy with boot manager installed to boot from USB). 
 
otherwise if you have windows, Linux LiveUSB has a very nice userfriendly interface.
 
after the image is copied to USB then you just add data to it (perhaps in separate folder). 
again linux liveUSB has a nice removal utility in case you want to remove it from USB and then Copy another version on it.

---

### Post by mcduck on 2012-11-05
> **SBMN7 said:**
> Bro, 2GB is enough for it.

1GB is enough. The disc image is less than 800MB. :)

You only need more space if you plan on using the USB drive to run Ubuntu, rather than just as install media.

For a live/setup, 4GB is a decent choice, anything above that gives you more space but requires some extra manual work to get access to that space from within the live system itself, due to the 4GB filesize limit on FAT filesystem limiting the size of the virtual disk file on the drive.

...and if you just want to have a bootable USB drive for installing Ubuntu, and also use the same drive for storing other files, there's also the usefull option of installing Grub on the drive, allowing you to boot multiple .iso files directly withouyt having to ever actually "burn" the image to the drive...

---


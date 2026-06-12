---
title: "USB 4 GB Thumbdrive Live Question"
date: 2014-09-18
forum: New to Ubuntu
---

### Post by Thomas_Niccolai on 2014-09-18
Hello Dear Ones:

This is a test post. I have created a thumb drive which contains  Ubuntu 14.01.1. I was on You tube the other day watching a video on installation. The presenter said that if you created a thumb drive version you would be missing a file on the thumb drive that would be on the DVD version. He did not mention which file would be missing or how to add that file to the thumb drive version. I also want to know if I could do a full installation on a western Digital My Book external hard drive so I can run my version absolutely separate from windows.

Thanks for your help on this. I have so much to learn...I think it will be a good exercise for me though.

Sincerely

Thomas Niccolai

---

### Post by Impavidus on 2014-09-18
I don't know what missing file he was talking about. But sure, you can install Ubuntu on an external drive. The surest way to make sure the boot loader isn't installed on the internal drive is by disconnecting the internal drive (with the Windows boot loader) before you install Ubuntu.

---

### Post by Thomas_Niccolai on 2014-09-18
Thanks for the help. For now I have only two more questions for you. What virus protection would you advise that I use and is a Linux firewall also necessary?

---

### Post by ThatBum on 2014-09-18
There aren't really any viruses for Linux. Some exist, but they are unable to propagate well due to Linux's permissions system, so you don't see them in the wild. Basically, the best antivirus for Linux is your brain. Don't run any suspicious commands and be wary of software from third-party sources.

The antiviruses for Linux (ClamAV for example) scan for Windows viruses and are designed for servers so they don't pass on viruses to Windows machines.

Ubuntu comes with a firewall, ufw. Turn it on with [FONT=courier new]sudo ufw enable[/FONT] in a terminal. It's not on by default because Ubuntu doesn't come with any software that listens on ports, but it can't hurt to turn it on. Just remember to add rules if you need P2P programs to work or whatever. You can install a GUI for it with [FONT=courier new]sudo apt-get install gufw[/FONT]. It should then show up in your settings menu.

---

### Post by mastablasta on 2014-09-19
it could be that wubi (which is not supported anymore anyway) is missing on USB. hard to say since i never heard of this.

otherwise to external drive - either unplug internal drive while doing it or make sure you choose mnual install and put grub on the root (/) of external drive.

one thing to note is that USb transfer speeds are slower than SATA. it should still work quite well for a number of things.

---

### Post by JKyleOKC on 2014-09-19
I believe the OP may have a serious problem installing on the WD MyBook, if he wants to use the external drive for anything else: The install will reformat the drive to EXT4 from NTFS! This won't be a problem if the drive will be used only for Linux afterward, but Windows will not recognize the format at all...

---

### Post by Pelvur on 2014-09-19
> **JKyleOKC said:**
> I believe the OP may have a serious problem installing on the WD MyBook, if he wants to use the external drive for anything else: The install will reformat the drive to EXT4 from NTFS! This won't be a problem if the drive will be used only for Linux afterward, but Windows will not recognize the format at all...

He doesn't need to occupy the whole drive. He can make a partition for / with ext4 (or two if he wants /home to be on separate partition, or even more if he wants /boot and /var to be separate as well) and leave the rest of the drive with NTFS.

---

### Post by Thomas_Niccolai on 2014-09-19
Thanks so much everyone! There is so much to learn! I love it though. I am reading through the official online manual and it is great. I was not even aware of this world until just a few days ago. I want to make this work but I do intend to take my time and just enjoy learning everything I can.

I am using windows 7 which I love...I had the idea of isolating Unbuntu while I am testing it on the WD external hard drive and leaving the rest of the computer as a windows system for now...I think it will work.

---

### Post by stalkingwolf on 2014-09-20
in 10 years i have had 1 virus. it came thru facebook chat.  I now always install clam tk it has never let me down.

---

### Post by Thomas_Niccolai on 2014-09-20
Thanks for the information. Can I download clam tk via windows 7 downloads? If not where do I go in Ubuntu to get it?

Sincerly Tom and I am also dreaming of freedom!

---

### Post by yancek on 2014-09-20
I would just type clamtk in the Search box in the software center.  It was available for earlier versions per the site below.  There is not data on the site.

[https://apps.ubuntu.com/cat/applications/precise/clamtk/](https://apps.ubuntu.com/cat/applications/precise/clamtk/)

---


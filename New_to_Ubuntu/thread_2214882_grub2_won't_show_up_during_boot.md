---
title: "grub2 won't show up during boot"
date: 2014-04-03
forum: New to Ubuntu
---

### Post by aviv3 on 2014-04-03
(Well I hope that the Absolute Beginners Section really is for ABSOLUTE beginners)


So this is the first time I ever (tried to) dual booted a machine. I started with installing win7 about a month ago, when I did it I left 50 GB for Ubuntu in the hard drive during the partitioning process.

 Yesterday I tried to install Ubuntu, and it all went fine; I chose the option to install Ubuntu along-side win7 and when the installation process ended I restarted the computer, only problem is that it 

automatically starts up in windows and I have no idea how to change it to Ubuntu/give me an option to choose between the two on startup.

If I understand correctly, I should be getting gnu grub2 when I start up or some other boot loader, not sure how to set it up tho..

I wanted to try some thing like installing easyBCD but I'm kinda scared to mess around with my drive without some proper guidance, so, yeah.


If it matters, here's how my partitions are set up (the one with 7.9 GB is Linux Swap Space or something similar)
[IMG]http://i.imgur.com/UkIh0ik.png[/IMG]

---

### Post by sudodus on 2014-04-03
Welcome to the Ubuntu Forums :-)

Maybe Windows is installed in UEFI mode. Then Ubuntu must also be installed in UEFI mode. See this link

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)


Maybe you installed the bootloader to the wrong place. It should be installed to the head of the drive, not to a partition, so /dev/sda (not for example /dev/sda5)

It can be repaired according to this link

[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

```
sudo mount /dev/sdXY /mnt # Example: sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sdX # Example: sudo grub-install --boot-directory=/mnt/boot /dev/sda
```

or you can simple reinstall Ubuntu and remember where to install the bootloader.

Anyway, please tell us about your computer:

- is there UEFI or old style BIOS?
- what version of Windows

and please boot the computer from the Ubuntu install drive and run this command and post the output in a reply
```

sudo parted -l
```

Edit: The end of the command should be 'space minus ell'

---


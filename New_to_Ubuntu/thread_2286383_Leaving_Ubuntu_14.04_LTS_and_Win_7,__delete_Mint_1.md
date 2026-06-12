---
title: "Leaving Ubuntu 14.04 LTS and Win 7,  delete Mint 17.1"
date: 2015-07-11
forum: New to Ubuntu
---

### Post by MIKRO402 on 2015-07-11
I would like to leave Ubuntu 14.04 and Windows 7 but delete Mint 17.1. I have liiked at Gparted but am unsure which partion is which. Will I also have
to edit the Grub2 menu?

Thanks...

---

### Post by Bucky Ball on 2015-07-11
Using Gparted: Windows is NTFS filesystem. The system you are booted into is EXT* and has a key next to it and the mountpoint /. The other Linux install is an EXT* filesystem. 

Delete the correct partition and resize using live media is best (what you installed with> Try Ubuntu> Gparted). Yes, you may have to fiddle with grub, depends which OS was installed last probably.

---

### Post by Vladlenin5000 on 2015-07-11
The first thing is assuring that Ubuntu 14.04 - the one you want to keep - is in control of Grub. If needed, boot Ubuntu, install (or reinstall) Grub and update it. Reboot to make sure everything is working as expected.
That done, in the same Ubuntu session it should be easy to understand which partitions is which: The partition you wan to keep (Ubuntu) is the one you won't be able to delete or even edit due to it being in use; The Windows partition should also be easy to spot; that leaves the other linux partition (Mint) and, provided it isn't mounted in your Ubuntu session - it shouldn't be -, that's the one you can and want to delete. Next, just boot Ubuntu again and upgrade Grub to reflect the changes.

---

### Post by grahammechanical on 2015-07-11
You first need to find out whether Ubuntu or Linux Mint is controlling the Grub boot menu. If Linux Mint is controlling Grub and you delete Linux Mint, then you will have a broken Grub menu.

So, Is Ubuntu at the top of the Grub boot menu? Another question to answer: Does this machine has a BIOS or UEFI boot system. If it is BIOS then load Ubuntu. Open a terminal and run

[code]sudo update-grub
sudo grub-install /dev/sda{/code]

I am assuming that you only have one hard disk and all 3 OS are installed on it. Inaccurate information leads to inaccurate advice. Those 2 commands should put the Grub of Ubuntu in change of the boot menu. You will need to run them again once you have removed Linux Mint to get rid the the entries for Linux Mint from the boot menu.

As to which partitions are being used for what, we cannot say. A screen shot of what Gparted is showing you would be useful. Do you not think?

Regards.

---

### Post by MIKRO402 on 2015-07-11
> **grahammechanical said:**
> You first need to find out whether Ubuntu or Linux Mint is controlling the Grub boot menu. If Linux Mint is controlling Grub and you delete Linux Mint, then you will have a broken Grub menu.

So, Is Ubuntu at the top of the Grub boot menu? Another question to answer: Does this machine has a BIOS or UEFI boot system. If it is BIOS then load Ubuntu. Open a terminal and run

[code]sudo update-grub
sudo grub-install /dev/sda{/code]

I am assuming that you only have one hard disk and all 3 OS are installed on it. Inaccurate information leads to inaccurate advice. Those 2 commands should put the Grub of Ubuntu in change of the boot menu. You will need to run them again once you have removed Linux Mint to get rid the the entries for Linux Mint from the boot menu.

As to which partitions are being used for what, we cannot say. A screen shot of what Gparted is showing you would be useful. Do you not think?

Regards.

Here is the screen shot:    [ATTACH=CONFIG]263151[/ATTACH]

---

### Post by Bucky Ball on 2015-07-11
Now boot into the other Linux OS and provide the same screenshot. As I imagined (which is why I didn't ask) it is anyone's guess. 

All that can be known for sure is that whatever you were booted into when you took that screenie is on sda12.

---

### Post by MIKRO402 on 2015-07-12
> **Bucky Ball said:**
> Now boot into the other Linux OS and provide the same screenshot. As I imagined (which is why I didn't ask) it is anyone's guess. 

All that can be known for sure is that whatever you were booted into when you took that screenie is on sda12.

Here is the other screen shot:

[ATTACH=CONFIG]263156[/ATTACH]

---

### Post by Bucky Ball on 2015-07-12
Same screenshot. Same OS. sda12 is /. Boot into the other Linux OS.

Probably best to right click and label the partitions in future if you are not going to keep a note of what's where. You can do this from live media.

---

### Post by Geoffrey_Arndt on 2015-07-12
You can (and should) label the partitions, starting with the default linux partition that is auto selected by grub2 (e.g., the default linux).   Label it via gparted gui, and then boot into the other (select it manually from grub2 screen), and then label it also.   Makes life much simpler if you multi-boot many distros or even versions of Windows.

oops . . I see Bucky already is on the same track!:lolflag:

---

### Post by MIKRO402 on 2015-07-12
> **Bucky Ball said:**
> Same screenshot. Same OS. sda12 is /. Boot into the other Linux OS.

Probably best to right click and label the partitions in future if you are not going to keep a note of what's where. You can do this from live media.

They seem to be screen shots  to me..

---

### Post by Bucky Ball on 2015-07-12
No, they are the same screenshot. Both show / as sda12. You are booted into the same OS each time. We need you to boot into the other Linux OS and take another screenshot then post it here. / will be allocated to another partition. An EXT filesystem one.

---

### Post by yancek on 2015-07-12
The image you posted in post #5 shows / on sda12 while the image you posted in post #7 shows / on sda11.  So if you know which you booted first, you should know which is Mint/Ubuntu.

---

### Post by MIKRO402 on 2015-07-13
That finally makes sense.. Thank you!

---


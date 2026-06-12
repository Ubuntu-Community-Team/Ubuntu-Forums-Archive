---
title: "Grub boot problem"
date: 2014-05-30
forum: New to Ubuntu
---

### Post by Otacon.hugs on 2014-05-30
Hello all at ubuntu forums
This is my frst post so I hope I do not too bad

I recently installed Ubuntu 14.04 on my computer as a dual boot option to Windows 7 Ultiamte (both 64bit) by using a bootable USB
But upon boot i come across a certain problem
I have researched for about a day and all I can find is people who have meesed with their partitions and as a result have encountered something similar to my problem.
What happens is that when I boot my pc, it takes me to a Command prompt screen that shows no such partition (with a code line/number) and entering grub rescue mode.
In order to get to an OS, upon boot, I must go to boot screen via pressing F11 and then select my primary hard drive (not my main ssd, which Windows is installed on, Ubunut is installed on a secondary drive) 
after selecting a hard drive  get a pink screen with 5 options such as Ubuntu, advanced options and last one is Windows 7. from this screen i can then boot into a selected OS.

shouldnt it automatically take me to that pink screen?:shock:

I am not sure what to do and my searches have only brought about problems from people who have messed with their partitions,so i wanted to be sure before proceeding :)
I hope i did not do too bad for a first post 
And thank Y'all In advance!!:D
PS (for some reason Ubuntu is very slow on my PC, but with my current setup, its kinda weird that i sometimes encounter loading and speed problems....a 4770K must stand for something right?):confused:

---

### Post by sudodus on 2014-05-30
Welcome to the Ubuntu Forums :-)

I think you installed the bootloader into 'your primary hard drive', not 'your main ssd'. I think you can get into your BIOS/UEFI menu system and change the boot order, so that it will boot from the correct drive automatically (so that you need not do it via F11).

---

### Post by Otacon.hugs on 2014-05-30
Sorry if this may annoy you, but can you provide a little instruction on how to go about doing that? and how to change it back to normal if I uninstall Ubuntu? Thanks in advance for your help!

---

### Post by sudodus on 2014-05-30
I suggest that you try to enter into your BIOS/UEFI menu system. That is different between computers. Often it is shown on the first screen during boot for maybe one second with hotkey to press, ESC, F12, ... If you cannot find it looking at the boot screen, and cannot find it by trial and error, you can browse for it in the internet. Search for something like ***boot menu hotkey {and the name and model of your computer or motherboard}***


But if you want to reinstall grub you can use the instructions in this link and put it where the computer is searching now

[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

If you want to get back to only Windows, and you have not touched the Windows disk, there should be no problem, but I am afraid that you have at least messed with the boot sector, otherwise the computer should have booted into Windows now. Then you should reinstall the Windows bootloader, which can ge done from a Windows install disk or some utility disk (or USB drive), that you can get via the internet (download an iso file).

---

### Post by Otacon.hugs on 2014-05-30
I just figured it out, I own a z87 fatility killer mother board which redirects everything to SSD boot, I just had to replace Primary HDD under BIOS influence from SSD to HDD and i was fine, now it boots into grub, and as for un installin, will creating a repair disk and running a few command for boot loader re-installation work?

---

### Post by sudodus on 2014-05-30
Congratulations, that your problem is solved :KS

Yes, I think creating a Windows repair disk and running a few command for boot loader re-installation works.

When you have no more question related to this matter, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED.

---


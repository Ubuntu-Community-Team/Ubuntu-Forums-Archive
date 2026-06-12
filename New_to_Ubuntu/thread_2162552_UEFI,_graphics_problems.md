---
title: "UEFI, graphics problems"
date: 2013-07-15
forum: New to Ubuntu
---

### Post by Edathi on 2013-07-15
I have tried installing Ubuntu on a separate drive atleast 6 times. I have been at this for 8 hours and have been getting the same error "this is not a bootable disk. Please insert a bootable floppy and press any key to try again..." I really want to try Linux/Ubuntu but I can't and its so frustrating PLEASE HELP!

---

### Post by varunendra on 2013-07-15
Welcome to the forums Edathi !
> **Edathi said:**
> I have tried installing Ubuntu on a separate drive atleast 6 times. I have been at this for 8 hours and have been getting the same error "this is not a bootable disk. Please insert a bootable floppy and press any key to try again..." I really want to try Linux/Ubuntu but I can't and its so frustrating PLEASE HELP!
Please use Boot-Repair whatever way is convenient to you : [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If it does not automatically fix the issue, post back the pastebin link to the "Boot-info" report it generates.

---

### Post by Edathi on 2013-07-15
when it asks "Is sdc (320GB) a removable disk?" does it mean is it like a flash drive or what? Im assuming no. ill go with that.

---

### Post by Edathi on 2013-07-15
here is the paste debian link just in case [http://paste.debian.net/16104/](http://paste.debian.net/16104/)

---

### Post by Edathi on 2013-07-15
The error is gone, YEA but at this moment (it's been like 6 minutes) it is still stuck at a pinky purple screen(depending on which of my monitors you look at). Is this a standard time for the first boot?

---

### Post by varunendra on 2013-07-15
Absolutely not. Who would be crazy enough to wait that long for an OS just to load? :P
Taking a look at the Boot info....

---

### Post by Edathi on 2013-07-15
After waiting for 20 minutes I decided to restart my pc and than a white dash blinked for like 10 seconds then it said have up waiting for root device. Then gave a list of problems that might be occurring. Need any more info?

---

### Post by varunendra on 2013-07-15
It seems your BIOS is set to UEFI mode while the installation is not done in the same mode (no /boot/efi mount points in fstab). I'm not very familiar with EFI based installations and may not be able to help much. Please read this guide carefully and see if it can help : [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by deadflowr on 2013-07-15
You can also read through oldfred's [UEFI Installing Tips]("http://ubuntuforums.org/showthread.php?t=2147295") tutorial thread, if it helps any.

---

### Post by Edathi on 2013-07-15
I'm so confused as to what is wrong exactly and what I need to do if you explain the problem a bit more I may be able to figure it out.

---

### Post by mastablasta on 2013-07-15
it's all explained int he links. If you have UEFI and possibley secure boot enabled mashcine, you need to install it in UEFI mode. For that the procedure is in the links. UEFI is the "new" BIOS. And requires a key to install other operating system besides microsoft windows. there could be achance of disabling the UEFI secure boto which would give you BIOS mode which should help you boot into the OS.

you mention you have two monitors - you might need to use nomodeset for first boot and then install proprietary drivers.

---

### Post by varunendra on 2013-07-15
As per the Boot-info report, your laptop is UEFI capable and it is *currently* enabled in its BIOS. However, Ubuntu somehow got installed in 'legacy' mode (maybe you turned EFI in BIOS off at that time, or turned it on later??).

Either that, or Boot-Repair could not fix the problem correctly (whatever it was) and did some changes that are not compatible with EFI based setup.

Just forget the problem for a while and read the UEFI page to get a better understanding of it. For troubleshooting, the link deadflowr posted above could be the best one. But you will be able to follow the tips/instructions there in a better way if you get some understanding of the UEFI setup first.

In short, if your windows was installed in EFI mode, you have to install (or change the current installation of) Ubuntu in EFI mode as well. If windows was a non-EFI setup, then you may be good by just turning EFI off in BIOS. But I can't say for sure what exactly you'll need to do at this point.

---

### Post by Edathi on 2013-07-15
So I am on the "installation type" screen do I reinstall erase and reinstall or what? I custom built my desktop and in my bios there is no uefi or edit mode and It is 4:15 am and I have weight lifting in 4 hours and just want this working before I go to sleep.

---

### Post by Edathi on 2013-07-15
From what I can tell "Windows 7 UEFI, or new self built system - no secure boot issues

You will not have any of the secure boot issues, but still should use the newest versions of Ubuntu. They include many UEFI & grub install updates.
You still have gpt partitioning and should use Windows disk tools to shrink Windows if you have Windows.
If installing only Ubuntu (no Window), see partitioning below. But you then can use either BIOS or UEFI, but probably should use gpt partitioning." Is the only part in the articles that applies to me and that part isn't very helpful.

---

### Post by varunendra on 2013-07-15
Reinstalling may be of no use unless you understand which mode you are installing in and which mode is required. It may make your Ubuntu installation work, but the wrong mode may render your windows installation unbootable.

So instead of rapid posting here, just read the wiki link I gave you, or the link deadflowr gave you. Or wait until someone who is good with EFI based setups posts offering straight help.

Sorry, but I'm not able to offer more help at the moment.

---

### Post by Edathi on 2013-07-15
I disabled quickboot in my bios and launched my dvd drive in uefi mode so this will probably be my last attempt of ubuntu before I give up, ive been at this for 11 hours.

I reinstalled Ubuntu and it is at a screen saying my system is running in low graphics mode, I can't click on anything or press enter should I just restart my system?

---

### Post by Edathi on 2013-07-15
Yep. Got the same error again. I'm going to bed.

---

### Post by Edathi on 2013-07-15
Umm... I just got back from weight lifting and turned on my pc and its stuck at a black screen, I can't go into bios or anything. I cleared CMOS and unplugged and plugged back in.

---

### Post by oldos2er on 2013-07-15
Changed thread title to something more appropriate. It's a good idea to choose a title that reflects your problem rather than just "HELP!"

---

### Post by Edathi on 2013-07-15
Thanks for changing that up I jut really needed/still need help so whatever gets me an answer first is great help.

---

### Post by oldfred on 2013-07-15
Even though you have an efi partition on sdc, all your drives are MBR(msdos) so you have booting with BIOS. Windows only boots from gpt partitioned drives with UEFI. Ubuntu will boot from gpt with either UEFI or BIOS, but both systems only boot from MBR with BIOS. Both systems have to be installed in the same mode.

If black screen, most likely video issues. What video card. But sometimes other boot parameters in addition or in place of nomodeset are also required.

 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

### Post by Edathi on 2013-07-15
I have a amd raedon 7850, I'll try taking it out and putting it back in right quick... Nope, still nothing, I am new to Ubuntu/Linux so I am confused by all these terms (I'm normally really good with computers) so a bit explanation could be useful. Thanks everyone for the help so far.

---

### Post by Edathi on 2013-07-15
By black screen I mean bios isn't even posting.

---

### Post by oldfred on 2013-07-15
Fast boot in UEFI setting skips some or all of a UEFI/BIOS boot screen and jumps to booting to speed boot process. But some then cannot even get back into UEFI to change settings or have to be very quick.

Do not know much about AMD as I have nVidia.
       [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[URL="http://ubuntuforums.org/showthread.php?t=2050320"]http://ubuntuforums.org/showthread.php?t=2050320

[/URL]
 [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_amdstock&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_amdstock&num=1)
On the proprietary driver side, the AMD Catalyst 12.11 Beta Linux graphics driver was used. For this initial testing, three discrete graphics cards from the AMD Radeon HD 5000/6000 series were used, since pre-HD5000 graphics cards are now on the Catalyst Legacy driver and the latest-generation Radeon HD 7000 series hardware still doesn't fully work with the open-source Gallium3D "RadeonSI" driver.

[URL="http://ubuntuforums.org/showthread.php?t=2050320"]
[/URL]

---

### Post by Edathi on 2013-07-15
An admin changed it to graphics issues but I turn my pc on and the screen never wakes up. ATM I can't do anything.

---

### Post by Edathi on 2013-07-15
Since all I have is my phone I posted a Instagram video on what happens. [http://instagram.com/p/bzQC2Ogags/](http://instagram.com/p/bzQC2Ogags/)

---

### Post by oldfred on 2013-07-15
That sounds more like a hardware issue where a cable or power has disconnected?

When they first started needing nomodeset, my monitor would work with BIOS and about 3 seconds into the boot process would then turn off.

---

### Post by Edathi on 2013-07-15
I checked all my wires and changed which wire my gpu was using, still nothing.

---

### Post by Edathi on 2013-07-15
heres a link to my motherboard [http://www.ecs.com.tw/ECSWebSite/Product/Product_Detail.aspx?DetailID=1265&MenuID=115&LanID=0](http://www.ecs.com.tw/ECSWebSite/Product/Product_Detail.aspx?DetailID=1265&MenuID=115&LanID=0)
and a link to someone going over the bios (not me) [http://www.youtube.com/watch?v=h0EH7W6_lAk](http://www.youtube.com/watch?v=h0EH7W6_lAk)
im on my laptop now so I can do a bit more.

---

### Post by oldfred on 2013-07-15
The screen worked before and after you unplugged it and plugged it back in, it stopped working? You did not do that with power on did you? Otherwise double check that everything is firmly seated and power all connected.

---

### Post by Edathi on 2013-07-15
no If you go back in the thread said something like "trying one last install" then i said something like"it didnt work. going to bed" when I got back on my pc it didnt work at all. so then I went through basic troubleshooting steps. making sure all plugs are good on mobo, unplugging and plugging back in etc.

---

### Post by oldfred on 2013-07-15
Can you go straight into UEFI/BIOS and does that show. Your motherboard manual should have what key to use to get into BIOS.

---

### Post by Edathi on 2013-07-15
My normal key is delete key but when i press the power button my drives all start spinning but my screens dont wake up or anything.
and my install disk is definatly good, i just installed it onto my laptop no problemat all.

---

### Post by oldfred on 2013-07-15
Then either monitor or video card have some sort of issue? UEFI/BIOS should always come up.

---


---
title: "New to Linux Multiboot problem"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Zerxez on 2008-05-25
I have have searched and searched, but cannot seem to completely solve this problem.

I installed Windows XP on hd0,0 then I installed Hardy on hd1,0 the Hardy install created a GRUB for me that worked beautifully.  Then I installed Vista on hd2,0. Yes I know, Ubuntu is now my primary OS, but I use both XP and Vista exclusively for gaming.
Next I did some research and restored the Grub, I also created a boot for Vista at hd2,0
Now for the weird part...on boot if I select Ubuntu everything is great and Ubuntu boots.  If I select XP it takes me to another boot loader and asks if I want to boot Vista or an "older version of Windows" if I select Vista there it boots into Vista.
If at the Grub I select Vista it errors out and asks me to control, alt, delete.
How do I fix this?  The Grub shows the correct options, at the correct drive locations, but it seems the Vista boot loader is still active or something and blocks me after the Grub tells the system to book from one of the Windows drives.
I have looked at a lot of threads and cannot seem to find a good answer.

---

### Post by sam_delta on 2008-05-25
try supergrub disk, make 1 grub menu for all os'es
[www.supergrubdisk.org/](www.supergrubdisk.org/)

sam

---

### Post by Zerxez on 2008-05-25
Ok, thank you I am looking at it now.

---

### Post by housam on 2008-05-25
Read this [[COLOR="Red"]_Guide_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=724817") by Bodhi.zazen :

---

### Post by Zerxez on 2008-05-25
Ok,
I downloaded the .iso and burned/booted from it.  I learned a bit and now can boot into all three OS's however it is still not ideal.

From the Grub I can go directly into Ubuntu, if I select Windows XP from the Grub it takes me to the Windows boot loader and if I choose Vista it takes me to Vista and if I choose "Older Version of Windows" it boots XP.

Isn't there a way to get all of this consolidated into the Grub so I can choose the OS I want to boot into in the Grub and have it boot directly into that OS with out having to go through the Windows boot loader to boot into one or another version of Windows?

Super Grub Disk looks like a cool tool to me and I will learn more about it.  However it does not have an obvious way to solve this problem and the help on their web site doesn't seem to address this problem either.

---

### Post by sam_delta on 2008-05-25
you can edit the file /boot/grub/menu.lst and add/edit the operating systems and partitions you wish to change from the menu. to be honest, i dont know what you have to type to actually add each of the 2 windows to the boot menu and boot from them succesfully. do some research, or wait for someone else to post on how to add an operating system to /boot/grub/menu.lst

something like this link is what your looking for
[http://ubuntuforums.org/archive/index.php/t-286157.html](http://ubuntuforums.org/archive/index.php/t-286157.html)

hope it helps
sam

---

### Post by adrian15 on 2008-05-27
> **Zerxez said:**
> Ok,
I downloaded the .iso and burned/booted from it.  I learned a bit and now can boot into all three OS's however it is still not ideal.

Let's see.
> **Zerxez said:**
> 
From the Grub I can go directly into Ubuntu, if I select Windows XP from the Grub it takes me to the Windows boot loader and if I choose Vista it takes me to Vista and if I choose "Older Version of Windows" it boots XP.

Can you please tell me how do you boot Windows XP and Windows Vista from SGD ? Which options do you use? What's the difference between using your own grub and using SGD options? Can you also post here your menu.lst?

> **Zerxez said:**
> 
Isn't there a way to get all of this consolidated into the Grub so I can choose the OS I want to boot into in the Grub and have it boot directly into that OS with out having to go through the Windows boot loader to boot into one or another version of Windows?

Usually you only can select in Grub: Linux or Windows menu (not a given windows os) but I am asking myself how did you manage to boot Windows XP directly with SGD.

> **Zerxez said:**
> 
Super Grub Disk looks like a cool tool to me and I will learn more about it.  However it does not have an obvious way to solve this problem and the help on their web site doesn't seem to address this problem either.

Super Grub Disk is not meant to recreate menu.lst but to restore them or creating menu.lst on the fly that you can use for booting some oses.

If you want to work on Rescatux maybe these problems will have an easier fix in a future.

adrian15

---

### Post by Zerxez on 2008-05-27
Hi,
Wow the amount of help and response here is great.  I have now modified my GRUB so that I have the Ubuntu options on startup and/or I can select "Windows XP or Vista" when I select the Windows option it immediately brings up the Windows boot loader and gives me the option of Vista or "Older versions of Windows" If I choose Vista it boots from that drive.  If I choose "Older versions of Windows" it boots off of the XP drive.  So I can choose to boot from any of the three drives and it default boots into Ubuntu if I turn on the computer and walk away.  This isn't bad and I can live with it.  However I expected the following:

GRUB 1.5


Ubuntu and all its variations (hd1,0)

Windows XP (hd0,0)

Windows Vista (hd2,0)

However that doesn't work. If I try to boot from the Grub to HD 0,0 it fails and says it cannot find a bootable HDD.
I know this is some how a MS thing as the drive is obviously bootable since I can get there through the boot loader.

If I want to make it a perfect world and be able to boot directly to the HDD of choice directly from the GRUB what needs to be changed or eliminate the MS boot loader or some sort of bootstrap modification to hd0,0?

---

### Post by phoenix_abhi on 2008-05-27
Ur Grub writes the other OS installed in a PC and Boot to that OS as per the User's selection. Grub is a big file compare to MBR and Cannot be saved in XP or Vista drive.
Where as MBR is not restored/fixed to configure the Linux OS.U can google for EASYBCD which may help u . are there three HDDs ?

---

### Post by bumanie on 2008-05-27
Agreed, easybcd is your easiest option.
To get all three to boot with grub, you need to add xp's boot.ini files into vista's bootlader files and then install grub to vista's mbr. It is best if vista is on the first partition of the primary drive to achieve this. xp and vista's respective bootladers recognise each other but they can't boot each other without some user intervention. Unfortunately, I can't tell you how to put the boot.ini files into vista's bootloader - but I'm sure there are some guides somewhere.

---

### Post by Zerxez on 2008-05-27
Yes there are three separate HDD's.  I have downloaded EasyBCD and will try it tomorrow night when I get back from work.  Am I then correct in understanding, that this will eliminate the need for the Grub and allow me to boot to any of the three HDD's from the MS boot loader?

---

### Post by Duck2006 on 2008-05-27
> **Zerxez said:**
> Yes there are three separate HDD's.  I have downloaded EasyBCD and will try it tomorrow night when I get back from work.  Am I then correct in understanding, that this will eliminate the need for the Grub and allow me to boot to any of the three HDD's from the MS boot loader?

Yes

---

### Post by adrian15 on 2008-05-28
> **adrian15 said:**
> Let's see.

Can you please tell me how do you boot Windows XP and Windows Vista from SGD ? Which options do you use? What's the difference between using your own grub and using SGD options? Can you also post here your menu.lst?

Usually you only can select in Grub: Linux or Windows menu (not a given windows os) but I am asking myself how did you manage to boot Windows XP directly with SGD.


I'm still waiting for your answers.

Thank you.

adrian15

---

### Post by Zerxez on 2008-05-28
I am sorry, Hopefully this is a more direct answer to your questions.  I created an SGD CD and booted into it.  As it is the first time I had seen it  I went through and looked at it, but didn't see an obvious solution to my problems.  So I set the SGD disk aside and began working with all the options in menu.lst and the GRUB directly.  Right now the system boots to the Grub and I have two options 1.  All of the Ubuntu options and 2. an item I named "Boot XP or Vista" when the second option is chosen the system goes to hd0,0 and the MS boot loader launches and gives me the choices "Vista" or "an Older verison of Windows" if I select Vista it boots from hd2,0 if I choose "older version of Windows" it boots from hd0,0 which will not boot directly from the Grub.  So I did not boot directly into XP from SGD and I am to much of a noob to know if what I am doing is normal or not.

---

### Post by adrian15 on 2008-05-29
> **Zerxez said:**
> So I did not boot directly into XP from SGD.

That's what I wanted to know. Ok. Thank you very much.

adrian15

---


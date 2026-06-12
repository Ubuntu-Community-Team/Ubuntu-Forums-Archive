---
title: "NTFS windows partition not detected Gparted or XUbuntu install"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by Omnilol on 2013-02-17
Hi there
So I have a eeepc, EM250, and long time ago i had a Ubuntu 10.04 or something like this on it. To do short i had to install Windows Xp on it 2 weeks ago for my korean girlfriend and her korean softwares (wrong idea... :D ) . Windows being slow and ****, i suspect it to be a zombie NetBot version blabla, i decided to come back to my trusty Ubuntu. Here the deal 
when i installed Windows xp i formated my hard drive to 2 partitions, first one to NTFS, second one to unallocated (i did format it later to fat32, after the windows install completed)
So now I have created a YUMI Multiboot usbkey with a Ubuntu 12.10 iso on and a Gparted and Partedmagic isos aswell 
I boot on my usb, choose the ubuntu install everything works well till ubuntu install has an error with the internal hard not detected.
I reboot on Gparted GUI and same deal, only my usb drive detected...
I reboot on my Partedmagic GUI and same deal only my usb drive detected... 

When Im rebooting on my  internal hard drive, Windows boots like a princess, everything s fine. 

So here am I on Partedmagic GUI on the integrated Firefox asking for some help
I browse a bit Ubuntu forums about it but found nothing really related 
Im a bit of a noob aswell but i did a fdisk -l which is only listing my usb drive as /dev/sdc1

I need to come back to a really clean, fast and light system as I had before.
please 
Omnilol

---

### Post by Mark Phelps on 2013-02-17
Sorry, but you're not going to get a "fast and light" experience with any recent Ubuntu versions -- as they are designed to run on PCs a lot more powerful than yours.

However, you could look into Lubuntu -- it's leaner and will run better on lower-powered PCs.

---

### Post by offgridguy on 2013-02-17
> **Mark Phelps said:**
> Sorry, but you're not going to get a "fast and light" experience with any recent Ubuntu versions -- as they are designed to run on PCs a lot more powerful than yours.

However, you could look into Lubuntu -- it's leaner and will run better on lower-powered PCs.
+1 for Lubuntu:D

---

### Post by oldfred on 2013-02-17
I have had same thing, but newer versions do not have the issue I thought.

My issue was XP needed chkdsk. Gparted would search for many minutes and then only show my other drives. XP booted ok. I then ran chkdsk on XP. Gparted found the sda drive right away and XP did boot a bit faster (still slow).

Other issues can be if drive was set up in RAID or LVM as gparted does not work on that. Or if drive was converted to dynamic partitions, but I think that is only newer versions of Windows.

---

### Post by Omnilol on 2013-02-17
Thanks for the answer guys.
Gonna check it right now

---

### Post by Omnilol on 2013-02-18
I did the chkdsk 2 times and it still doesnt want to detect my NTFS internal hard drive...
sorry for long update had busy day

I had an idea earlier but as a newbie im not really sure 
what if I exec, let say, Partition Magic live while booted on Windows, and format the C: from NTFS to Fat32 or ext3 ? could it work ? Windows OS would be in the Ram during the operation and would fail the next action asked after the formating ? 

anyway i ve got only this computer available for me and no other means to do test and/or open it and change i dont know what 

so once again 
I need help ...
please

---

### Post by oldfred on 2013-02-18
If Windows works BIOS must see drive, but do you have any settings in BIOS. 

Someone posted they had a BIOS setting to turn drive on, but I think that was for a new drive that was not seen or used before.

---

### Post by Omnilol on 2013-02-18
> **oldfred said:**
> If Windows works BIOS must see drive, but do you have any settings in BIOS. 

Someone posted they had a BIOS setting to turn drive on, but I think that was for a new drive that was not seen or used before.

Thanks mate it worked! 
I changed the SATA mode from IDE to AHCI and now it s back to normal Gparted detects it again.
Now I remember changing it to IDE while installing Windows XP back then let it like that as it worked. Thanks again, now it s time for me to try this Lubuntu people talked about ;D
Long life to the forum and its dudes, we may see each others later ;D

---


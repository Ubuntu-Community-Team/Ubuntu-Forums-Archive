---
title: "installed to external hard drive, windows doesn't boot"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by Durandall on 2008-07-02
I installed Ubuntu 8.04 to my external hard drive... Now... IF the external is attached, then we get a message basically saying "Do you want to start Ubuntu, or Windows XP"?  We can boot to Ubuntu or XP.  If the external is NOT attached when we boot up... Grub loader hangs.  Error 1.5, I think.  And it never boots into XP.  Doesn't even give me the option too.

Here's some back story..  I inserted the Live CD, and Wubi comes up.  I selected the first option to install/run the Live CD - then I selected the third option, to help me set up my computer to use Live CDs.  The PC rebooted, then I was running Ubuntu Live.  I installed to my external hard drive... then rebooted once that was done.  So, I think the "Help you boot live CDs" bit - is what's causing the problem, maybe.

Basically... i think my BIOS might be messed up now.  How can I fix my wife's laptop, so that it boots straight into windows?

---

### Post by meindian523 on 2008-07-02
Your BIOS is not messed up,you have installed the Bootloader to the MBR of the external drive.What you need to do is to install Grub to the MBR of the internal HDD.To do this,plug in your external HDD and follow:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

EDIT:Be sure to check the HDD you are installing to.To do this,assuming that sizes of internal and external HDDs are different,use ```
sudo fdisk -l
``` to determine the appropriate device to use(eg : /dev/hda or /dev/hdb or in Grub terminology,hd0 or hd1)

---

### Post by caljohnsmith on 2008-07-02
> **meindian523 said:**
> Your BIOS is not messed up,you have installed the Bootloader to the MBR of the external drive.What you need to do is to install Grub to the MBR of the internal HDD.
I don't think that is true--Durandall said "If the external is NOT attached when we boot up... Grub loader hangs.  Error 1.5, I think." That means Grub must be in the MBR of his internal drive, but it *points* to his Ubuntu partition on his external drive. So when the external drive is missing, Grub can't find stage 1.5 or stage2 to load and returns that error.

Durandall, you could install Grub into the MBR of your external drive, reinstall the Windows MBR into your internal drive; that way when your external drive is missing, Windows will load as normal. But to boot into Ubuntu, you would have to change your BIOS settings every time you wanted to boot off your external drive.

A better alternative would be to make a small 50 MB or 100 MB partition on the internal HDD, and install Grub there. That way on boot-up, you will always get the Grub menu allowing you to choose between Windows or Ubuntu, regardless of whether your external HDD is connected or not.

Or, if you really don't want to touch the internal HDD, you could reinstall the Windows MBR so that the internal HDD is back to normal, and then make a Grub boot floppy to boot off of whenever you want to boot your external HDD. Let me know if you need more specifics, I would have to look up some links for tutorials.

---

### Post by Durandall on 2008-07-02
> **caljohnsmith said:**
> I don't think that is true--Durandall said "If the external is NOT attached when we boot up... Grub loader hangs.  Error 1.5, I think." That means Grub must be in the MBR of his internal drive, but it *points* to his Ubuntu partition on his external drive. So when the external drive is missing, Grub can't find stage 1.5 or stage2 to load and returns that error.

Durandall, you could install Grub into the MBR of your external drive, reinstall the Windows MBR into your internal drive; that way when your external drive is missing, Windows will load as normal. But to boot into Ubuntu, you would have to change your BIOS settings every time you wanted to boot off your external drive.

A better alternative would be to make a small 50 MB or 100 MB partition on the internal HDD, and install Grub there. That way on boot-up, you will always get the Grub menu allowing you to choose between Windows or Ubuntu, regardless of whether your external HDD is connected or not.

Or, if you really don't want to touch the internal HDD, you could reinstall the Windows MBR so that the internal HDD is back to normal, and then make a Grub boot floppy to boot off of whenever you want to boot your external HDD. Let me know if you need more specifics, I would have to look up some links for tutorials.

I'd say you're more correct.  I appreciate that you want to help me get my external working better - but right now, what's more important is getting my wife's laptop back the way it was.  How do i re-install the windows MBR?  Is that even what i'm supposed to do?

---

### Post by bumanie on 2008-07-02
I believe caljohnsmith is correct - that's what I thought too. To correct/rewrite windows mbr you need to go into recovery console. [Please excuse if I get the odd detail re getting into recovery console wrong as it's a while since I've done it, but it should be self evident when you get to each stage]. 
Boot with xp disc and choose the option to repair and then choose recovery console. You will be faced with a dos-like environment, that will ask for username and admin password. You then be asked to choose which OS you want - windows should be marked as 1, therefore type 1 --> enter. Then type fixboot --> enter then fixmbr --> enter It will ask are you sure you want to do this, you answer y --> enter Then type exit --> enter and you should be able to reboot into xp. Hope I have remembered all details correctly.

---

### Post by caljohnsmith on 2008-07-02
Do you have the original Windows install CD? Just boot up the Windows install CD, enter the recovery console, run the "fixmbr" command, and you're good to go. 

If you don't have a Windows CD, then probably your best option is to use the Super Grub Disk CD to reinstall the Windows MBR, see [http://www.supergrubdisk.org/wiki/UninstallGRUB](http://www.supergrubdisk.org/wiki/UninstallGRUB). I checked their website and for some reason they seem to be down at the moment, and I'm not sure why since I've never seen that happen to them before. 

If none of the above options are available, and if you're in "hot water" with your wife and need a fix ASAP :D, you could also download the Ultimate Boot CD which has all the Super Grub Disk software included: ultimatebootcd.com. The main thing is don't let your wife panic, your problem is easy to fix. :)

---

### Post by stchman on 2008-07-02
> **Durandall said:**
> I installed Ubuntu 8.04 to my external hard drive... Now... IF the external is attached, then we get a message basically saying "Do you want to start Ubuntu, or Windows XP"?  We can boot to Ubuntu or XP.  If the external is NOT attached when we boot up... Grub loader hangs.  Error 1.5, I think.  And it never boots into XP.  Doesn't even give me the option too.

Here's some back story..  I inserted the Live CD, and Wubi comes up.  I selected the first option to install/run the Live CD - then I selected the third option, to help me set up my computer to use Live CDs.  The PC rebooted, then I was running Ubuntu Live.  I installed to my external hard drive... then rebooted once that was done.  So, I think the "Help you boot live CDs" bit - is what's causing the problem, maybe.

Basically... i think my BIOS might be messed up now.  How can I fix my wife's laptop, so that it boots straight into windows?

Ubuntu wrote GRUB to the MBR of the boot drive.  That information tells GRUB to go to the external hdd for the menu.lst file.  When you have the hdd not attached GRUB has no menu.lst to go to.

My recommendation is to install Ubuntu to an internal hdd.

---

### Post by bumanie on 2008-07-02
If you want ubuntu on an external hard drive, I suggest you follow this [http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/) If you need xp and 8.04 on the computer together, consider using ubuntu inside a vm such as vmware or virtualbox if you don't want to dual boot.

---

### Post by goforlinux on 2008-07-02
I know that alot of BIOS out there wont allow a person to boot from an external drive such as a USB. But i think sata works and firewire. Although newer systems let you im not sure about most old ones?:(

---

### Post by kansasnoob on 2008-07-02
If you do not have the XP Recovery disc(s) you can also restore the Windows mbr with this:

[http://www.download.com/MbrFix/3000-2094_4-10485990.html](http://www.download.com/MbrFix/3000-2094_4-10485990.html)

I have one. I've used it. It works.

---

### Post by Durandall on 2008-07-03
> **bumanie said:**
> I believe caljohnsmith is correct - that's what I thought too. To correct/rewrite windows mbr you need to go into recovery console. [Please excuse if I get the odd detail re getting into recovery console wrong as it's a while since I've done it, but it should be self evident when you get to each stage]. 
Boot with xp disc and choose the option to repair and then choose recovery console. You will be faced with a dos-like environment, that will ask for username and admin password. You then be asked to choose which OS you want - windows should be marked as 1, therefore type 1 --> enter. Then type fixboot --> enter then fixmbr --> enter It will ask are you sure you want to do this, you answer y --> enter Then type exit --> enter and you should be able to reboot into xp. Hope I have remembered all details correctly.

Your absolutely correct... I just did it - and it worked!  My wife isn't pissed at me anymore!!

However, there is something else.  For what I can tell, there's no reason it should ask me if I want to boot into either Ubuntu or Win XP - it should just boot to XP.  Any clue how I can fix that?

---

### Post by meindian523 on 2008-07-03
Now,can you boot both Windows and Ubuntu?If your issue is resolved,please mark the thread solved.

---

### Post by bumanie on 2008-07-03
> However, there is something else. For what I can tell, there's no reason it should ask me if I want to boot into either Ubuntu or Win XP - it should just boot to XP. Any clue how I can fix that? Don't know why that is happening, overwriting windows mbr as you've done, should remove all traces of grub. Can't explain why it hasn't. I guess you could try overwriting the mbr again via the same method.

---


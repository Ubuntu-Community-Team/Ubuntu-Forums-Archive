---
title: "Keyboard doesn't work at GRUB menu"
date: 2013-03-10
forum: New to Ubuntu
---

### Post by raj727 on 2013-03-10
I'm using Ubuntu 12.10 with a dual boot option with Windows 7.  I also have a fairly new MSI motherboard.  After a software update a few days ago, my keyboard doesn't work when the GRUB menu appears.  I'm not able to choose any option other than going into Ubuntu.  Once into the Ubuntu login screen, the keyboard works fine.  I've tried enabling and disabling the legacy USB support in the BIOS but that didn't help.  I need to get into Windows 7 to do my income tax return.

Is there anything I can try to get my usb keyboard working with GRUB?

---

### Post by RoosterHam on 2013-03-10
Not sure how relevant this is, but I have stumbled on this AskUbuntu question that sounds like the same problem. 
[URL="http://askubuntu.com/questions/198489/kubuntu-roccat-keyboard-does-not-work-under-grub-and-works-partially-in-bios"]
http://askubuntu.com/questions/198489/kubuntu-roccat-keyboard-does-not-work-under-grub-and-works-partially-in-bios[/URL]

If there is a newer release of your BIOS, perhaps see if that fixes it.

---

### Post by raj727 on 2013-03-10
My usb keyboard works as soon as I leave the GRUB menu.  I can enter BIOS, as well, before the GRUB menu appears by using the "delete" key.  It's in between the BIOS and the Ubuntu log-in screem that I have a problem.  I've also had problems with UEFI on another computer while trying to dual boot Ubuntu with Windows 7.

Is it possible to re-install GRUB?  I need to access Windows 7.

---

### Post by sully101 on 2013-03-11
As a temporary workaround so you can get your tax done have you seen this [http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order]("http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order")

---

### Post by raj727 on 2013-03-11
sully101.

Thank you.  A question though, if I change the order to start Windows 7 first, would that mean I could not boot into Ubuntu again because it would always boot into Windows 7?  This is because the keyboard should still not work in the GRUB menu and thus I could not change the order to boot Ubuntu again.  I need to be in Ubuntu to change the boot order.

My only other thought is back-up my Ubuntu files and use my Windows 7 disk to remove the GRUB program.  I could then reinstall Ubuntu and see if the GRUB is fixed.

It seems this GRUB problem is only an Ubuntu related problem and my Windows 7 should work.

I would like to keep Ubuntu but since I picked up a Samsung Chromebook a week ago, I'm wondering if I can live with the Chromebook until Ubuntu 13.04 comes out and then try that.

---

### Post by sully101 on 2013-03-12
I have read something somewhere about restoring grub from a live usb/cd so I dont think you would have to go the extent of reinstalling ubuntu etc. But as always it would pay to back up your files. A quick google gave me [http://www.noobslab.com/2011/10/install-grub2-from-live-cdusb-after.html]("http://www.noobslab.com/2011/10/install-grub2-from-live-cdusb-after.html")

@RoosterHam seems to have the answer. 

I cant stress this enough, backup before you flash your bios. I had a bad experience with my asus P8Z68 ended up buying a new chip and hot flashing the old one with "flashrom"

---

### Post by raj727 on 2013-03-24
Today I tried to repair my Ubuntu 12.10 install by putting in an install disk and repairing my previous install.  I went through the re-install process and restarted my computer to complete the repair.  However, I get to the GRUB menu (GNU GRUB version 2.00-7ubuntu11) with the various boot options (Ubuntu, advanced options... etc) but no further.  At the bottom of the screen there used to be a 8 second countdown before the highlighted option was started.  Now, there is no countdown line and my keyboard still does not work.  The arrow keys don't work to change the selection and the enter key also doesn't work to select the highlighted option of Ubuntu.  I'm stuck at the GRUB menu without any way to proceed further.  

Any suggestions would be much appreciated.

---

### Post by Bucky Ball on 2013-03-24
You could perhaps try 12.04 LTS and see if that makes a difference. It would at least help to ascertain whether this is a problem specific to 12.10. 12.04 also has five years support rather than 18 months.

---

### Post by raj727 on 2013-03-24
The other odd thing is that I tried putting in my Windows 7 disk to restore Windows but my computer ignored it and went into GRUB at start-up with the same problem.  I have two SSD's with Windows 7 on one SSD and Ubuntu 12.10 on the other.  I don't know if this is part of the problem.

---

### Post by RaHorakhty on 2013-03-25
It might be the BIOS as sully101 suggested.  Have u tried booting into Hirens bootdisk and then selecting the GRUB hd?  You might have to either upgrade (or downgrade) GRUB.  I don't know if its possible to write scripts for grub....maybe you can write your own script to take over the boot process.

---

### Post by buptwangzh on 2013-10-25
I am using Ubuntu 12.04LTS. After yesterday's updates, the arrows do not work in grub too. A little search suggests that using PageUp and PageDown instead. Then I tried PageDown, and also the up arrow works. Once enter Windows 7, I found some of the small keyboard won't work, including the down arrow. However, all keys work when I returned to Ubuntu 12.04LTS.

---


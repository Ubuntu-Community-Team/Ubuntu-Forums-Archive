---
title: "Noob Grub boot question"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by donsimon on 2008-10-31
I am a total noob to Linux, ubuntu, etc. but am working to change that!  I downloaded and burned an ubuntu CD yesterday, ran it from the CD to try it out and decided it seemed like a good idea to go with it.  I installed ubuntu 64-bit on a 4gig flash drive and both WindowsXP and ubuntu have been working fine.  Now the problem I have is that I can't boot to the original install of WindowsXP without the thumbdrive in.  Grub gives me an "error 2" and stops.  I have done some searching but haven't found an answer to my issue.  I would like to be able to boot into WindowsXP without the flash drive in, but be able to boot to either XO or ubuntu when I do have it in.

Here is what I think I have learned while looking for how to do this(feel free to correct my thinking):

The install I did set up grub on the flash drive, the MBR on the hard drive goes looking for the flash drive to get to the multi-boot window.  Am I think about that correctly?

---

### Post by Sarmacid on 2008-10-31
> **donsimon said:**
> The install I did set up grub on the flash drive, the MBR on the hard drive goes looking for the flash drive to get to the multi-boot window.  Am I think about that correctly?
I'm not an expert, but I think you're right. You can fix the grub or reinstall it in another HD, just google around for fix grub and you should find your answer.

---

### Post by Duck2006 on 2008-10-31
Some info on grub.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

In your BOIS can you chose to boot from a usb flash drive in there?

---

### Post by donsimon on 2008-10-31
> **Duck2006 said:**
> Some info on grub.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)



Ooooh, good suggestion.  I am currently reading voraciously.

---

### Post by Duck2006 on 2008-10-31
If you can boot from a usb stick, then repair you mbr of the hard drive with the recover mode on your xp win disk, This will help you set-up the flash drive,

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by caljohnsmith on 2008-10-31
Your situation is very common; most likely what happened is that Grub was installed to the MBR (Master Boot Record) of your internal Windows drive so that on start up, you get the Grub menu. The problem with that is as you've found, removing the USB drive causes Grub to choke since Grub needs its boot files on the USB drive. 

I think the most ideal solution is to reinstall a Windows MBR to your internal drive, install Grub to the MBR of your USB drive, and then set your BIOS to boot the USB drive before the Windows drive on start up. That way if you remove the USB drive, you still can boot your Windows drive just fine. 

If that sounds good to you, then first open a terminal (applications > accessories > terminal) and post output of:
```
sudo fdisk -lu
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
cat /boot/grub/menu.lst

```
And we can work from there. :)

---

### Post by haylun98 on 2008-10-31
> **Sarmacid said:**
> I'm not an expert, but I think you're right. You can fix the grub or reinstall it in another HD, just google around for fix grub and you should find your answer.
I too agreed the only (easy) solution would be to reinstall ubuntu. Grub is broken down in parts (stages) and 1st part is installed in MBR and 2nd part is usually /root partition. In this case the stage 2 portion is on the USB drive. It is not possibly to boot XP unless it is first inserted and reminds at least until xp is booting. Also visit Illustrated Dual Boot Site: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) where you can learn Grub and dual booting in depth.

---


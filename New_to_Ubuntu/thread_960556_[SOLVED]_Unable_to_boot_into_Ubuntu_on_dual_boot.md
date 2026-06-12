---
title: "[SOLVED] Unable to boot into Ubuntu on dual boot"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by Manillien on 2008-10-27
Hi

I have just installed Ubuntu on my desktop which had XP already installed. I want to dual boot, and the installation went well, and it automatically created a partition on my hard drive. I have both XP and Ubuntu on the same hard drive. When I reboot, it just boots right into XP, Grub doesn't even seem to start. I have tried doing the setup(hd0) thing in grub using the Live CD, but it doesn't work. 

I don't know if there's anything special about my computer, I do know that it has two hard drives and one of them is a mirror of the other, for security reasons. 

Anyway... any suggestions?

---

### Post by caljohnsmith on 2008-10-27
Since you have two HDDs, probably Grub was installed to the MBR (Master Boot Record) of your other drive. How about booting your Live CD, open a terminal (applications > accessories > terminal) and try the following to install Grub to the correct drive:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
And please post the output of all the above commands. :)

---

### Post by Manillien on 2008-10-27
Hello,

I don't understand why Grub should have been installed to the other hard drive, as this is just the mirror of the first, and I think Ubuntu was installed on the first... I'm not sure, though. Here's the output of the commands:

sudo grub
grub> find /boot/grub/stage1
(hd0,4)

grub> root(hd0,4)

grub> setup(hd0)
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 16 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,4)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

This is what I did before. Still, it only loads the windows startup tool or whatever it's called.

---

### Post by caljohnsmith on 2008-10-27
So are you saying that you have a RAID 1 setup? Unfortunately, that could explain your Grub problems. Please post:
```
sudo fdisk -lu
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
That should help clarify your setup.

---

### Post by Manillien on 2008-10-27
Hmm, I might be saying that:) don't know.

Hmm, shoot. I tried saving the output file in one of my windows folders (internet isn't working in ubuntu yet, so I have to log in and out each time), but now the folder won't open in windows, it's corrupted. That's swell.

Well, as far as I can remember from the fdisk command, first it listed the sda device. It had the windows partition, with a star indicating boot for this partition, and the linux partitions, with no stars on any of them. 

Then, it listed the sdb drive (the mirror drive, I suppose), which contained only a windows partition, with a bootstar also here.

The first of the dd commands gave

GRUB

as output, the second gave

Missing operating system.

I hope you can work with this- if not, I'll write down everything tomorrow, but it's a hassle when I can't copy and paste it!

---

### Post by caljohnsmith on 2008-10-27
OK, your description actually helps quite a bit; your sda drive has Grub correctly installed to the MBR as we would expect from the commands you ran in post #3. And your sdb drive has a Windows MBR, so that is obviously the drive that is being booted on start up. Can you go into your BIOS and make sda first in the boot order? If not, you could install Grub to the MBR of your sdb drive and point it back to your Ubuntu partition on sda for its boot files, but that is not as ideal as changing your BIOS to boot sda first.

---

### Post by Manillien on 2008-10-28
Hi,

I tried entering BIOS setup and changing the boot sequence, but there is only one hard drive, called Intel Volume0, that I can choose. Thus it seems there are two physical disks, but only one RAID1 (I checked) hard drive. So I'm not able to change anything in boot setup...

Edit: I tried doing the other thing you said, but I must have messed up somehow. I did 

sudo grub

root (hd0,4)

setup (hd1)

with the same output as before. Now, when I rebooted, GRUB loaded, at least. But it said

GRUB Hard disk error... 

and I couldn't do anything. I managed to disable the second physical drive in BIOS, which made GRUB load as normal, and I was able to choose between Ubuntu and XP. So it's half solved, but now, my second hard drive is disconnected, which isn't what I want!

---

### Post by caljohnsmith on 2008-10-28
OK, I think we can still get it to work. Try the following:
```
sudo grub
grub> device (hd0) /dev/sdb
grub> device (hd1) /dev/sda
grub> root (hd1,4)
grub> setup (hd0)
grub> quit
```
Reboot, make sure none of your drives are still disabled so that you boot from sdb like before, and let me know what happens.

---

### Post by Manillien on 2008-10-28
Hi,

It works now! I don't know whether it was your suggestion or not, because:

I reenabled the second disk in BIOS, which didn't quite return things to normal - the Intel Matrix Storage Manager said "Rebuild" next to the RAID1 volume now, instead of what it usually says. Anyway, Grub loads successfully, and I try to reboot with the Live CD to do what you told me to. I do, and reboot again, and Grub still works. I want to get rid of that "Rebuild" thing, so I download the newest driver for Intel Matrix Storage Manager, which then starts rebuilding the second physical disk. I rebooted again, and Grub works! I'm writing this from Ubuntu. Thanks!

---

### Post by caljohnsmith on 2008-10-28
Glad it's working, that's what counts. RAID issues can be real bugaboos with Grub sometimes, so I'm glad you got yours working without too much hassle. Cheers and have fun Ubuntu-ing. :)

---


---
title: "Grub Rescue..."
date: 2012-10-12
forum: New to Ubuntu
---

### Post by Vir2ListiX on 2012-10-12
Ok, I had Windows 7 and Ubuntu installed on my Toshiba Satellite P755D.
Ubuntu was my primary partition. That my pc booted to. I never used it, so I wanted that space on it back for windows 7. Well, I f*cked up, and when I deleted the partition, I forgot to make windows the active partition. Now, when I boot my pc it gives me the "Error: no such partition. Grub Rescue" crap. I've tried but can not boot from my windows disc or even my ubuntu disc. I can't seem to even get to my BIOS, or anything. My windows 7 partition should be fine, I just can't figure out how to make it my primary partition. (or whatever the problem is.) So..

1. Stuck at grub rescue.
2. Can't boot from disc, usb, etc
3. Can't access boot menu or BIOS
4. What now?

---

### Post by redaxe90 on 2012-10-12
Do you have access to another machine, where you could connect the harddrive and force the Windows partition to become active??

---

### Post by DuckHook on 2012-10-12
If you cannot get to even your BIOS, then I'm afraid that there is nothing that anyone can do except a computer shop or the manufacturer. Are you sure that this is the case? It isn't often that a messed up partitioning exercise hoses the BIOS, so I suspect that you are just not pressing the escape key to enter BIOS quickly enough. If the BIOS is truly hosed, I suggest a posting on the *Hardware* forum. But even they will have trouble helping you with a system that has really and truly given up the ghost.

If you can access the BIOS, then boot up with your Windows CD and take it from there.

Good luck!

---

### Post by Vir2ListiX on 2012-10-12
> **redaxe90 said:**
> Do you have access to another machine, where you could connect the harddrive and force the Windows partition to become active??

Yes, I'm using my grandmother's desktop. It's a nice computer. How do I go about doing this?

And I'm sure I can't access the BIOS. My friend is pretty good with computers and pc repair, and he can't even get it to. I have no boot up screen. It bypasses everything, and goes straight to the error.

Also, the only thing I'm worried about is getting my data off of the pc. So if there's a way to recover my data, even if the hard drive is gone out, that's fine.

---

### Post by DuckHook on 2012-10-12
You will have to attach your HD to another computer, say, your grandmother's. You will need to use Windows utilities to try and recover your data from there. I'm afraid you will have to ask for further advice from a Windows-users forum, as they will be far more capable to help you at that point.

---

### Post by oldfred on 2012-10-13
It is not just the boot flag or in Windows active partition, but having a Windows boot loader in the MBR.

You need to be able to get into the BIOS. There has to be a way. Then you should be able to boot from a CD or USB flash drive. Or many systems have a one time boot key (f12 on my system) that will let you boot anything that is bootable.

But you have to have a bootable CD, DVD or flash drive. 

You can use this and download into your Ubuntu liveCD or USB or download a full Linux repairCD. That will reinstall a Windows like boot loader and set boot flag on correct partition.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

If your other system is either 32bit or 64bit and your system is the same:

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

### Post by funicorn on 2012-10-13
find a windows7 compact disk, enter administration mode, try to rewrite windows MBR back into your disk.

or just insert a ubuntu livecd or boot from ubuntu lievusb, press 'shift' continuously until you see the boot menu, press 'c', then input following lines
```

grub> insmod ntfs
grub> set root=(hd0, NUMBER)
grub> chainloader +1
grub> boot

```where NUMBER denotes the number of windows7 boot partition. Then use easybcd to write back win7 mbr to the disk.

---

### Post by Vir2ListiX on 2012-10-13
Ok, thanks for the advice everyone. I went ahead and went out and bought a new hard drive. I needed a new one anyways. That's why I didn't need the other one to work, just need the data. In the morning I'm going to try your suggestions. I'll respond as soon as I get the results from these attempts.

---


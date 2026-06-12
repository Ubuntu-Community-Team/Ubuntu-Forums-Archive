---
title: "Upgrade MS XP Home to Pro with Ubuntu on separate drive"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by mdecler2 on 2008-10-04
Hello. I am kind of a newb at upgrading OS's with multiple OS's installed. I would like to upgrade my existing XP Home OS to XP Pro. This MS installation is on a separate hard drive from my Ubuntu installation...but I want to take every precaution to keep Windows from destroying my Hardy install. I am willing to unplug the Ubuntu drive during the upgrade, but I want to make sure I can still get to Ubuntu after the upgrade when I plug her back in. Will GRUB get p0wned during the upgrade? I don't recall where GRUB is installed because Hardy didn't tell me when I installed her.

---

### Post by iansane on 2008-10-04
yeah I'm pretty sure the upgrade will write over grub with ntloader and you'll have to reinstall grub.

There's a lot of helpful docs on grub.

here's one

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

the first 5 steps have worked for me many times.

print it off or write it down before the upgrade so you know how just in case. And it might get complicated with seperate drive but should work.

---

### Post by mdecler2 on 2008-10-04
Scary. Could someone explain the two lines of code below (what the input is and what that line will do)?
```
grub> root (hd0,1)
grub> setup (hd0)
```
Is this overwriting the windows bootloader in these two steps? Or is the next section: "Overwriting the Windows bootloader" also necessary?

---

### Post by okey666 on 2008-10-04
```
grub> root (hd0,1)

```
When you are editing the grub (by using "sudo grub" etc which I presume you know how to do) This line tells the grub where the root partition is. Although Ubuntu might call this sda1, GRUB has a different way of looking at it.
```
(hard drive,partition)
```
You would need to set this up for your system.

The next line is:
```
grub> setup (hd0)
```
This tells grub to set itself up on hard drive "0".

I would think that yes, this would overwrite the windows bootloader, I don't think you can have two on one disc. BUT as you have two discs it is different. Personally (although I have never tried it) I would have thought that this would be done through the bios. Can you not order each drives priority with it?

---

### Post by iansane on 2008-10-04
When you do the step from the link I gave you,

```

find /boot/grub/stage1

```

It gives you the info for the next step (ie. "grub> root (hd0,1)") . This is where grub stage1 is located on your ubuntu installation. Change the "hd0,1" in the next step to what ever the output was from that first step.

Then the part 
```

grub> setup (hd0)

```

uses that information to install grub to hd0 with info about grub in ubuntu which writes over windows loader. Well, something like that.

If all works right, it then is aware of and lists both windows and ubuntu in the boot menu at reboot.

---

### Post by cariboo on 2008-10-04
For more info on grub in a Applications-->Accessories-->Termianl type:

```
man grub
```

For update-grub:

```
man update-grub
```

For grub-install

```
man grub-install
```

Jim

---

### Post by louieb on 2008-10-04
```
root (hd#,#)
```This tell Grub which partition it files such as stage2, menu.lst, device.map ... are located.

```
setup (hd#)
```This tell grub to write some code to the mbr that will load the stage2 program. Grub will look in the partition set by the **root** statement If it finds the stage2 program it will alter the MBR to load it. Its the program stage2 that displays the GRUB menu.

---


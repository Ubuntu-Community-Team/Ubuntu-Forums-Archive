---
title: "installed Ubuntu and now can't access Windows."
date: 2012-09-13
forum: New to Ubuntu
---

### Post by rikimaru90 on 2012-09-13
I installed it using the first option, install along side Windows. And I had 30GB of unallocated space on a separate hard drive than Windows. 

Now when I choose the Windows boot I get something like 'Invalid EFI path.' I still need Windows because my family also use this PC.

EDIT: Here is information from boot info script:
[http://paste.ubuntu.com/1202156/](http://paste.ubuntu.com/1202156/)

---

### Post by Bucky Ball on 2012-09-13
Welcome.

Are you using the 64bit version? With EFI think you need to.

EFI is something I know nothing of so hopefully someone who does can chime in, but I would be looking there. 

If you boot to Ubuntu and launch Gparted, the partition editor, or boot from the LiveCD and run it from there, that will give you a good look at what you have on there and certify Win is still there (should be the NTFS partitions).

Best would be to download and run the Boot Info script:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Post the resulting file back here and that will show everything. 

Generally, you have a maximum of four primary partitions per physical drive. I think if you try and add more with EFI setup things get awkward. Research EFI would be the clue. ;)

---

### Post by rikimaru90 on 2012-09-13
Thank you for replying. Yes I am on 64bit. There seems to be 5 partitions on my drive, one is unknown and I really don't know what it is, but it was there when I installed too.

[http://i.imgur.com/orDnB.png](http://i.imgur.com/orDnB.png)
^This is a screenshot from my gparted.

My windows drive is sdb1 and is still NTFS.

EDIT: Looking at the link you provided now, sorry.

---

### Post by Bucky Ball on 2012-09-13
Yea, that's something to do with the EFI the five partitions. Some are experts on this, not me, but I think it screws up the MBR (master boot record) or something. You could maybe try Boot Repair but not sure if that will work. 

You can boot from a LiveCD, install it there from Software Centre or Synaptics (yes, it will install running from the CD), run it and see if that works. Not sure if it can fix EFI boot probs, but as I say, EFI/partitioning/MBR is where you want to be researching.

Just some thoughts; If Win is on sdb1, a separate drive, where did you install Ubuntu to? sda or sdb, alongside you say? So the five partitions are on sda or sdb?

---

### Post by mips on 2012-09-13
What happens if you select sdb hard drive as you boot device from the bios screen?

---

### Post by rikimaru90 on 2012-09-13
Well here is the results from the boot info script. Sorry but it is beyond me to be honest.
[http://paste.ubuntu.com/1202156/](http://paste.ubuntu.com/1202156/)

---

### Post by mips on 2012-09-13
You can try this [https://help.ubuntu.com/community/UEFIBooting#Chainloading_Windows_x86_64_UEFI-GPT](https://help.ubuntu.com/community/UEFIBooting#Chainloading_Windows_x86_64_UEFI-GPT)

EDIT: Ignore that as you already have a entry for windows in grub.

---

### Post by rikimaru90 on 2012-09-13
See on the unknown partition, do you know what that flag means? 'msftres'?

---

### Post by anewguy on 2012-09-13
Hummmmmm......this wouldn't by chance be on an Intel based MAC would it?

OR.....did you convert the disk to a dynamic disk in Windows?

---

### Post by rikimaru90 on 2012-09-13
Not sure...it's only 128MB, not sure , do you think I should delete it?

---

### Post by rikimaru90 on 2012-09-13
Some people on #ubuntu think maybe the unknown partition was Windows boot, and it's been ruined.  :(

This will be bad...

[http://i.imgur.com/orDnB.png](http://i.imgur.com/orDnB.png)

I just tried boot repair and got this: 'GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.'

---

### Post by YannBuntu on 2012-09-14
Hello

Your Windows is installed in Legacy (not-EFI) mode.
Ubuntu must be installed in the same mode, but [Ubiquity (the Ubuntu installer) is buggy]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1050940") and installed it in EFI mode.

Solution:
1) Via [Gparted]("https://help.ubuntu.com/community/GParted"), delete your EFI partition (sda3). Instead, create a BIOS-Boot partition (1MB, unformatted filesystem, bios_grub flag).
2) Run Boot-Repair's Recommended Repair
3) Indicate the URL that will appear
4) Reboot the PC and tell us what you observe.

See also: [https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_Legacy_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_Legacy_mode)

---


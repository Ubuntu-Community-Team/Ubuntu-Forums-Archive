---
title: "installation/dual booting"
date: 2013-05-06
forum: New to Ubuntu
---

### Post by npagan on 2013-05-06
I have dual booted my laptop a few times before, but now I have encountered a problem.  I'm still fairly new to linux, normally when I put the disk in ubuntu normally ask if I would like to dual boot and it normally will remove the previous linux OS on the laptop.  I downloaded the latest ubuntu, I try to install it and it doesn't offer to remove Zorin for me.  So I figured I would try the manual mode so I'm asking how and where I need to load ubuntu, remove zorin without removing windows, this is the only computer in the house that has windows on it and the wife needs it for some programs from work so I can not delete it or I might get cut off, lol.

[IMG]https://files.one.ubuntu.com/thumbnail/file_storage/OJ6nvHXzTq-i1EbHAyK_Ig:m6FIBbOTRR-N2ZENhWu4dg/1000x1000/[/IMG]
This is how the computer partitioned my laptop, so how can I remove zorin and install ubuntu, any and all help will be very much appreciated.

---

### Post by fantab on 2013-05-06
Boot with your latest Ubuntu CD and "TRY Ubuntu", wait until the Ubuntu desktop is loaded. Find and run "GPARTED" or "DISKS". Find the 'Zorin' partition and choose to format it with ext4.

YOu can also do this from the installer: at the dialog where it ask 'Installation Type' choose something else. On the next dialog choose 'Something Else' and select the 'Zorin' partition and hit "Change". Choose the format option, select filesystem and use "/" mountpoint and say Ok or whatever. Ubuntu will format that partition and install itself.

Do Backup you DATA from that partition before you format it.

---

### Post by npagan on 2013-05-06
Thank you fantab it worked very nicely, currently using ubuntu 13.04 flawlessly, one thing i did noticed when it boots up says KVM disabled in bios. is that needed for anything? other than that things running smoothly. 

Thank you:P

---

### Post by fantab on 2013-05-06
Not really. KVM is needed only if you wish to use Kernel Virtualization. It is not needed otherwise. Details [HERE]("https://en.wikipedia.org/wiki/Kernel-based_Virtual_Machine"). But enabling it in BIOS should take care of the error message. It alright if you ignore it, I think.

---

### Post by npagan on 2013-05-06
Thank you so much, you have been extremely helpful :)

---


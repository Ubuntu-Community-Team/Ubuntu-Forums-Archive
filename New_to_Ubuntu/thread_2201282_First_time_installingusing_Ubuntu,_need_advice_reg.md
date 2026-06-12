---
title: "First time installing/using Ubuntu, need advice regarding partitions..."
date: 2014-01-23
forum: New to Ubuntu
---

### Post by adrian14 on 2014-01-23
Hey everyone,
I'm completely new to Linux in general and I'm finally ready to try it out. I own a asus Ux51vz laptop and was looking to dual boot Ubuntu 12.04 alongside Windows 8, and will be doing so via USB since the laptop does not have a disk drive. I have followed the instructions on creating the USB and have gotten as far as booting my machine into the Ubuntu installation wizard but once I got to the partition step I freaked a little, backed out, and decided to do some more research. So here I am, asking this community for some assistance on what to do.

Here is some info on my system:
Asus Ux51vz
Two SSD drives (C:/, D:/) 128GB each
-Windows OS and programs in C:, files and media in D:
-They are in RAID, no idea what level or what that even means...
-Both have 18GB of free space each, but I can always clear up space 

As far as my plans go, I want to use Ubuntu as my primary coding environment (computer science student) so I really don't need too much hard drive space.  I would also like to be able to share files across operating system. For instance, work on the same program from windows and Ubuntu.

So with that being said, where do I begin, which drive should I install on, how many partitions and how much space each?

Thanks in advance.

---

### Post by oldfred on 2014-01-23
I found these which may have some specific idiosyncrasies for your machine.
[http://ux51vz.blogspot.com/](http://ux51vz.blogspot.com/)
[https://wiki.archlinux.org/index.php/ASUS_Zenbook_UX51Vz](https://wiki.archlinux.org/index.php/ASUS_Zenbook_UX51Vz)

You do need to review UEFI install instructions, but also the Ultrabook or RAID type installs.
And if you have the nVidia chip you will need nomodeset if booting with nVidia or other boot parameters if booting with Intel as dual video.

RAID 0 is not normally recommended, but may be giving you faster speed at the cost of reliability. When one SSD dies you loose all data on both drives.
 Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

See also some of the links on UEFI install issues in the link in my signature.

---

### Post by adrian14 on 2014-01-23
Thanks for the quick response. Looks like I've got my reading list set for the weekend :)

---

### Post by access1denied on 2014-01-23
If you are just testing... why not use an hypervisor and call it a day??  Most people use Virtual Box... or download an use a live CD. Dual booting Windows and Linux... I question why you would put yourself through such misery?

---

### Post by adrian14 on 2014-01-23
I just talked to a classmate who recommended the same thing. I am going to go that route for now, but down the line I was looking to install OpenGazer eye tracking software to be used for a school project and I wasn't sure if it would work properly being run on a virtual machine. BTW, I know nothing about virtual machines either and need to do some more homework :P

---


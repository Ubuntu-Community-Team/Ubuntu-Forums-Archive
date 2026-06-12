---
title: "Confusing page in &quot;Install Ubuntu Desktop&quot; Tutorial"
date: 2019-08-15
forum: New to Ubuntu
---

### Post by andromache2 on 2019-08-15
Hello,
I plan to install Ubuntu Desktop 18.04.3 LTS as a the second OS in a dual boot configuration. 
I will use an ISO loaded onto a USB drive which I made using another great ubuntu tutorial.
However, the installation guide ([https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#5](https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#5))
has a very confusing section (Section #6) shown in the link above.

The directions say:
**6. Allocate drive space**

Use  the checkboxes to choose whether you'd like to install Ubuntu _*alongside  another operating system*_, delete your existing operating system and  replace it with Ubuntu, or &#8212; if you're an advanced user &#8212; choose the 'Something else'
-----
The choices do not seem to mention anything related to a dual boot (i.e. alongside another operation system).
The choices are:
[LIST]
[*]Erase disk.... 
[*]Encrypt the installation... 
[*]Use LVM with the new ubuntu installation... 
[*]Something else 
[/LIST]

Can anyone please tell me which one to use to install ubuntu as a dual boot with Windows 10?
It might be helpful to edit the tutorial to help others who are trying to follow it....

Thank you!

---

### Post by crip720 on 2019-08-15
Unfortunately they decided to show the picture of what you would see if no operating system was on your computer.  If there is a operating system you should see a picture that shows the options you mention under, 6. Allocate drive space.  They do have a note in a box at the bottom about this.  If you do have a operating system and see the picture you mention, then there is a problem.

---

### Post by wildmanne39 on 2019-08-15
*Thread moved to **New to Ubuntu a more appropriate sub-forum**.*, the tag line for the tutorial sub-forum is:
> the place to post your Ubuntu related Tutorials and Howtos. New threads requesting technical support should be posted in an appropriate support sub-forum.


---

### Post by andromache2 on 2019-08-15
Thank you so much **cryp720**! I will report back tomorrow with a screen shot (if I can post an image) to show the full set of options in case someone else has this question!

---

### Post by andromache2 on 2019-08-15
Thank you **Wildmanne39 **for moving my post to a more appropriate forum. I took the forum name too literally. And because of your help, I have the answer I needed to complete the install tomorrow!

---

### Post by andromache2 on 2019-08-16
The ubuntu install did NOT detect that Windows 10 was installed. I had formatted a 2TB drive into a 1TB NTFS partition and free space. When I selected either, I got a error message saying that no file system was found. I selected the free space partition and then said quit and voila, it seems that ubuntu is running out of RAM! This is not what I want to do. More help for this most basic of basic procedures is needed. Help is appreciated.

---

### Post by TheFu on 2019-08-16
Dual booting is hardly a basic procedure.  If you are really new, perhaps running Ubuntu inside a virtual machine for a few months would make more sense? It is much safer to your Windows install and you won't loose the ability to boot Linux when MSFT decides to do something with their boot code. That happens about once a year, I hear.

I stopped dual booting about 10 yrs ago. Too risky.

---

### Post by Impavidus on 2019-08-17
Dual booting is not as easy as it used to be when I first installed Ubuntu in 2006. This is mostly because of some changes introduced in Windows 8. The problem is basically FastStartup. To hide the fact that Windows boots so slowly, it doesn't shutdown completely. Without a clean shutdown, Ubuntu cannot detect Windows and cannot properly configure the bootloader, which is the piece of software that makes dual booting possible. Dual booting is possible, but it's harder than before and a bit fragile.

Furthermore, there's the problem of UEFI and hardware manufacturers not sticking to its standards.

[https://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](https://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)

---

### Post by andromache2 on 2019-08-18
But sometimes you have to be able to dual boot although I am also exploring a VM approach. So far, neither Windows native Hyper-V or Oracle's Virtual Box work very well. Lot's of kludgey hacks seem necessary and even then they do not work except as toys. Long term plan is to install Linux and host VMs with VMware. But for now, dual boot is what I need.

---

### Post by andromache2 on 2019-08-18
Thanks for the link. I will try it out tomorrow to see if it resolves anything.
However, I installed ubuntu on a completely separate SSD and made that the BOOT device in BIOS/UEFI. It is still not starting Linux. So that is very puzzling. 
Something is clearly wrong with the tutorial however since it does not provide complete information for how to set up a system with multiple drives.

---

### Post by richard378 on 2019-08-18
If you are booting from two drives and installed Ubuntu on a second drive.  You have to change the BIOS settings to boot from that drive is likely the error you are finding.  And if you are dual booting you will find clock errors in syncing between your Windows and Ubuntu install.  If you install Kubuntu you won't have this problem but with Ubuntu the problem is the UTC time on Ubuntu thows off your clock on the Windows install.

---

### Post by richard378 on 2019-08-18
I have done Dual boots on both single drive and dual drives and it is different only in choosing the Boot device in BIOS

---

### Post by Dennis N on 2019-08-19
> Can anyone please tell me which one to use to install ubuntu as a dual boot with Windows 10?

Pre-installed W10 is in UEFI Mode, so you should be installing Ubuntu in UEFI mode in order to dual boot with Windows. Some brands of computer require special attention, but I didn't notice the brand you are using mentioned.

Two things you must do:
Installer must boot in UEFI mode to install that way.
Windows Fast Start Up must be turned off or grub will not detect it.

'Install Alongside' and 'Something Else' both can be used to end up with a dual boot. If you prepare the partition to be used for Ubuntu beforehand, use 'Something Else' to select that partition for Ubuntu root partition. You can optionally prepare two partitions beforehand if you intend a separate home partition.

---


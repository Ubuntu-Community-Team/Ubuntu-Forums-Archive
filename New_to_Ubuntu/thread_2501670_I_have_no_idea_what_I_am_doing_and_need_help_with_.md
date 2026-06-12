---
title: "I have no idea what I am doing and need help with a few things."
date: 2024-10-16
forum: New to Ubuntu
---

### Post by shadowtabby on 2024-10-16
Heyo everyone,

Pleawse be kind, I am already overwhelmed with everything already.

I have changed to ubuntu from Windows today, and I have a few things.  

1) I have updated my graphics drivers for my nvidia 2060 super.  But the problem I am having is in the setting for the nvidia panel, it allows me to make my AOC monitor the main monitor, figured that out, but when I go and save to config file because when I reboot it doesn't save it it says "unable to open X config file '/etc/x11/xorg.config'.

I have made sure that ubuntu is updated completed via terminal that much I do know how to do.

2) I cannot get cyberpunk to run.  What do I do?

3) I have steam installed on my main drive but want games to install on a different drive, and I have done that successfully, but when I reboot it says the drive isn't there and I have to repoint it to that drive again, how to I stop that from happening and make sure it stays to the drive like um save it?

3)  How do I get the login screen to stay on my AOC monitor and not my samsung monitor.  One is on DP and the sumsang on HDMI.

4) How do I run an VM on here so I can use microsoft word? 

5) How do I see how much disk space I have on each drive?

---

### Post by TheFu on 2024-10-16
1 question per thread, please.

There are lots of different hypervisors for Linux. Gnome-Boxes, Oracle VirtualBox, KVM/QEMU, and commercial tools.  I use KVM/QEMU, but it is really something that it easy to use without some linux knowledge.  There are others.  In general, people don't use MS-Word on linux. We use LibreOffice and have it read-write docx files.  But if you are working in a collaborative environment, then you NEED the exact same version of MS-Word ... you can use a VM for that, but you may be able to use WINE too, which would have much less overhead if the exact version of MS-Word you need is supported by WINE.

To see storage space on each partition - MS-Windows has been lying to you by using the term "drive" - they are actually partitions with a file system - there are lots of different ways.
**ncdu**, **df -Th**, **lsblk -f**, and I suppose there are GUI programs too. Some file systems that could be installed on Linux will not report the truth to the system tools.

I truly hope you didn't download drivers directly from nvidia. That's a good way to get an unstable system.  Alway use the drivers through the Ubuntu "Additional Drivers" method. NEVER go download files directly from nvidia.

---

### Post by yancek on 2024-10-16
>  but when I reboot it says the drive isn't there and I have to repoint it to that drive again

How do you check to see the drive?  fdisk -l, parted -l, the Disks software or some other method?

Changes to system files must be done using sudo so you have root permissions.  What you are describing, changes not being saved on reboot is expected behavior on a live system, Ubuntu written to a usb.  If you actually booted the usb and installed Ubuntu to one of your drives, you should be able to make changes.

---

### Post by shadowtabby on 2024-10-16
I have Unbuntu acutally installed on my PC and during set up I did put my self as admin and set up logins etc.

---

### Post by shadowtabby on 2024-10-16
> **yancek said:**
> How do you check to see the drive?  fdisk -l, parted -l, the Disks software or some other method?

Changes to system files must be done using sudo so you have root permissions.  What you are describing, changes not being saved on reboot is expected behavior on a live system, Ubuntu written to a usb.  If you actually booted the usb and installed Ubuntu to one of your drives, you should be able to make changes.


I do have ubuntu installed even had to set up logins and I did give my self admin perms.

---

### Post by shadowtabby on 2024-10-16
> **TheFu said:**
> 1 question per thread, please.

There are lots of different hypervisors for Linux. Gnome-Boxes, Oracle VirtualBox, KVM/QEMU, and commercial tools.  I use KVM/QEMU, but it is really something that it easy to use without some linux knowledge.  There are others.  In general, people don't use MS-Word on linux. We use LibreOffice and have it read-write docx files.  But if you are working in a collaborative environment, then you NEED the exact same version of MS-Word ... you can use a VM for that, but you may be able to use WINE too, which would have much less overhead if the exact version of MS-Word you need is supported by WINE.

To see storage space on each partition - MS-Windows has been lying to you by using the term "drive" - they are actually partitions with a file system - there are lots of different ways.
**ncdu**, **df -Th**, **lsblk -f**, and I suppose there are GUI programs too. Some file systems that could be installed on Linux will not report the truth to the system tools.

I truly hope you didn't download drivers directly from nvidia. That's a good way to get an unstable system.  Alway use the drivers through the Ubuntu "Additional Drivers" method. NEVER go download files directly from nvidia.


Thank you for your reply.  

I used the Addistial drivers  in software and updates.  Because of this update I was able to do my monitors at their actual refresh rates and its working better too. I used the tested one.

Can you suggest some GUI ones for me that would be easy to understand or does ubuntu have one?

I got so mad with windows so I did a clean install of ubuntu on my PC, screw windows and their bs, I want to get better on linux and learn more etc.

---

### Post by QIII on 2024-10-16
@shadowtabby --

I have edited your original post.  Please review and read my comment about why I did that.  You might do well to read the "The Forum Rules" link in my signature.

Also, please edit your post to leave only one question.  Please create new threads for each ot the other questions.  As you have it, you will be getting a series of answers in confusing order that will make it difficult for you to keep up and for those who wish to help to keep things straight,  One topic per thread, please.

I suggest leaving the first item in this thread and starting new threads for each of the others.

---

### Post by shadowtabby on 2024-10-17
What was wrong with the first post?  I have done new ones for ones I still need help with now.  Thank you.

---

### Post by TheFu on 2024-10-17
> **shadowtabby said:**
>  I used the Addistial drivers  in software and updates.  Because of this update I was able to do my monitors at their actual refresh rates and its working better too. I used the tested one.
Ok. If you used the "Additional Drivers", that should be the best known drivers.

> **shadowtabby said:**
> Can you suggest some GUI ones for me that would be easy to understand or does ubuntu have one?
Sorry, but no.  I'm a server guy, so don't use GUI stuff too much.  Also, GUIs lie often enough, so I want to limit the chances of getting incorrect information.  Don't fear the shell. That's where 80% of the power of a Unix system can be tapped.  Lots of people get along fine without ever touching their shell, so it isn't mandatory, just more powerful because it works on all systems anywhere in the world.  I manage a few servers on different continents and connect to do my work on those systems without any GUI, just a shell using ssh.  ssh is how Unix systems all connect together and are managed and it has been nearly 30 yrs.

As for a GUI tool for disk stuff.  Gnome-Disks and GParted are the two, but they can be dangerous because they are partition tools.  Open a terminal and run this command:
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```
That will show the file system sizes, types and available.  Don't confuse a "disk" with a "partition" or with a "file system".  They are related, but not the same.  We put files and directories into "file systems." File systems don't have to take an entire partition. There are methods to put 1-50 file systems into a single partition, if that makes sense.  Each file system will be mounted. It works the same on MS-Windows, BTW.  Typically, a file system is mounted as a drive letter in MS-Windows, but it is still a file system, inside a partition, on a drive.  

It might be useful to work through a tutorial about how storage is laid out on Linux, so confusion doesn't lead to data loss.  I say this as someone who remembers deleting everything on an important file system when I was new to Linux.


> **shadowtabby said:**
> I got so mad with windows so I did a clean install of ubuntu on my PC, screw windows and their bs, I want to get better on linux and learn more etc.

I understand completely.  A few times a month, I still have to use MS-Windows and find it very frustrating.  But it is still necessary for me and probably will be for the rest of my life.

---

### Post by shadowtabby on 2024-10-18
Heyo!!

Thank you.  That was a lot of reading but enjoyable.

Do you find that linux is better then windows personally?

---

### Post by TheFu on 2024-10-18
> **shadowtabby said:**
>  
Do you find that linux is better then windows personally?

Better?  That's a personal answer for each of us to determine with different criteria for what "better" means.  Since around 2015, I haven't been able to agree with MSFT's EULA, so I've refused to click "Ok" on any of those from that company.  I felt MSFT had gone too far with their demands in the EULA.  My copy of MS-Windows hasn't been updated since BEFORE that EULA changed.  I know the risks and mitigate those risks by keeping it off any network.

Better?  That's something we each have to decide.  If I thought MS-Windows was better than Linux, wouldn't I use it daily? Since I don't, you have your answer.  

I'm definitely not forced into using Linux.  I am forced into using MS-Windows, however.

---

### Post by shadowtabby on 2024-10-19
Heyo,

Yee fair.  I don't agree with their privacy invasion things,  mainly with recore coming and making it easier for hackers to see what you do just by looking at screenshots.  Forcing local logins to nearly be non exsistant etc.  I don't agree with what microsoft is doing at all.

---


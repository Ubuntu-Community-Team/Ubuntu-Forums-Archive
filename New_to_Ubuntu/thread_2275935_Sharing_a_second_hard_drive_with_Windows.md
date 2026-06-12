---
title: "Sharing a second hard drive with Windows"
date: 2015-04-29
forum: New to Ubuntu
---

### Post by Matthew_Williams on 2015-04-29
Hi all,
Im currently running only on Windows 8.1 , however i am planning on dual booting both windows and ubuntu (only going to keep windows for the one or two games *cough* blizzard games *cough* that will need it for). 
Presently, my windows OS is installed onto a SSD and most of my games and data are on a second HDD . If i dual boot , both will run off the SDD, however i wanted to retain access to the HDD for both windows and linux.

Ive been trawling this forum and couldnt find an answer or previously addressed threat (unless im blind) .

Is there any way to make this possible (such as partitioning the drive) ?
If not, i might consider an exclusive ubuntu computer but that will make things harder for a few games as i mentioned.

Thanks in advance!

PS. dont hurt me, im super new! haha

---

### Post by nerdtron on 2015-04-29
So you are saying that you have 2 physical hard drives, one SSD and one HDD right? and your data is on the HDD?

That is simple enough, dual boot, installing 2 OS on the SSD is possible. And since your HDD is NTFS, you can also access/read/write on it when you are on Linux. No problem with that.

So just install the Ubuntu as dual boot,
1. disconnect the HDD, so that the SSD is the only one detected.
2. Boot ubuntu, then click Install Ubuntu,
3. On the Installation,  choose "install alongside windows" and adjust the hard drive partition allotment for ubuntu.
4. finish the installation and reboot just to make sure BOTH OS are bootable.
5. Now it is safe to connect the HDD. You will be able to access it on both OS.

---

### Post by Matthew_Williams on 2015-04-29
ah brilliant! easy enough. i was concerned as I had seen comments on websites about ubuntu only being able to read NTFS, not write to it. I was running ubuntu off a usb and it could see the hard drive but threw up an error when i clicked in it.

thanks for the assistance!

---

### Post by Mark Phelps on 2015-04-29
You should NOT write to the Windows OS partition from Ubuntu.  Doing so can easily corrupt the Windows OS partition, rendering Windows unbootable and making it very hard to fix.

As to sharing the Windows data partition, you have to first disable FastStartup in Win8.  This prevents Win8 from going into hibernation when you exit is.  Also, be shure to use ShutDown when exiting Win8, as using Restart will cause Win8 to remain in hibernation.

---

### Post by nerdtron on 2015-04-29
> **Matthew_Williams said:**
> ah brilliant! easy enough. i was concerned as I had seen comments on websites about ubuntu only being able to read NTFS, not write to it. I was running ubuntu off a usb and it could see the hard drive but threw up an error when i clicked in it.

thanks for the assistance!

What is the error?

And also is this computer a laptop or desktop? Computer specs/model? Also, the comment above of Mark_Phelps offered good advise for windows 8 computers.

---

### Post by garyed on 2015-04-29
> **Mark Phelps said:**
> You should NOT write to the Windows OS partition from Ubuntu.  Doing so can easily corrupt the Windows OS partition, rendering Windows unbootable and making it very hard to fix.

As to sharing the Windows data partition, you have to first disable FastStartup in Win8.  This prevents Win8 from going into hibernation when you exit is.  Also, be shure to use ShutDown when exiting Win8, as using Restart will cause Win8 to remain in hibernation.

I never heard that one before, can you elaborate a little more. I back up files from Ubuntu to my Windows OS drive plenty without ever having a problem that I know of. Have I just been lucky? Am I playing with fire?

---

### Post by Mark Phelps on 2015-04-29
> Have I just been lucky? Am I playing with fire? Yes ... you have been lucky.

NTFS is sensitive to changes from outside -- even from other Windows OSs.  You can read/write a data partition all you want (since it doesn't boot), but messing around with an OS partition is risking filesystem corruption.

---

### Post by garyed on 2015-04-29
> **Mark Phelps said:**
> Yes ... you have been lucky.

NTFS is sensitive to changes from outside -- even from other Windows OSs.  You can read/write a data partition all you want (since it doesn't boot), but messing around with an OS partition is risking filesystem corruption.

I don't understand the difference but I'll take your word for it & be more careful til I find out more info.

---


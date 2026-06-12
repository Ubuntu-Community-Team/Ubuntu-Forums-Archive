---
title: "Sun xVM VirtualBox"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by bbright20 on 2008-11-27
First off, I am running a dual boot XP/Ubuntu system and I am trying set up XP to run inside virtualbox. I have downloaded and installed Sun xVM VirtualBox and don't really know where to go from there. Any suggestions?

---

### Post by HereInOz on 2008-11-27
If you have properly installed VirtualBox, you should find it in the menus somewhere, and run it from there.  You will then be able to create a virtual disk for your Windows XP install. 

Once you have created the virtual disk, you can then, making sure that the CD drive is mounted in the virtual machine, boot up the virtual machine from within VirtualBox, and it will run you through the install of Windows XP.

---

### Post by anewguy on 2008-11-27
Another point would be to be sure you downloaded the PUEL closed source but free version, not the open source free version.  Why?  The PUEL closed source free version allows you to use USB devices in the VirtualBox guest OS (in your case, Windows XP).  If you didn't just remove what you have, download the PUEL version and reinstall.

As mentioned in the post above, running it is quite easy - just open VirtualBox and a "console" will come up.  From there, you can create a new Virtual Machine, giving a type of Windows XP.  Then put your XP installation CD in the CD drive and start the virtual machine - it should come up with the Windows XP installation - just follow it as normal and it will install XP in the vm as the guest OS.

Dave :)

---

### Post by nakama85 on 2008-11-27
It sound to me like your trying to run your current xp install through vbox.
Just to let you know this is not possible as far as I know. Someone can correct me if I am wrong

---

### Post by benhur99ph on 2008-11-27
This might be of some help to you --> [Boot an existing XP (Physical HDD) install inside VirtualBox]("http://ubuntuforums.org/showthread.php?t=769883").

The guide is pretty in-depth and should answer most of your questions.

---

### Post by Dedoimedo on 2008-11-27
> **benhur99ph said:**
> This might be of some help to you --> [Boot an existing XP (Physical HDD) install inside VirtualBox]("http://ubuntuforums.org/showthread.php?t=769883").

The guide is pretty in-depth and should answer most of your questions.

Hello,

I strongly recommend AGAINST running physical partitions (raw disk access), especially for new users. This can lead to serious data corruption.

At the very least, the user should get comfortable working with virtual disks before testing physical access.

Dedoimedo

---

### Post by benhur99ph on 2008-11-27
> **Dedoimedo said:**
> Hello,

I strongly recommend AGAINST running physical partitions (raw disk access), especially for new users. This can lead to serious data corruption.

At the very least, the user should get comfortable working with virtual disks before testing physical access.

Dedoimedo

Yes. I agree. Sorry I didn't warn you earlier but this is for the more experienced users.

---

### Post by bbright20 on 2008-11-28
Thanks for all the help guys!

---

### Post by anewguy on 2008-11-29
As a user who has tried both, I can ditto what has already been said:  it can be risky to run an existing Windows installation with virtualbox - it can be done, but is not recommended.  The info for doing so is right in the help under advanced and vboxmanage.  However, if you have your Windows installation disk, you will be better served to create a virtual disk and load Windows to it.

Dave :)

---


---
title: "[SOLVED] Mount an external USB harddrive"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by phread59 on 2008-05-18
I have 2 external hard drives.  Both are Maxtor OneTouch4's.  One was used with a Windows system and mounts and detects just fine.  I recently bought another cheap.  It is new and never been used.  I hooked it up and cannot get it mounted in Linux.  It comes back with an error like "unable to mount, Windows incomplete shutdown. Cannot mount NTFS in use"

I tried a forced mount and just cannot find the right command to mount it up.  I have disconnected the good drive just in case.  Any suggestions on how to mount this puppy to use it in Linux.  I don't want to have to go back to Windows to play with it.  I believe because it is formatted for NTFS it may not mount up.  I do know there is Windows specific back-up software in there.  This may be causing the error.  Any help would be appreciated.

Mark Shuman

---

### Post by nhasian on 2008-05-18
I've seen that error before with an internal NTFS drive that refused to mount in linux because it was shut down abruptly.  i had to use the -force option to mount it and that reset some flags that allowed it to automount next time.

if the force option doesnt work for you, you could try plugging it into a windows machine and then safely remove the usb device to reset the flags.  But if you dont want to use windows then you could always format it right?  its probably in FAT32 anyway :)

---

### Post by phread59 on 2008-05-20
OK, I went and reinitialized my Windows installation.  I then went in and initialized and mounted the drive.  I now can get it to auto maount just fine.  How do I go about renaming the drive?  I have 2 one touch 4's.  That's how they show on my desktop.  Any suggestions on how to rename one?

Mark Shuman

---

### Post by walking_mushrooms on 2008-05-23
Same problem except I can't get into Windows and "Safely Remove" because my Windows unfortunately has a virus, not allowing me to even get to the logon menu, which is the reason I currently have ubuntu.  Any suggestions?

---

### Post by bumanie on 2008-05-23
> **walking_mushrooms said:**
> Same problem except I can't get into Windows and "Safely Remove" because my Windows unfortunately has a virus, not allowing me to even get to the logon menu, which is the reason I currently have ubuntu.  Any suggestions?

Does your device get a /dev/sda, /dev/sdb or dev/sdc etc. assigned to it? If so try > sudo ntfsfix /dev/sdx,x That should reset the filesystem on your usb device as long as you know which device name to assign it to.

---

### Post by phread59 on 2008-05-24
Couldn't change the name.  I just added a file named Linux in the second.  I will add one for Windows too.  That way I can just save to the file I need.  I will add a 1 &2 files to differentiate the 2 drives.  This will get me where I want to go.

Mark Shuman

---


---
title: "To mount or unmount, that is the question?"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Jamface on 2008-07-01
What does 'mount' and 'unmount' mean in Linux-speak? 
What is the computer/software doing when it does it?  Why?
When  do I need to do it as a user? Why?
When is it done automatically, i.e. without user action, if at all? Why?
More generally, is there a Linux-Ubuntu dictionary which explains these terms for Absolute Beginners, rather than the do this do that guides which explain very little?

---

### Post by kuja on 2008-07-01
You might find this page helpful: [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

Mount as a user whenever possible ... simply because it's more convenient. 
If it's done without user action, then that probably means hal (hardware abstraction layer) did it, and that again is for your convenience.

---

### Post by bab1 on 2008-07-01
> **Jamface said:**
> What does 'mount' and 'unmount' mean in Linux-speak? 
What is the computer/software doing when it does it?  Why?
  to mount a drive is to make it available to the system and users
  To unmount is to remove it from availablity
When  do I need to do it as a user? Why?
  When you stick a CD in the drive the system needs to mount it to be able to read it.
When is it done automatically, i.e. without user action, if at all? Why?
  Most of the time and through the /etc/fstab file
More generally, is there a Linux-Ubuntu dictionary which explains these terms for Absolute Beginners, rather than the do this do that guides which explain very little?

Get a basic book on Linux for the commands or look on the internet for unix/linux commands.  After you know what the commands are you can use the terminal on your system to look at the online manual.

It's available from the command line as: "man whatevercommand" 





see above

---

### Post by hyper_ch on 2008-07-01
mount --> binding a device into the local filesystem.

Linux starts all filesystem as "/" (root). From this path you can add more devices. E.g. you can mount a cd-rom as "/cdrom" or "/cd-rom". You can have the "home" folder on a complete different harddisk or even on a networked storage devices. You can mount your usb pendrive as /home/USER/Desktop/USB

umount is releasing the devices from the filesystem.

---

### Post by forger on 2008-07-01
Mount/unmount is like when you "Safely disconnect" your usb flash drives through Windows, you "safely disconnect" the drive, which you can then use to partition and/or check for problems :) Which is also one example of why using unmount.

You need it when you want to say mount a drive **when you want** to mount it, when you want to make it available, and not to be loaded at all times. That's one example.

A few manuals to get you started:
from menu Applications > Accessories > Terminal, execute:
> man mount
man umount
man fstab


Scroll with arrow keys (or space, page up, page down) and press "q" to quit

edit: see the post #2 :P

---

### Post by lisati on 2008-07-01
"Mount" means getting the computer system to recognize a disk/tape/some physical gadget, and "unmount" means to tell the computer that you've finished with it and want to remove it from the system.

Automatic mounting can be a good thing, but you need to be careful about removing something from the system without the "unmount" - as with the Windows equiavalent "safely remove hardware" you need to make sure that there's nothing waiting to be written to something you've hooked up before you pull the plug, otherwise you could end up with scrambled or missing data.

---

### Post by iaculallad on 2008-07-01
Mount and Umount had been explained above:

You can mount devices automatically by configuring your /etc/fstab file.

For the Ubuntu-Dictionary thing: Simply drop to your terminal and issue the man command.

```
i.e: man umount
     man mount
```

This will give you a very concise explanation about the command and the options you can use with the command.> 

---


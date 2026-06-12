---
title: "install ubuntu from usb into virtual box"
date: 2014-01-18
forum: New to Ubuntu
---

### Post by gscratch2 on 2014-01-18
I apologize if this has been answered; a quick search didn't find it.

I am running Windows8.  I have installed VirtualBox.  I want to install Ubuntu on a virtual machine.  The machine has no CD, so I want to install from USB. I have created a bootable USB using Startup Disk Creator.  the ISO is Saucy, but the created USB has no .ISO files on it (I assume this is OK). When I start the virtual machine, USB is not a choice in "boot order".

thanks in advance for help,

Glen

---

### Post by howefield on 2014-01-18
Why don't you create the VM using the iso file, no need to create a USB disk.

---

### Post by gscratch2 on 2014-01-18
Thanks for the quick reply.   I actually thought of trying that - how do I tell the virtual machine to find the .ISO  ?  I don't see "ISO" as a boot medium

pardon my ignorance

---

### Post by deadflowr on 2014-01-18
+1 to what howefield stated.
You can run virtualbox installs by selecting a virtual disk file.
Just go to settings > storage and where you select the disk choose a file and then it's up to you to find the file in your system.
(ie, usually in the downloads folder)

---

### Post by gscratch2 on 2014-01-18
Excellent, using the ISO directly worked.  thanks.  It took me a minute to realize I had to select a controller and connect the "hard disk" (the ISO) to it.

Now, I have a new issue: I have 64b Windows8 so I used the "server-amd64"  However, the installer says I need the "i686" version of the ISO. I don't find a "i686" ISO on the Ubuntu download 

My machine says the CPU is Intel Core i7-3667TU  and "x64-based processor"

I have found some information here:  [http://askubuntu.com/questions/308937/cannot-install-ubuntu-in-virtualbox-due-to-this-kernel-requires-an-x86-64-cpu](http://askubuntu.com/questions/308937/cannot-install-ubuntu-in-virtualbox-due-to-this-kernel-requires-an-x86-64-cpu)


thanks,

---

### Post by deadflowr on 2014-01-18
i686 is 32-bit.
When you go to the download page, where you select which Ubuntu you want,(I assume you'll be downloading from ubuntu's main site) change the version from 64-bit to 32-bit.

Beats me, though, as to why it wants the 32-bit version if the machine can handle 64-bit.

---

### Post by gscratch2 on 2014-01-21
just so this is posted: once I enabled virtualization in the BIOS I was able to create a vm using the 64-bit Ubuntu server .ISO

thanks for the help

Glen

---


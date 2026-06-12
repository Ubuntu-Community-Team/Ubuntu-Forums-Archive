---
title: "Installing Ubuntu from Local HD to another HD"
date: 2009-02-09
forum: Other OS Talk
---

### Post by Dannamoth on 2009-02-09
I currently have a Vista/Ubuntu Desktop machine that I use for my work. I also have a three year old Dell inspiron laptop that died on me (XP boot files corrupted after it losing power shutting down).

I recovered the data that I need from the HD, pictures ect by plugging it into my desktop. 

I'm trying to figure out a way to install Ubuntu onto the laptops HD while connected to the desktop. 

I don't have the option to burn a disc because I don't currently have a cd/dvd burner on my desktop (soon).

any options?

---

### Post by cyfur01 on 2009-02-09
You can create a Live USB stick if the Laptop will support booting from a USB Key.

In Ubuntu 8.10, you can run System->Administration->Create a USB startup disk, and use this to copy the files from a Ubuntu iso file onto the USB key. I found when I did this that I then had to run "install-mbr /dev/sdX" where sdX is the USB key's device name, which rewrites the master boot record.

---

### Post by Dannamoth on 2009-02-09
ok, I'll go fiddle around with this, room mate is letting me borrow his 2 gig usb drive.

---


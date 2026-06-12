---
title: "Primary Partition is mounting and appearing on desktop."
date: 2008-05-13
forum: New to Ubuntu
---

### Post by ejpyle on 2008-05-13
Well not sure what I did wrong though I had to reboot my PC and when I did I got the message the selected partition could not be found...

I changed the entry that it was pointing to to the partition that had Ubuntu on it. it was (hd0,0) I changed it from (hd1,0)

So once it booted up I edited the /boot/grub/menu.lst and changed the entry in there as well.

Now after rebooting I get the mounted drive icons on my desktop from my other drives connected as well as **_[COLOR="Red"]the primary partition that Ubuntu is running on!!!!!!![/COLOR]_**. Why would this happen? Is there a risk because Ubuntu is mounting the partition that it is booted into? 

Just want to make sure I don't need to back up anything because it might be lost.

---

### Post by shinobitux on 2008-05-13
First thing...**don't panic**.
Ubuntu mounting your partitions is not necessarily a bad thing.

First could you post the command line output for the "mount" command and the output for "dd if=/etc/fstab" and "dd if=/etc/mtab"

If it prompts you to use sudo I've made a mistake in my commands so let me know.

Also, do you dual boot your computer?

---


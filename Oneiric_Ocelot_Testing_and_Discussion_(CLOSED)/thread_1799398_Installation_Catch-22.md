---
title: "Installation Catch-22"
date: 2011-07-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ratcheer on 2011-07-07
I cannot get a complete installation of Oneiric AMD64. The same thing occurred with Natty on this PC. It fails to correctly detect the network hardware and/or installs the wrong driver. Then, when the installer gets to the step "Select and Install Software", the installation fails because it cannot connect to the Internet.

If I can't get a bootable installation, I cannot fix the NIC driver. If I cannot fix the NIC driver, I cannot get a bootable installation. It is Catch-22.

Does anyone have any idea how to get around this?

Thanks,
Tim

---

### Post by cariboo on 2011-07-07
I've used the Live CD to install sucessfully without a working network connection, is there a reason why you're using the alternate install iso, instead of the desktop iso?

---

### Post by ratcheer on 2011-07-07
No particular reason, the alternate image just goes right to the installation, so I usually prefer it. Maybe that is how I got around the problem with Natty - I attempted installing so many times I really can't remember what worked in the end.

Thanks, I'll download the LiveCD and try again.

Tim

---

### Post by ratcheer on 2011-07-07
Well, installation ran to completion from the LiveCD, but I got uppity and tried installing it to btrfs, again. When I tried to boot the new installation, I got the old "sparse file error". Hasn't that been fixed, yet?

I thought some people said you could hit Enter and it would go ahead and boot after that, but mine does not. I just have an interminable flashing cursor on a black screen. If anyone can tell me how to continue, I would appreciate it. Or I guess I just need to install again to ext4.

Tim

---

### Post by ratcheer on 2011-07-08
Installing from LiveCD to ext4 filesystem worked. I'm marking this thread as SOLVED.

Now, I am having trouble creating both the NIC driver and the wireless PCI card driver in Oneiric. I'm using the same driver sources I used for Natty, but neither is resulting in a driver that the kernel will load. I will start new thread(s) on that, though.

Tim

---


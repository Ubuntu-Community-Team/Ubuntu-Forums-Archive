---
title: "reinstalling Windows"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by Joe Skillman on 2012-04-26
After installing Ubuntu I've decided that I want to reinstall Windows before reinstalling Ubuntu with both operating systems. How can I reformat the hard drive so that I can reinstall Windows?

---

### Post by papibe on 2012-04-26
Hi Joe Skillman. Welcome to the forums.

You can use the same CD/USB Ubuntu installer, but instead of installing Ubuntu, choose 'Try Ubuntu'.

When you get to the desktop environment, run 'gparted'. There you can delete all partitions and reformat your HD.

I don't know if that's really necessary since, at least in my experience, you are presented with the option to reformat the drive when installing Windows.

Hope that helps,
Regards.

---

### Post by CLCressman on 2012-04-26
If you can boot ubuntu from a cd or usb device, you can use gparted to edit your partitions. If you are planning to install ubuntu on its own partition, set that up at same time. If you want more specific instructions, I would be glad to help.
Oops, I was a little too slow.

---

### Post by Joe Skillman on 2012-04-26
Thanks for the help. My Windows 7 disc does not appear to give me that option, although the online documentation says it should.

---

### Post by Mark Phelps on 2012-04-27
> **Joe Skillman said:**
> Thanks for the help. My Windows 7 disc does not appear to give me that option, although the online documentation says it should.

What "option"??

Win7 can NOT be installed to a hard drive that is filled with Linux filesystem partitions -- as it does not understand that filesystem.

You will either have to remove the Linux filesystem partitions (which is really not needed), or shrink the partitions (from a LiveCD) to leave room for the Win7 installer.

If you choose the second approach, do NOT format the unallocated space -- let the Windows installer do that.

---


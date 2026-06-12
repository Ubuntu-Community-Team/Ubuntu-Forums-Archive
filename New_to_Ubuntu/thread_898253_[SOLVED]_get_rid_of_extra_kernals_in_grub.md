---
title: "[SOLVED] get rid of extra kernals in grub"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by soloman498 on 2008-08-23
could someoone assist me in how to get rid of excess kernals in grub menu (dual booted system)

---

### Post by eightmillion on 2008-08-23
You should be able to remove them from synaptic and it will take care of your grub menu also. Just search installed packages for 'kernel'. I recommend keeping at least one extra kernel in case you run into problems in the future.

---

### Post by livestockPimp on 2008-08-23
if you only need to remove the entries to make the boot list smaller you can just edit the /boot/grub/menu.1st and remove any entries you do not want to see on boot.

---

### Post by alienexplorers on 2008-08-23
I just leave the extra kernels loaded in synaptic and just delete them from the /boot/grub/menu.lst file.  This way if I nee to go back to a lower kernel they are already loaded.

---

### Post by mcduck on 2008-08-23
> **alienexplorers said:**
> I just leave the extra kernels loaded in synaptic and just delete them from the /boot/grub/menu.lst file.  This way if I nee to go back to a lower kernel they are already loaded.

..and you have to access them using Grub command line, since they are not in the menu. Not to mention how unlikely it would be that you would ever _really_ need to boot a kernel 3 versions old.. ;)

No, I'd say uninstall them, and if you really feel you might for some reason some day need an older kernel, then keep one. No reason to keep them _all_.

I can't really even imagine why (or how) the kernel would suddenly break and force me to use older one instead. Keeping the old one for a while to make sure the new version works fine is a different thing, of course. Personally, I uninstall old kernel versions day or two after updating to new one.

---

### Post by alienexplorers on 2008-08-23
I'm on kernel 21 so I have 18,19,and 20 still listed this way if I have a problem with 21 I can always just add back in to grub 19 or 20.

---

### Post by mcduck on 2008-08-23
> **alienexplorers said:**
> I'm on kernel 21 so I have 18,19,and 20 still listed this way if I have a problem with 21 I can always just add back in to grub 19 or 20.

Yeah, but why wiuld you need to go back to 18 or 19, if you also have 20 that works just as fine? And, honestly, how often have you neded to do even that _after_ you have tested the latest kernel for a while and found no problems? How bad luck would you need to have to find out that suddenly not only the latest kernel, but also 2 previous versions, have stopped working on your machine, forcing you to use even older one?

Like I said, even in worst cases you would only need one older kernel available, not every single version you have used since the release.

Really, many kernels together with their modules & headers can take several gigabytes of disk space. I can understand the wasted space for one fallback kernel, but not for more than that. Not even when you have terabytes worth of disk space. Keeping more than one old kernels is still just wasting the space with no actual benefits.

---

### Post by soloman498 on 2008-08-23
I went to synaptic but couldn't find a list of the kernals.when I go to /boot/grub/menu.lst file and try to change it it tells me that root is the owner and I can't change it.how do I get permission to change it?

---

### Post by mcduck on 2008-08-23
Click the search-button & searh for "kernel" in package name & description.

The kernel packages are called "linux-image", "linux-headers" and "linux-resticted-modules". Find the old versions, right-click & select "mark for complete removal". When done, click "Apply".


For the grub editing problem, the file is owned by the root user and you can't edit it like you would edit your personal files. You should probably read this: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

In short, run "gksudo gedit /boot/grub/menu.lst" topen the file for editing as root. Or run "gksudo nautilus" to open the file manager as root, which allows you to easily open any files with root privileges. Of course you should be very careful with these, as they allow you to do _anything_ on your system, including breaking it beyond all repair..

---

### Post by soloman498 on 2008-08-23
thankyou mcduck. synaptic said they weren't loaded.gksudo gedit seemed to work.

---


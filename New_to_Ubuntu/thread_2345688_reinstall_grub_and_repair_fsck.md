---
title: "reinstall grub and repair fsck"
date: 2016-12-06
forum: New to Ubuntu
---

### Post by metaphizix on 2016-12-06
Hi

i was trying to repair my fsck/initramfs ended up damaging grub in the process, I would like to know if i reinstall grub does it fix the fsck problem?
I am also having problems reinstalling/repairing grub .
Please see this link for more information.

[http://paste.ubuntu.com/23565360/](http://paste.ubuntu.com/23565360/)

Thank you

---

### Post by DuckHook on 2016-12-07
Welcome to the forums, metaphizix

Your posting is cryptic, incomplete and very hard to understand. What do you mean by:> **metaphizix said:**
> …i was trying to repair my fsck/initramfs…fsck is not used to repair initramfs. It repairs the whole filesystem. Or were you trying to repair the fsck app itself?> …if i reinstall grub does it fix the fsck problem?What is "the fsck problem?" Why did you need to use it? Is fsck broken or missing? What is the background and history? Without proper info, all anyone can do is blindly throw darts in the dark.> I am also having problems reinstalling/repairing grubDescribe the problems. Why did you need to do this? Describe the processes you tried. Post the error messages.

We appreciate the pastebin data, but it doesn't go very far without some effort on your part to tell your story. Please see the link in my sig: *How to Ask for Help*

---

### Post by yancek on 2016-12-07
You have mixed an MBR install with an EFI install.  If you want MBR, you install some Grub boot code to the MBR (which you have) and if you want an EFI install you do NOT install Grub code to the MBR.  If you look, you can see that you do have an EFI partition with the Ubuntu EFI files.  Not sure what your fsck problem is?  If this is a new install, I would suggest re-installing and deciding in advance which method you want.  You are also using LVM which adds another layer of complexity to the situation.  Never used LVM myself so don't have any suggestions on that.  Posting more details as suggested would be a good first step.

---

### Post by oldfred on 2016-12-07
While your ESP - efi system partition is a larger size, your /boot partition looks tiny.
Do not know much about LVM, other than many threads complaining about small /boot partitions of 230MB as used by default install, yours is 1 MB  or 1003KB or more the size of  a bios_grub partition.

---


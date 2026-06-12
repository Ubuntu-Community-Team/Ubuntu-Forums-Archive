---
title: "Install DOES NOT allow drive selection"
date: 2020-05-07
forum: New to Ubuntu
---

### Post by altondavis on 2020-05-07
Bootable usb stick with latest ubuntu. Booted and tested.... ran well. 

I have Hewlett-Packard PACKARD pc with qty 2 internal drives.  While in testing I selected to l&#8221;INSTALL&#8221;.  It DID NOT give me hard drive selection option.

i want to keep windows 7 on C:/ drive.  I need to install on &#8220;&#8221;D:/&#8220;&#8221; drive.

plz advise

---

### Post by oldrocker99 on 2020-05-08
You should choose "Something Else," and not use the "Install" selection.

You probably will have to use the top buttons to select the drive you want to install Linux on, but make sure that it writes the boot sector to the Windows drive, or you won't be able to boot Ubuntu at all.

---

### Post by ActionParsnip on 2020-05-08
If the D: is for Ubuntu then remove the partition (this will destroy any data on it). When you boot to the Ubuntu install media it will offer to usethe free space

---

### Post by yancek on 2020-05-08
You need to follow the advice in post 3 or simply format what you refer to as the D partition to a Linux filesystem as Linux will not work on a windows filesystem.  Either method destroys all data on the partition (D) and windows does not assign drive letters to partitions which do not have windows filesystems.

---

### Post by Impavidus on 2020-05-08
You can install Ubuntu on the D partition, except that after install it will no longer be known as the D partition. All data there will be wiped. You can just as well delete the partition beforehand in Windows, then the installer should offer to install alongside Windows, using the now unallocated space where the D partition used to be. For more control, or if something doesn't work right, you can use the "something else" option, which allows for manual partitioning. With multiple hard drives, it's usually better to partition manually.

Is your Windows installed in UEFI mode or legacy mode (is there an EFI partition)? If using Windows 8 or later, have you disabled FastStartup? Can Ubuntu see the harddrive at all? That's a fairly common issue these days, but easily solved (usually).

---


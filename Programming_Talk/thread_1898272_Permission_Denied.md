---
title: "Permission Denied?"
date: 2011-12-21
forum: Programming Talk
---

### Post by burhangondal on 2011-12-21
Hello guys/guls,

I am trying to use codeblock to program for my C++ class but the problem is that everytime i try to build and run, i get a permission denied error in terminal:confused:..... i know  i know i need to save my stuff in home folder but i cant do that cuz i am directly trying to run it from my usb stick which i carry to skol and my all data is saved on the USB. I NEED to run everything from the usb. Any one cud help me solve this problem? is there a problem with USB not mounting with root permission? or that is just how FSTAB handles it? 

Its not only the codeblock, its the problem with codelite too and netbeans too. Seems like a minor problem with ubuntu which i donno about?

Help would be much appreciated cuz i dont wanna use VISUAL BASIC its so slow to compile and run compare to codeblock or codelite....and yes i m a first year comp sci student still learning :)

Thanks in Advance eh

---

### Post by amingv on 2011-12-21
You are getting permission denied because, since a few versions ago, Ubuntu mounts NTFS/FAT drives without exec permissions by default; you can do a few things about this:

1. Remount the drive with exec permissions.
2. Create an entry for the drive in fstab and grant it exec permissions there (this way it will have the appropiate permissions whenever it is mounted)
3. If the drive is large enough, create an additional ext2/3/4 partition, then configure your IDE to save binaries there.

---


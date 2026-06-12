---
title: "Windows 7 User folders empty"
date: 2012-03-17
forum: New to Ubuntu
---

### Post by MittyG on 2012-03-17
Hi people,

I have a Sony Vaio laptop that recently encountered an error resulting in UNMOUNTABLE_BOOT_VOLUME BSOD in Windows 7, so I turned to xubuntu, booting it from a USB pen drive and using a non-persistent installation.

My aim was to recover all of the files from the broken hard drive and re-install windows from scratch so I used ddrescue to create an image of the damaged partition and upon mounting the image I can successfully browse the files in their original Windows structure.

However, when browsing the directory Users\[USERNAME]\Documents, I find an empty folder. This is made even more strange by the fact that I can successfully view the Users/[USERNAME]\Downloads folder, the contents of which are intact and have now been backed up.

I also used testdisk to browse the Users\[USERNAME]\Documents directory and it to, fails to find anything inside.

Can anyone help me out?

---

### Post by Mark Phelps on 2012-03-17
No disrespect intended .. but this is NOT the Windows 7 forum; this is the Ubuntu forums.

Win7 filesystem uses soft links for LOTS of its directories -- which is why they appear to be empty.

Suggest you take the problem to a Win7 forum: sevenforums.com

---


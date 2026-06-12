---
title: "filesystem size"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by Ace88 on 2008-09-23
My question stems from this: I installed Ubuntu on one of the empty hard drives (250 GB, ntfs) on my computer and the filesystem size is only about 5 gigabytes (it says there is 1.7 gigs free). Then, there is a folder in the filesystem called "boot" which is huge (about 225 gigabytes) and aside from the GRUB program which is located in there, it is empty. 

Is it normal to have a filesystem that is so small? Is there a way to expand the filesystem so there is more than 1.7 gigs free? I ask b/c all of the document folders, desktop, music, etc folders are located on the filesystem and for such a broad range of files there is so little space for them. Should I move them to the boot folder? Any recommendations?

---

### Post by phidia on 2008-09-23
A boot directory that has 225GB? How did you determine these sizes and which version of Ubuntu are you using?

---

### Post by Sef on 2008-09-23
> My question stems from this: I installed Ubuntu on one of the empty hard drives (250 GB, ntfs) on my computer and the filesystem size is only about 5 gigabytes (it says there is 1.7 gigs free). Then, there is a folder in the filesystem called "boot" which is huge (about 225 gigabytes) and aside from the GRUB program which is located in there, it is empty. 

Is it normal to have a filesystem that is so small? Is there a way to expand the filesystem so there is more than 1.7 gigs free? I ask b/c all of the document folders, desktop, music, etc folders are located on the filesystem and for such a broad range of files there is so little space for them. Should I move them to the boot folder? Any recommendations?

If your boot sector is 225 GB, then something went wrong with the install.   The boot sector should be only about 50 mb.

---

### Post by Ace88 on 2008-09-23
Ok, first off I have winxp installed on my central hd ("C"). I used the cd for ubuntu 8.04 and opted to install inside windows choosing one of my empty hard drives ("D" Drive, formatted ntfs)...it just kind of installed by itself ( just asked me how big I wanted the install, username, etc) and told me to restart and I thought I was good to go...guess not. I haven't put anything of significance on here so starting from scratch again won't be an issue. 

What would be my next step here?

---

### Post by Ace88 on 2008-09-23
So should I just try to re-install....anyone?

---


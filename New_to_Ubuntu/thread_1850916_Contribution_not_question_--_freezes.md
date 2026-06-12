---
title: "Contribution not question -- freezes"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by jk121960 on 2011-09-27
I am relatively new to linux and at last I think I have something to contribute. IN the current builds 'Natty' based, I have been plagued with freezing, I ran accross the 'gtk-window-decorator --replace' fix which did help in some instances. I also ran across a post for this error, [https://answers.launchpad.net/ubuntu/+s](https://answers.launchpad.net/ubuntu/+s) ... ion/148757, I started to notice a connection. For those of you who have multiboot or reinstall etc. Whether because the installer doesn't ask or you don't notice, and your shared 'swap' and 'tmp' get refomatted. The fstab reference to these is no loner any good because the UUID gets regenerated and changed, this can cause the error in the above post and also desktop freezes. I also noticed in Suse that they use /dev/disk/by-id references in thee fstab. This will stop that problem indicating swap and tmp etc. by the exact disk and partition and wont change when formatted. It looks like this '/dev/disk/by-id/scsi-SATA_WDC_WD2002FAEX-_WD-WMAY01454091-part5 /tmp ext4 defaults 0 2' this combined with adding the 'gtk-window-decorator --replace' fix to your start up programs and seemingly eliminated my problem. 

I hope this helps with some of the freeze victims out there. 

Please anyone wants to comment or refine this I am grateful, I am sure you know more then I.

---


---
title: "[First MOTU Patch] Patch does not seem to apply to built .deb"
date: 2017-10-08
forum: Packaging and Compiling Programs
---

### Post by lrdev on 2017-10-08
Hi everyone, 

I'm trying to avoid contacting the mailing lists in so hoping that I might get some help here first, if the mailing lists are the correct place to ask could you please point me to which one? ( motu, developer-outreach, other? )

The bug I'm trying to fix is a typo in the man page for mount - [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/1712433](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/1712433) 

I followed the steps at [http://packaging.ubuntu.com/html/fixing-a-bug.html](http://packaging.ubuntu.com/html/fixing-a-bug.html) 

```
pull-lp-source util-linux artful
cd util-linux-2.30.1
edit-patch lp1712433
Edited sys-utils/mount.8 and fixed the type
dch -i ( I needed to this before exiting the tmp directory where in the link it says to do it after )
exit (tmp shell)
dch -i now seems to be run automatically after exiting the shell so I added my changelog description
debuild -S -d -us -uc
pbuilder-dist artful build ../util-linux_2.30.1-0ubuntu5.dsc
I then copied ~/pbuilder/artful_result/util-linux_2.30.1-0ubuntu5_amd64.deb to a vm running artful and installed using sudo dpkg -i ./util-linux...
```

When I ran man mount I saw the typo was still present so I went back to my dev machine and ran "quilt push" until no more patches were available then ran from debuild again with the same result. Can anybody see where the problem is? 

Thanks, 
Liam

---


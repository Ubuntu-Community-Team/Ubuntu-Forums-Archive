---
title: "FC4 Chroot Mini-HowTo"
date: 2006-08-07
forum: Outdated Tutorials &amp; Tips
---

### Post by almamuerta on 2006-08-07
[CENTER]**_[SIZE="4"]Ubuntu Dapper - FC4 Chroot Mini-HowTo[/SIZE]_**[/CENTER]


**Install rpmstrap from debian ([http://packages.debian.org/unstable/admin/rpmstrap](http://packages.debian.org/unstable/admin/rpmstrap))**
$wget [http://mirrors.kernel.org/debian/pool/main/r/rpmstrap/rpmstrap_0.5.2-2_all.deb](http://mirrors.kernel.org/debian/pool/main/r/rpmstrap/rpmstrap_0.5.2-2_all.deb)
$dpkg -i rpmstrap_0.5.2-2_all.deb

**Build the chroot:**
$mkdir /var/chroot/fc4/
$rpmstrap --verbose stentz /var/chroot/fc4/

**Add to fstab (**/etc/fstab**):**
/dev            /var/chroot/fc4/dev         none    bind            0       0
proc-fc4     /var/chroot/fc4/proc        proc    defaults        0       0
devpts-fc4   /var/chroot/fc4/dev/pts    devpts  defaults        0       0

**Run:**
mount /var/chroot/fc4/dev
mount /var/chroot/fc4/proc
mount /var/chroot/fc4/dev/pts
cp /etc/resolv.conf /var/chroot/fc4/etc/
cp /etc/hosts /var/chroot/fc4/etc/

**Install dchroot whit apt-get**
apt-get install dchroot

**Add to **/etc/dchroot.conf**:**
fc4 /var/chroot/fc4/

**Replace "$releasever" with "4" in all files in (**/etc/yum.repos.d/**):**

**For bash in chroot, run:**
dchroot -c fc4

You can use this for an easy installation of zimbra and others comercials products without support for ubuntu.
My english is very basic :( , sorry.

---


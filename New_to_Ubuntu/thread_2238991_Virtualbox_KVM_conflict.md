---
title: "Virtualbox KVM conflict"
date: 2014-08-11
forum: New to Ubuntu
---

### Post by kurasdan on 2014-08-11
I appear to have a KVM conflict when I try to start Ubuntu via VirtualBox on a Windows 8.1 system.  I understand the solution is to purge the KVM module from Ubuntu.  Problem is that KVM is preventing me from starting Ubuntu in order to purge KVM from Ubuntu.  Help would be appreciated.

Thanks,
Daniel Kuras
Jackson, Michigan USA

---

### Post by Tadaen_Sylvermane on 2014-08-11
Boot VM with a live image, chroot into the installation and do the deed.

---

### Post by kurasdan on 2014-08-12
I deleted Ubuntu from VirtualBox, then performed a clean install via VirtualBox.  Ubuntu rebooted gave me access, so I started a terminal session and issued the command "sudo apt-get remove kvm". I powered down Ubuntu and was able to again bring it up.  Upon switching on my computer this morning, I attempted to start Ubuntu and received the error message shown in the attachment. I get the same message when I attempt to run CAELinux or when Ubuntu is the only VM. Suggestions?

Dan Kuras
Jackson, Michigan USA

---


---
title: "VMware lockups every minute"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by shanepardue on 2008-05-18
I installed VMware Server 1.0.5 on a 32-bit dual-core laptop and everything 
installed fine with the vmware-any-any patch. However, I've noticed that 
about every minute, my entire computer (host and guest) lock up for a few 
seconds. I can move the mouse around, but nothing is responsive until the 
system comes to.

Thanks for your help!

---

### Post by mmb1 on 2008-05-18
See if this helps:

[http://ubuntuforums.org/showthread.php?p=4868919](http://ubuntuforums.org/showthread.php?p=4868919)


Best of luck!

---

### Post by shanepardue on 2008-05-18
> **mmb1 said:**
> See if this helps:

[http://ubuntuforums.org/showthread.php?p=4868919](http://ubuntuforums.org/showthread.php?p=4868919)


Best of luck!
That's the guide I used, thanks anyway!

---

### Post by shanepardue on 2008-05-19
Also, it doesn't seem a Windows 2003 server image will work as a domain controller even if it is a bridged network connection..I'm running out of ideas/options.

---

### Post by Living2007 on 2008-05-19
> **shanepardue said:**
> I installed VMware Server 1.0.5 on a 32-bit dual-core laptop and everything 
installed fine with the vmware-any-any patch. However, I've noticed that 
about every minute, my entire computer (host and guest) lock up for a few 
seconds. I can move the mouse around, but nothing is responsive until the 
system comes to.

Thanks for your help!
 Maybe the VM is using too much RAM.

---

### Post by shanepardue on 2008-05-19
> **Living2007 said:**
> Maybe the VM is using too much RAM.
Nah, I gave the image 256mb and I have 2gb of ram.

I'm a little disappointed with virtualization on the Linux desktop. The domain controller issue seems to be related to VMware though. It occurs on Windows as well.

---

### Post by Living2007 on 2008-05-20
> **shanepardue said:**
> Nah, I gave the image 256mb and I have 2gb of ram.

I'm a little disappointed with virtualization on the Linux desktop. The domain controller issue seems to be related to VMware though. It occurs on Windows as well.

Silly me, i was supposed to say "too little". Ubuntu needs 512mb of RAM to run properly.

---

### Post by shanepardue on 2008-05-20
I've tried upping the ram to no avail. It seems to be network-related. And I can't figure out why I can't create a domain controller out of a VM as well.

---

### Post by Living2007 on 2008-05-20
> **shanepardue said:**
> I've tried upping the ram to no avail. It seems to be network-related. And I can't figure out why I can't create a domain controller out of a VM as well.

Hmm..., I don't have experiance on networking, so I can't help here. Sorry :?: :oops:

---

### Post by shanepardue on 2008-05-24
I'm not completely sure what the problem is since it works fine 
in Windows, but the same exact VMware image freezes every few 
seconds. It has forced me into Windows for VMware.

---


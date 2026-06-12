---
title: "Install GRUB2 to a virtualbox vdi image"
date: 2012-07-18
forum: New to Ubuntu
---

### Post by kara85 on 2012-07-18
Hi!
I tried to install grub2 to a mounted virtual box vdi image, but when I started the virtual machine it didn't work.
 I used the following commands for compile and installation:  
 (in decompressed folder: )
 ./configure --prefix=/mnt/ --exec-prefix=/mnt/
 make
 make install
 (in /mnt/sbin folder: )
 ./grub-install --boot-directory=/mnt/boot /dev/nbd0
 

  The error massage was: „no such device: xxx”
 

 The grub.cfg file doesn't load.
 

 Please someone help me what should I do.

---

### Post by doctorbighands on 2012-07-18
Curious: Why are you wanting to do this?

I'm not a great resource for something like you're asking (I love VirtualBox, but it's still basically magic to me), but it seems to me that the VB application itself does basically what Grub would normally do - that is, load the OS of your choice using whatever options you want/need. So although I can't help you with your question directly, I'm wondering if there isn't some other way to do whatever it is you're trying to do...

---


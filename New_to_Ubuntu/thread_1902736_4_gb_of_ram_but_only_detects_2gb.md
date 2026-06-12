---
title: "4 gb of ram but only detects 2gb?"
date: 2011-12-31
forum: New to Ubuntu
---

### Post by ilikelinuxitisthebest on 2011-12-31
hey guys i have ubuntu 11.10 and when i go into system monitor it only says it has 2gb ram. i have a 32 bit istallation. just wondering how i can fix it?

---

### Post by ubudog on 2011-12-31
Hi there!  Does your computer support a 64-bit installation?  If so, that would probably be the best option.  A 32-bit kernel doesn't detect your ram over 2.5GB (as far as I know, please correct me if I'm wrong).

---

### Post by ubudog on 2011-12-31
Or, you could use a PAE kernel to use all your RAM.

---

### Post by ilikelinuxitisthebest on 2011-12-31
How do i set up this pae thing?

---

### Post by gandaran on 2011-12-31
> **ilikelinuxitisthebest said:**
> How do i set up this pae thing?
install synaptic package manager, then on synaptic scroll down to the linux kernels to mark the intended kernel for install.
synaptic is the best tool to control your system.

---

### Post by philinux on 2011-12-31
> **ilikelinuxitisthebest said:**
> How do i set up this pae thing?

 [http://www.jonboy60.com/2011/01/20/howto-install-kernel-pae/](http://www.jonboy60.com/2011/01/20/howto-install-kernel-pae/)

---

### Post by ilikelinuxitisthebest on 2011-12-31
@gandaran I have synaptic package manager. that was actually the first thing i did. anyway thank you for your replies it worked perfectly. thanks.

---


---
title: "Installing Virtual Box"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by sjbaugh on 2008-09-14
I have run another version of Linux (32 bit Fedora) in VirtualBox under Ubuntu 64 bit and I found that I could not get USB from the virtual machine and the quality of sound was poor. The sound improved to some extent when I enabled the visualization extensions in VirtualBox, but still not perfect. I say this in case these points are important to you. (I have not tried VMWare on Linux, only on WinXP).

Steve

---

### Post by howefield on 2008-09-14
> **sjbaugh said:**
> ... I found that I could not get USB from the virtual machine...

Was this the version of Virtualbox from the Ubuntu repository ?

This is the OSE version (Open Source Edition) which doesn't have USB support but the PUEL (Personal Use Evaluation License) version on the virtualbox website does, although you may need to activate it.

---

### Post by sjbaugh on 2008-09-14
> Was this the version of Virtualbox from the Ubuntu repository ?

I got mine from the website as a .deb file. It is not the virtualbox-ose in the repository.

It is version 1.6.2 and does have an option to enable USB (there is no reference to OSE in the About Box or the Help), but when I try to do it I get:

"Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer."

I have not been able to find any reference to a USB Proxy service on Ubuntu.

A friend of mine has had a similar problem.

Steve

---

### Post by Sef on 2008-09-14
Moved to its own post.

---


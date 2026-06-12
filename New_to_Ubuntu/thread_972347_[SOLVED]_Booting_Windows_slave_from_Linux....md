---
title: "[SOLVED] Booting Windows slave from Linux..."
date: 2008-11-05
forum: New to Ubuntu
---

### Post by akelsall on 2008-11-05
Yeah, I know this is probably a pipe dream, but I have to ask. 

I have Ubuntu loaded on my primary drive, and have my old Windows drive as my slave drive. Is it possible to boot the slave drive from within a virtual machine itself (e.g. VirtualBox or VMware)?  

I know it's possible to install VBox and then install XP within the VBox environment, but is there a way to boot the old Windows drive itself (from within the VM environment)?

Thanks,

Andy

---

### Post by philinux on 2008-11-05
[http://ubuntuforums.org/showthread.php?t=823876](http://ubuntuforums.org/showthread.php?t=823876)

---

### Post by akelsall on 2008-11-06
I am going to try this and post my results in this thread. It'd be great if it works!! Thanks for the link.

Andy

---

### Post by akelsall on 2008-11-07
After reading some other posts, it seemed that others were having various issues when running Windows from a slave drive, so I chose the simplest route and loaded VirtualBox last night. 

VBox was a breeze. I read just a little bit of their documentation before attempting to load Windows as a Guest OS. If you've done a lot of software installations in Windows, I think you'll find this pretty easy. It took maybe 20 minutes to figure out exactly what I needed to do. After that, it was just your basic Windows install from within VirtualBox. It came right up and I could surf the Net from within Windows immediately. I highly recommend using VBox. 

Just as an FYI: I had set aside a /windows partition for XP Pro. After the install, only 1.5 Gb had been used. I'm going to load a few other apps (like Camtasia and MS Money), but that should still leave me PLENTY of space in the 12G I set aside for Windows and the Win apps I still need to use.

Andy

---


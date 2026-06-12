---
title: "VirtualBox on Ubuntu 20.04 critical error"
date: 2020-05-16
forum: New to Ubuntu
---

### Post by magunto on 2020-05-16
Hello,
I had previously ubuntu 19.10 and installed VirtualBox, and then set up a virtual machine. Recently upgraded to Ubuntu 20.04 and now getting "critical error" when starting VirtualBox as a standard user. I can start VirtualBox as root (using sudo VirtualBox), I can start the virtual machine, but then I cannot login to the machine. It looks like the screen is not reading the mouse pointer or keyboard. What could have gone wrong? Is there a way to fix it?

---

### Post by David D. on 2020-05-17
I also had a critical error with VirtualBox after upgrading to 20.04.  I was able to fix my problem by using Synaptic to remove VirtualBox and reinstall the latest version from the VirtualBox website.

---

### Post by ajgreeny on 2020-05-17
I added the Oracle repos for VBox to my 20.04 systems as shown at the Linux Downloads section of the VBox site, Debian hosts but bear in mind that you have to use the eoan version in the line in your sources.list file even though you're  using focal; if you use focal in the line it will throw an error when updating repos.

---


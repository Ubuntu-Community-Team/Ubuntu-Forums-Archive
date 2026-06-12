---
title: "postinst without root"
date: 2010-06-22
forum: Packaging and Compiling Programs
---

### Post by NoBugs! on 2010-06-22
A .deb package can have a postinst script that runs after installation, this works fine, but it always runs as root. Is there any way to make the postinst script leave root and run as normal user? Some commands, like editing gconf settings, need to be run as normal user.

---

### Post by Umang on 2010-06-23
I don't know much about gconf, but if you change the default settings for that computer, then the users (except those who have manually overrided the default value for a paricular key) will all recieve the changes.

How do you change defaults? I don't know myself. But I do remember that the ubuntu-light-theme made a controversial change to a default setting in Lucid (i.e. shift the window command buttons to the left instead of the right). I've just looked at the source package and I seem to find a 'gconf-defaults' file in the debian directory. Look up `man dh_gconf` for more info.

How you do run as a normal user? I don't know. However it does seem impossible to do so. How should dpkg decide which normal user to run as and even if it does, dpkg is not supposed to make any user-specific change. If the user deletes his/her account, then how will it uninstall? Also, why should only one user be affected by a certain change?

Finally, you cannot run a certain script for each user one by one. This is because these changes will not affect user accounts created after the installation of your package.

Hope this helps. :)

---


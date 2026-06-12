---
title: "Installing HP printer on Ubuntu LiveUSB offline - how to get dependencies"
date: 2013-04-21
forum: New to Ubuntu
---

### Post by meeble on 2013-04-21
Hi Ubuntu forums,

I am an abosolute Ubuntu beginner, and I have searched for an answer to my question, but so far no luck. Any help appreciated:

I am trying to install my HP Deskjet 2510 printer using HPLIP, on a LiveUSB Ubuntu 12.10 on my windows machine, which has 0 persistence, and is deliberately offline.

When I install HPLIP it finds missing dependencies, which it expects I can download, but I would like to do an offline installation.

Is this possible? Ideally I would download the required dependencies via Windows, stash them in the root directory of the USB, and from there be able to access them in Ubuntu.

If it is possible, do I have to reinstall every time I boot (I assume yes because I have persistence set to zero)? 

Alternatively, is there a distro which will include the dependencies and HPLIP driver?

Here is a list of the dependencies that Ubuntu asks for:

[I]error: A required dependency 'gcc (gcc - GNU Project C and C++ Compiler)' is still missing.
error: A required dependency 'python-devel (Python devel - Python development files)' is still missing.
error: A required dependency 'cups-devel (CUPS devel- Common Unix Printing System development files)' is still missing.
error: A required dependency 'libusb (libusb - USB library)' is still missing.
error: A required dependency 'libtool (libtool - Library building support services)' is still missing.
error: A required dependency 'cups-image (CUPS image - CUPS image development files)' is still missing.
error: A required dependency 'libjpeg (libjpeg - JPEG library)' is still missing.[/I]

I realise I could solve it by going online, but the point of booting using LiveUSB is to have a secure offline environment that is not windows.

thanks in advance

---

### Post by Cheesemill on 2013-04-21
You shouldn't need to download anything, hplip is part of a standard installation.

In fact I've just done a clean installation of 12.10 and I have that exact printer. I just plugged it in and it was ready to print.

---

### Post by meeble on 2013-04-21
Thanks @cheesemill - if it ends being that simple I will be so happy.

Will boot in tommorrow and see if it works

---

### Post by meeble on 2013-04-22
Ok - Ubuntu doesn't react when the printer is powered on.

- CUPS and HPLIP are definitely installed, I checked the history
- The printer definitely works (tested in windows)
- The USB port definitely works in Ubuntu (tested an external HDD)

Basically, Ubuntu does not react when the printer is plugged in. When I go to add printer, it does not appear either.

Is there some reason why it wouldn't be recognised? 

I am going to reformat and reload the LiveUSB installation in the hope that it does something.

Any other ideas welcome :-)

---

### Post by meeble on 2013-04-22
FIXED!

Damn it - I just re-made my LiveUSB from scratch and now it works perfectly. Plugged in, recognised, prints. Nothing else to do.

Thanks for your help with this, and it's probably better to delete this thread to not confuse people. Looks like I just had a problem with my original installation.

Thanks again @cheesemill

---

### Post by mastablasta on 2013-04-22
otherwise there is hplip installer available for download as well as .deb packages for offline install. you know in case you need the latest version...
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)
[http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)

and .deb files:
[FONT=Courier New][http://packages.debian.org/unstable/allpackages](http://packages.debian.org/unstable/allpackages)[/FONT]

---


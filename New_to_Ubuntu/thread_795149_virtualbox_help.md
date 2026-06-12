---
title: "virtualbox help"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by shifty_powers on 2008-05-15
had a problem after i had installed virtualbox from the sun website. (not the ose).

uninstalled that and installed the ose version. but i then installed virtualbox-ose-guest module for linux-image-2.6.24-17-386 , which installed the linux image and played merry hell with my xserver.

sorted that out and reinstalled ose. but now i get the attached message.

any ideas?

---

### Post by shifty_powers on 2008-05-15
anyone?

---

### Post by techno-mole on 2008-05-15
ive been using virtual box for awhile and not had any trouble with it, i installed it from here - [http://www.virtualbox.org/](http://www.virtualbox.org/)

the version im running is the latest version - 

virtualbox_1.6.0-30421_Ubuntu_hardy_i386.deb

the only issue i have is something to do with the usb ports or something, which is a known issue and fixable (i just havent bothered as i dont use and usb devices on my virtualbox)

i dont know what the difference is between ose and non ose, but like i said i use that version from the (what used to be innotek) website now owned sun sun microsystems.

its a pain, but i would remove all versions of vb you have, and then get that .deb file and install it from that, then when you run it, dont select it from the " system tools " menu, open terminal and type sudo VirtualBox to run it (its a permission thing, i had trouble with it when i run it by clicking it in the menu)

not much help i know, but its the best solution i could think of, of course if you have been running the vm for a while and need to get data off it, then you'll need some one who knows more about it than me.

---


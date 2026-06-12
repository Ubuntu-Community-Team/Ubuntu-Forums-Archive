---
title: "USB Port (hardware)"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by vfrankli on 2008-05-29
Hello,
     I am absolutely new to Ubuntu (Linux).  I successfully installed Ubuntu and can operate the e-mail programs and the browser, and I can install/remove software, but I don't have a clue how to get the OS to recognize and use the USB port so I can backup the system to an external hard drive.  I would appreciate any help.

Virgil

---

### Post by Helgiks on 2008-05-29
You shouldn't really have to do anything, if it does not work by just plugging it in you should post more info about it, and your computer's hardware.

---

### Post by vfrankli on 2008-05-29
I am looking for an icon on the desktop or on the taskbar.  I don't see the external HDD anywhere on the laptop.  I can see the CD/DVD drive and icon.

---

### Post by rbc on 2008-05-29
Some specifics about your computer, and the external (make, how it's formatted) might help. Also plug the external hard drive in, then from terminal, type these and post the results. Forgive me if I am telling you something you already know, but you get terminal window by going to Applications-->Acces sories-->terminal, then type these commands:
1. mount
2. lsusb
3. sudo fdisk -l (that's a small L). You will be prompted for a password which will not display when you type it (again forgive me if you know this)

Can't promise you I can help, but this might be helpful for the gurus

---

### Post by vfrankli on 2008-05-30
Gracias, it worked!  I'm in business until the next issue.:)

---

### Post by rbc on 2008-05-30
Glad it's working. It's also good form to mark the thread as Solved when the issue is resolved. And when you resolve issues on your own, please post back with solutions so that other may learn. By the way, welcome to the forums, from a fellow Virginian

---


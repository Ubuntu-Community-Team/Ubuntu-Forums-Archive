---
title: "How to encrypt &amp; password protect a file"
date: 2018-08-23
forum: New to Ubuntu
---

### Post by waltd on 2018-08-23
Hi all, I installed Ubuntu Version 18.04.1 with Gnome desktop.  I noticed the compress option doesn't have "other options" to encrypt/password files. How do I encrypt and password protect a file or collection of files with Ubuntu Version 18.04.1?

---

### Post by #&amp;thj^% on 2018-08-23
There are still some good ways to Securing Files. [https://www.howtoforge.com/tutorial/how-to-hide-lock-encrypt-and-secure-your-files-on-linux/](https://www.howtoforge.com/tutorial/how-to-hide-lock-encrypt-and-secure-your-files-on-linux/)

And another option : [https://www.makeuseof.com/tag/encrypt-files-folders-ubuntu/](https://www.makeuseof.com/tag/encrypt-files-folders-ubuntu/)

And as always make sure to have good back-ups.
I'm sure others will have even more ways to achieve what you want.

---

### Post by slickymaster on 2018-08-23
Personally I use [https://packages.ubuntu.com/search?keywords=encfs](https://packages.ubuntu.com/search?keywords=encfs)

---

### Post by Dennis N on 2018-08-23
> **waltd said:**
> Hi all, I installed Ubuntu Version 18.04.1 with Gnome desktop.  I noticed the compress option doesn't have "other options" to encrypt/password files. How do I encrypt and password protect a file or collection of files with Ubuntu Version 18.04.1?

To have the encrypt and decrypt options for files in the Ubuntu right-click menu, you need to install **seahorse-nautilus**.

---

### Post by Geoffrey_Arndt on 2018-08-24
Or another option . . open the "File Roller" application (aka "Archive Manager") and then just drag the directory or individual file from Nautilus into the File Roller window and respond to the pop up window regarding actions. You should then see the "other options" tag for encryption.

Note1:   you must also have "p7zip" installed (available via Synaptic PM).

---


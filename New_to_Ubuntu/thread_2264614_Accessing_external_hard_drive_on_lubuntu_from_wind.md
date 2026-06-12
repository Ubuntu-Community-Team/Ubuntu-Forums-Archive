---
title: "Accessing external hard drive on lubuntu from windows 7"
date: 2015-02-08
forum: New to Ubuntu
---

### Post by Chris_Chivers on 2015-02-08
I have a Lubuntu box setup running Kodi on it. Kodi is reading files from an external hard drive. 

I use a windows 7 laptop in day to day use and when I try to access the files on KODIBUNTU (how it is listed in my Windows machine) it gives me mostly empty directories (System & Sounds) a Media directory with a splash.png file in it, a SYSTEM directory with more empty directories, but no access to the external hard drive plugged into the system. I am sure I am missing something simple to get me access to those files, but I don't know what it is.

I want the ability to add/remove files from the external hard drive without having to unplug it from the KODIBUNTU system and plug it into my Windows 7 laptop.

Any and all help will be appreciated. 

Chris

---

### Post by yancek on 2015-02-08
If it's two separate computers on a local network, samba is what you need on Linux.  I don't use it myself but you should be able to find a lot of tutorials on setting it up on Ubuntu.

---

### Post by Chris_Chivers on 2015-02-08
Yes, it is two separate computers on the same network. 

I'll look into samba. Thank you yancek.

---

### Post by Chris_Chivers on 2015-02-09
Okay. I've modified the smb.conf file and can now read my external hard drive on the libuntu server. Thank you yancek!

Chris

---

### Post by yancek on 2015-02-09
You're welcome.  Glad you got it working.

---


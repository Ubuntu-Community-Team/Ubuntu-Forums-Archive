---
title: "wireless in hardy doesnt work"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by konner920 on 2008-07-16
how do i get my linksys WMP54GS to work.. in hardy 8.04 i could never get it to work and i dont know anything about linux someone help pl0x

---

### Post by konner920 on 2008-07-16
can someone please help me im in a hurry :[

---

### Post by appi2012 on 2008-07-16
you need ndiswrapper
ndiswrapper is a utility that runs your windows drivers in ubuntu. So, if you have a cd windows drivers read this post:
[http://ubuntuforums.org/showpost.php?p=5384727&postcount=7](http://ubuntuforums.org/showpost.php?p=5384727&postcount=7)

---

### Post by konner920 on 2008-07-16
still no wireless.. i did all that

---

### Post by moore.bryan on 2008-07-16
have you installed linux-restricted-modules-common?

according to a couple of webpages, your card uses a broadcom chipset that has been built-in kernels since 2.6.17-rc2.

---

### Post by Aarookie on 2008-07-16
Try this

1. Insert your Ubuntu cd and open terminal
2.sudo apt-cdrom add
3.sudo apt-get install build-essential (Not sure this part is necessary but it sure was for proper tarballing when I was trying to install multiple tar.gz files.
4.sudo apt-get install ndisgtk

5.Open system>administration>Windows wireless drivers menu/program.
6.My computer sort of stuttered at this point but eventually a little window opened up and I was able to browse to my .inf file from winxp driver.
7.After a reboot and figuring out wpa2 wasn't going to work without more stuff I havn't figured out yet I changed my router back to wep, and was able to configure wireless

---


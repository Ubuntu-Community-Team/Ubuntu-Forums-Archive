---
title: "Canon Pixma 160 and xsane"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by PhilJ on 2008-11-01
Hi all,
 I have a Canon pixma 160 working using Turboprint drivers. Xsane recognises the scanner half without any prompting and that works also.  I have tried to get this to work under PClinuxOS,Dremlinux,Mepis and Mandriva 2008 but none of them will recognise it using zsane or kooka. All will work the printer half after installing the Turboprint driver. 
 Why is it that Ubuntu, Kubuntu aand Xubuntu all recognise the scanner but the others dont? 
Using sane-find-scanner in Ubuntu I get a message saying something about libusb and the vendor id and product id. I have tried copying the contents of sane.d into the other distros but that doesnt work. Can anyone tell me what the problem is.. Is it a kernel problem or sane backend problem?  Or indeed can anyone tell me what backend Ubuntu is using for this scanner or how to find out?

Thanks

Philj

---

### Post by Shady3D on 2009-01-15
well i use same printer scanner, i managed to get the printer work easily but for the scanner after i search the was some people the say remove the current Xsane and install it again, but it was troublesome,** so the best thing i think is to use that command "scanimage > NAME_OF_THE_IMAGE.pnm"**

also u can take this one step further (if u r good with shell commands or python) and make a script that asks u to input the name of the image and then u can use the luncher every time u want to scan any image, also if u did that plz share it with me :D 

i use Ubuntu 8.10

---


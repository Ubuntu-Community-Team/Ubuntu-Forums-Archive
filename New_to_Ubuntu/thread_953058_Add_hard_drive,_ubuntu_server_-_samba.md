---
title: "Add hard drive, ubuntu server - samba"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by captclearleft on 2008-10-19
Hey There,

I am Abbsolutely the newist Noob out there.

I needed network storage and a file server. 

I installed Ubuntu server on an old motherboard/parts.

It took me a day or so, but I figured most of it out.  I am learning very quickly.  I have installed samba, and have some shared folders.

??????????????????????????????????????????????????????????????

I installed a new hard drive, and would like to access it on the network.  I have NO idea how to do that.  Can I just share the drive on the network, or do I have to map it somehow?  No idea how to do that either.  

Network consists of xp machines, and one ubuntu server, running samba.

Please help.  I know you are all real smart.  I am not. PLease keep it simple, if possible.

---

### Post by captclearleft on 2008-10-19
How do I use fstab?

What is the code to mount my second drive, and how do I share it?

---

### Post by gpsmikey on 2008-10-19
You have to "mount" the new drive so your system can see it, then you use Samba to make it visible however you want to the windows machines.

As far as Samba goes, check out the book **"Samba 3 by Example"** - you can buy it from Amazon or get the pdf version for free from the samba main site.  Here is the link to the pdf version of the book:
[http://www.samba.org/samba/docs/Samba3-ByExample.pdf](http://www.samba.org/samba/docs/Samba3-ByExample.pdf)
Snoop through there until you find a configuration similar to what you want to do and use his examples.  

Ah, found the link to the **fstab tutorial **-- check this out:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Hope that helps !! 
mikey

---

### Post by captclearleft on 2008-10-19
Thanks man, Ill give it a look.  thanks

---


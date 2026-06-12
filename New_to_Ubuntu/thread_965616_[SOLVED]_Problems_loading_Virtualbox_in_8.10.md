---
title: "[SOLVED] Problems loading Virtualbox in 8.10"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by Berean on 2008-10-31
Hi,

I've read somewhere that Absolute Beginner Talk is where to post on problems with Intrepid.  If this isn't the case perhaps a mod will move it?

I've updated from 8.04 to 8.10 simply by downloading and not doing a fresh install.  I then couldn't load Virtualbox.  So I uninstalled Virtualbox and then reinstalled it.  I can start virtualbox but as soon as I try to start my XP the following error messages occur.  Any ideas gratefully received.

---

### Post by drs305 on 2008-10-31
Have you run what the error message suggested?
```
sudo /etc/init.d/vboxdrv setup
```

If so and it didn't work, please provide the output.

You should also make sure you are a member of the vboxusers group:
```
id
```

---

### Post by BenAshton24 on 2008-10-31
This is relatively easy to solve :P I had this problem a while back (it explains how to fix it in the error message :P)

simply open up terminal ( Applications --> Accessories --> Terminal )

and type this command:

> sudo /etc/init.d/vboxdrv setup

Enter your password, press enter and after about 30 seconds it should be complete. virtual box should now work again :D

Hope this helps,
--Ben

---

### Post by Berean on 2008-10-31
The first screenshot shows what happens when I run the first command; the second when I administer id.  I'm still having exactly the same errors come up.

---

### Post by diablo75 on 2008-10-31
Try [this]("http://davestechsupport.com/blog/2008/10/29/how-to-fix-virtualbox-after-upgrading-ubuntu/").

---

### Post by Berean on 2008-11-01
I've tried all of these suggestions but to no avail.  However, when inputting /etc/init.d/vboxdrv status the following output is given;
Virtualbox kernel module is not loaded.  Does this mean I haven't downloaded it, that it simply - as it suggests - hasn't loaded?

---

### Post by BGFG on 2008-11-01
Hi, I've been to the VB site and i did not see a version for 8.10 Are we sure it's fully supported in 8.10 ?
I'm actually waiting for an 8.10 version form the site.

---

### Post by Berean on 2008-11-01
Since my last post I removed all things Virtualbox, and then reinstalled Virtualbox 2.0 using the download and not the repository.  It's working fine now.  So in answer to your question; I don't know if it's supported but it's working on my laptop.  Thanks to all for your input.  Regards, Berean.

---


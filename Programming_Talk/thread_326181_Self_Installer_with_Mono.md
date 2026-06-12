---
title: "Self Installer with Mono"
date: 2006-12-27
forum: Programming Talk
---

### Post by hadiriazi on 2006-12-27
Hello to all programmers out there

I have made an application with mono (C#) on Ubuntu Edgy 6.10.
How do i create a self installer for it? the application is a .exe file and the command used to execute it is mono appname.exe
Is mono pre-installed on all ubuntu or linux based OS's?

---

### Post by a.sappia on 2006-12-27
Usually Linux Distribution didn't use self-installing software
(unlike windows there is NO setup.exe)

you can create a package (deb, rpm) for your application which will be installed
using the ways your distro usually has (apt-get/rpm/emerge)

OR 

you can use makeself, a software that creates bash scripts self-installing...

both way you have to set that mono is a dependency foy your software, 
they'll manage to install it.

Personally, I strong disagree with the makeself solution. The great advantage of
repositories will be useless if you don't use it...

---

### Post by hadiriazi on 2006-12-27
> **a.sappia said:**
> 
you can create a package (deb, rpm) for your application which will be installed
using the ways your distro usually has (apt-get/rpm/emerge)


Thanks for the reply

Could you explain in more details how to make a deb,rpm package, or if there is a guide on the net or the forums you could direct me to?

---


---
title: "packing with upstart"
date: 2011-01-14
forum: Packaging and Compiling Programs
---

### Post by pablop on 2011-01-14
Hi

(using maverick)

I'm trying to understand how to include an upstart job when packaging (.deb).
Ubuntu wiki mentions dh_installupstart but I couldn't find it:
[https://wiki.ubuntu.com/FoundationsTeam/Specs/KarmicUpstartPackagingPolicy](https://wiki.ubuntu.com/FoundationsTeam/Specs/KarmicUpstartPackagingPolicy)

dh_make creates the init.d.ex example file but there is no upstart.ex example file.
Am I suppose to just drop the file and use the install file to tell the package to put it under /etc/init/mypkg.conf
or is there a better way?

Thanks

---

### Post by SevenMachines on 2011-01-15
Have a look at
$man dh_installinit
which is what does upstart jobs these days (depending on version i suppose :) ) 

It will try to install the upstart job or the init job depending on whats in your debian/ directory

> debian/package.upstart
           If this exists, it is installed into etc/init/package.conf in the
           package build directory.

       debian/package.init
           Otherwise, if this exists, it is installed into etc/init.d/package
           in the package build directory.

---

### Post by pablop on 2011-01-15
The packaging guide is missing that part.
Thanks.

---

### Post by SevenMachines on 2011-01-15
Thanks to you too, i didnt know it had changed until i looked for it!

---


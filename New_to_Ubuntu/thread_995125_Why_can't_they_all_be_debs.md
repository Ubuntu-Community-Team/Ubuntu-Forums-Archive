---
title: "Why can't they all be debs?"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by lavadisco on 2008-11-27
Debs are so easy to install. Why do developers use other packaging methods that are harder to use? Forgive my total ignorance if there is some obvious reason.

---

### Post by llamakc on 2008-11-27
> **lavadisco said:**
> Debs are so easy to install. Why do developers use other packaging methods that are harder to use? Forgive my total ignorance if there is some obvious reason.

Because they do not develop specifically for Debian-based distributions. Their software runs on many other types of GNU/Linux.

Usually most packages that you find out 'in the wild' already have a corresponding package available in Ubuntu.

Do you have an example of one?

---

### Post by DirtDawg on 2008-11-27
I really like binary packages that can run without being installed system-wide. Why can't they all be binaries? :D

Also, I think debs are fairly dependent on certain versions of packages. For example, there would need to be separate debs for an application that has the dependency 'libsooperrad' as maybe Hardy uses 'libsooperrad-0.9' while Ibex uses 'libsooperrad-1.0.' Take into account all the different debian-based distros and there's a potential mess in the making.

---

### Post by ibuclaw on 2008-11-27
If you read the howtos on making debian packages:
[http://tldp.org/HOWTO/Debian-Binary-Package-Building-HOWTO/](http://tldp.org/HOWTO/Debian-Binary-Package-Building-HOWTO/)

[http://ubuntuforums.org/showthread.php?t=51003](http://ubuntuforums.org/showthread.php?t=51003)

You'll see that they are probably the most complicated of all package files in Linux... though I agree that their efficiency far surpasses any other.

There are several places you can look for deb files that may have what you want.
[http://www.getdeb.net](http://www.getdeb.net)

[http://ppa.launchpad.net/](http://ppa.launchpad.net/)

And you can use **alien** and **fakeroot** to repackage other formats into deb files (rpm, tgz, etc).

And if all else fails, you could always compile and package it yourself.

Regards
Iain

---

### Post by drubin on 2008-11-27
> **tinivole said:**
> If you read the howtos on making debian packages:
[http://tldp.org/HOWTO/Debian-Binary-Package-Building-HOWTO/](http://tldp.org/HOWTO/Debian-Binary-Package-Building-HOWTO/)

[http://ubuntuforums.org/showthread.php?t=51003](http://ubuntuforums.org/showthread.php?t=51003)

You'll see that they are probably the most complicated of all package files in Linux... though I agree that their efficiency far surpasses any other.

There are several places you can look for deb files that may have what you want.
[http://www.getdeb.net](http://www.getdeb.net)

[http://ppa.launchpad.net/](http://ppa.launchpad.net/)


Nice info. :) 

> 
And you can use **alien** and **fakeroot** to repackage other formats into deb files (rpm, tgz, etc).

And if all else fails, you could always compile and package it yourself.

Regards
Iain

Bot those application tent to makes things go horriblely wrong on your system. If any thing dose go wrong every one will claim it was Alien and have no idea how to fix it. 

I suggest compiling stuff your self instead of trying to turn a rmp into a deb.

---


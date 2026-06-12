---
title: "upgrade open office"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by skiddly on 2008-11-09
Hi all i notice even the latest ubuntu 8.10 only has version 2.4 installed how do i upgrade it to open office 3.0

---

### Post by loell on 2008-11-09
you need to add a repository, in your sources.list

```

deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```

then do an update

**sudo apt-get update**
**sudo apt-get install openoffice.org**

---

### Post by Technomouse on 2008-11-09
thank you LOTS yay new OO

---

### Post by Ciwan on 2009-04-09
Hi guys

@loell I try them deb commands > but it says no such commands exist !!

I want to update my OpenOffice to the latest version :(

Please help :(

---

### Post by pbpersson on 2009-04-09
> **Ciwan said:**
> Hi guys

@loell I try them deb commands > but it says no such commands exist !!

I want to update my OpenOffice to the latest version :(

Please help :(

Those are not commands, they are lines you need to add into your sources.list file using a text editor.

---


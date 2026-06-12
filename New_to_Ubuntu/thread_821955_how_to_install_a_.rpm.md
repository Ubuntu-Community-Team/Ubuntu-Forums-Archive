---
title: "how to install a .rpm?"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by shamusl on 2008-06-07
I'm new to ubuntu and need a virtualization program, so I downloaded one from vmware and I need to install it, but it's not a deb, it's an RPM. How do I install this?

---

### Post by Xerp on 2008-06-07
Use "alien" to convert it.

sudo apt-get install alien
sudo alien -i /path/to/file.rpm

But why not use Virtualbox or any of the other virtualisation tools in the repository?

---

### Post by quelx on 2008-06-07
[http://ubuntu-tutorials.com/2008/05/30/install-vmware-server-106-on-ubuntu-804-hardy/](http://ubuntu-tutorials.com/2008/05/30/install-vmware-server-106-on-ubuntu-804-hardy/)

---

### Post by imT on 2008-06-07
in terminal paste this:
```
sudo apt-get install alien
```
```
sudo alien -i /path/to/file.rpm
```

---

### Post by drs305 on 2008-06-07
The easiest way is probably with alien, an rpm > deb converter.

First, download and install alien:
```
sudo aptitude install alien
```

Next, convert the rpm file to a deb file:
```
sudo alien -k /path-to-rpm-file
```

Finally, install the new deb:
```
sudo dpkg -i packagename.deb
```

Just make sure to put the proper path in the command if the commands aren't started in the same folder as the rpm/deb.

---

### Post by shamusl on 2008-06-07
> **Xerp said:**
> Use "alien" to convert it.

sudo apt-get install alien
sudo alien -i /path/to/file.rpm

But why not use Virtualbox or any of the other virtualisation tools in the repository?

Is Virtualbox any slower?

---

### Post by Xerp on 2008-06-07
Its on a par with vmware - so I find its fast enough for me on the desktop :) If I want to use server virtualisation I tend to go with Xen though.

---


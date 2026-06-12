---
title: "What's the difference between RPM and DEB"
date: 2008-09-24
forum: Recurring Discussions
---

### Post by esmailgad on 2008-09-24
what is the difference between RPM package and DEB package and how can I install it

---

### Post by SunnyRabbiera on 2008-09-24
> **esmailgad said:**
> what is the difference between RPM package and DEB package and how can I install it

They are different installers for different systems, RPM is for redhat based systems and Deb is for debian systems.
Ubuntu is a debian system so most .deb's you will find will be compatible with ubuntu.
RPM's are a little different, to install them you need to convert them, there is a terminal application called alien that is in your repositories, it will help convert your RPM's to debs.

---

### Post by brandon88tube on 2008-09-24
RPM, I believe is for distros like redhat and DEB are for debian distros like Ubuntu

---

### Post by SunnyRabbiera on 2008-09-24
> **brandon88tube said:**
> RPM, I believe is for distros like redhat and DEB are for debian distros like Ubuntu

yes, the package managers are simular but the rpm's are packaged differently.

---

### Post by dub_u on 2008-09-24
> **esmailgad said:**
> what is the difference between RPM package and DEB package and how can I install it

I only installed a DEB package once, and it was by entering

```
sudo dpkg -i filename.deb
```

Also found this [http://www.newlinuxuser.com/howto-use-dpkg-to-install-deb-files/](http://www.newlinuxuser.com/howto-use-dpkg-to-install-deb-files/)

---

### Post by SunnyRabbiera on 2008-09-24
> **dub_u said:**
> I only installed a DEB package once, and it was by entering

```
sudo dpkg -i filename.deb
```

Also found this [http://www.newlinuxuser.com/howto-use-dpkg-to-install-deb-files/](http://www.newlinuxuser.com/howto-use-dpkg-to-install-deb-files/)

yes but with gedebi the terminal is less needed

---

### Post by brandon88tube on 2008-09-24
Yeah with a .deb you should be able to just double click and run it.

---

### Post by dmizer on 2008-09-24
Split these off topic posts into a separate thread.  Carry on.

---


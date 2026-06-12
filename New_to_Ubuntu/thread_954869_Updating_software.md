---
title: "Updating software"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by brandoncolorado on 2008-10-21
Why can I just download OpenOffice 3 in Windows to update to the latest version, but I have to wait until Ubuntu developers think it is best to include it in Ubuntu?  Is this because the OS updates all of my software for me?  Can I just download a .deb and install it like an .exe to update to the latest version?

---

### Post by wolfen69 on 2008-10-21
[here]("http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=3.0.0") is the .deb file for 3.0. just double click to install.

---

### Post by brandoncolorado on 2008-10-21
> **wolfen69 said:**
> [here]("http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=3.0.0") is the .deb file for 3.0. just double click to install.

Thank you.  Will this new installation be updated automatically in the future?

---

### Post by ChildOfMana on 2008-10-21
You should be able to download a .deb from [here](http://download.openoffice.org/other.html#en-US).

It would be advisable to uninstall your current version of Open Office first though (via Add/Remove programs).

**Edit:** Duh, wolfen69 beat me to it! Oh well :)

---

### Post by Idaho Dan on 2008-10-21
You can.  There is a .deb you can download at openoffice.org.
I haven't tried it yet myself.

---

### Post by shifty_powers on 2008-10-21
you can indeed download a deb from the open office site. it would be best to remove open office 2 and use something like gdebi to install oo3.

```
sudo apt-get --purge remove openoffice.org-*
```

would completely remove oo

---

### Post by stephanvaningen on 2008-10-21
> **brandoncolorado said:**
> Thank you.  Will this new installation be updated automatically in the future?

If apt-get finds a newer version in one of the sources via the APT library, it will.

---


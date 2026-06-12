---
title: "When can we expect Open Office3"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by captgadget on 2008-11-02
to show up in Synaptic?

---

### Post by ugm6hr on 2008-11-02
Never in the main repos for Intrepid / Hardy etc.

Perhaps in backports much later - but unlikely.

This is because of the version freeze that Ubuntu follows.

So it will be in Jaunty (I'm sure).

---

### Post by eldragon on 2008-11-02
i dont think it will ever...until JJ.

just download the debs from [www.openoffice.org](www.openoffice.org)

remove openoffice.org-core

and install.

dead simple.

---

### Post by sayems on 2008-11-02
sudo gedit /etc/apt/sources.list

## Openoffice.org
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

sudo apt-get update

---

### Post by reg4c on 2008-11-02
I did what sayems suggested but it said that the packagages for OO.org have been kept back?

How can I push them through?

Cheers

---

### Post by Sef on 2008-11-02
> sudo gedit /etc/apt/sources.listThat is not correct.   For more information, read [RootSudo]("https://help.ubuntu.com/community/RootSudo?highlight=%28gksudo%29").

For Ubuntu and Xubuntu, it is ```
gksudo gedit /etc/apt/sources.list
```For Kubuntu, it is ```
Kdesudo gedit /etc/apt/sources.list
```If you only use sudo, you may have problems upon logging in.

---


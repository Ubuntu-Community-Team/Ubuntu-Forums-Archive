---
title: "Help with installing programs"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by irem-altan on 2011-10-21
Hello,
I have attempted to install open office 3.3 by downloading it from its site and opening the .deb files in the terminal.  I think this should have done the job of installing it, but I cannot find open office anywhere (searched for it in dash home, nothing).  I have ubuntu 11.10.  I'd be very glad if you could help.

---

### Post by Paqman on 2011-10-21
Libre Office (which is a version of Open Office) comes pre-installed in Ubuntu. Try searching for it in the dash.

---

### Post by llamabr on 2011-10-21
Is there some reason you want to install this version from the website, rather than just using ubuntu's package manager?  If not, then have a look at:

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by irem-altan on 2011-10-22
> **llamabr said:**
> Is there some reason you want to install this version from the website, rather than just using ubuntu's package manager?  If not, then have a look at:

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

Well, there is no package manager in 11.10.  I'd have to install that too.

---

### Post by cozumel on 2011-10-22
Hi,

Synaptic Package Manager was dropped in 11.10 in favour of Software Center.
You can install Synaptic from terminal with:```
sudo apt-get install synaptic
```

---

### Post by shihkster1015 on 2011-10-22
open office was dropped out
try searching for libre office

---

### Post by 3rdalbum on 2011-10-22
Openoffice 3.3 is some way behind the current Libreoffice.

Just use Libreoffice.

If you have multiple .deb files they might need to be installed simultaneously, which requires a command like this:

```
sudo dpkg -i *.deb
```

in the folder that contains the packages.

A better idea would be to find a repository or a PPA that contains the packages you want to install.

In your particular case, though, the current Libreoffice is much more capable than the current Openoffice.org. There's no reason to use OOo. Just use Libreoffice; it's preinstalled on Ubuntu.

---


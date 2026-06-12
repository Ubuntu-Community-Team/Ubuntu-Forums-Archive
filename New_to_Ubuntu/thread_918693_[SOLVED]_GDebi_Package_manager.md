---
title: "[SOLVED] GDebi Package manager"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by Louis de Broglie on 2008-09-13
Hi,

I google searched for this but did not find much info. Can anybody tell me what is this and it's key features? :)

---

### Post by ajmorris on 2008-09-13
hi there,
GDebi package manager is a GUI package manager to install .deb files, just like synaptic. The only feature it has that synaptic doesnt, is the ability to install local .deb packages, instead of just remote ones. IMO, you're just better off sticking with synaptic. and using dpkg for local .deb packages.

AJ

---

### Post by rraj.be on 2008-09-13
Thsi is what i got from synaptic summary for that package.

```
Simple tool to install deb files
gdebi lets you install local deb packages resolving and installing
its dependencies. apt does the same, but only for remote (http, ftp)
located packages.

This package contains the libraries and command-line utility.
```

This is what i got from man gdebi

```
GDEBI(1)                                                              GDEBI(1)

NAME
       gdebi - Simple tool to install deb files

SYNOPSIS
       gdebi [package.deb]

DESCRIPTION
       gdebi  lets you install local deb packages resolving and installing its
       dependencies. apt does the  same,  but  only  for  remote  (http,  ftp)
       located packages.

AUTHOR
       This  manual  page  was written by Gustavo Franco <stratus@debian.org>,
       for the Debian project (but may be used by others).

                                 Dec 23, 2005                         GDEBI(1)
```

---

### Post by Louis de Broglie on 2008-09-13
OK, If I save the packages which apt downloaded in a usb drive. Then is there any way to make it a repository for apt ? :) ( I am not talking about personal repo here. Just a usb drive )

---

### Post by northern lights on 2008-09-13
> **Louis de Broglie said:**
> OK, If I save the packages which apt downloaded in a usb drive. Then is there any way to make it a repository for apt ? :) ( I am not talking about personal repo here. Just a usb drive )
apt-cdrom can do this.

Run```
sudo apt-cdrom -d=/mountpoint add
```where '/mountpoint' needs to be replace with the USB pen drive's actual mount point, most likely something along the lines of '/media/flashdrive'

---

### Post by Louis de Broglie on 2008-09-13
Is there any restriction on the file system being used in the usb drive ? :)

---

### Post by northern lights on 2008-09-13
> **Louis de Broglie said:**
> Is there any restriction on the file system being used in the usb drive ? :)
That's a good question. Theoretically, anything that Linux can read from should be fine. Apt might be more restrictive though. Format the pendrive as ext3 to be on the safe side...

---

### Post by Louis de Broglie on 2008-09-13
And after doing that I will see my usb drive in the software sources GUI -> Third-party Software ? :)

---

### Post by northern lights on 2008-09-13
I'm not too certain about the GUI, but it will be listed in your sources.list and when running ```
apt-get install APP
``` without an internet connection but with the .deb on the pendrive, App will be installed without complains now.

---

### Post by Louis de Broglie on 2008-09-13
Ok, thanks for the idea :)

---


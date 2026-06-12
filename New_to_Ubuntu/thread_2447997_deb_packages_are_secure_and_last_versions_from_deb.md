---
title: "deb packages are secure and last versions from debian.org ?"
date: 2020-07-30
forum: New to Ubuntu
---

### Post by aug7744 on 2020-07-30
Debian packages downloaded in [https://packages.debian.org](https://packages.debian.org) and [https://security.debian.org/debian-security](https://security.debian.org/debian-security) are secure and have the latest software versions ? Thanks for reply.

---

### Post by CelticWarrior on 2020-07-30
Yes, no and you shouldn't use packages made for Debian in Ubuntu.

---

### Post by aug7744 on 2020-07-31
I had downloaded an software from debian.org and not start. I ubuntu repository not have some softwares that are available in debian.org.

---

### Post by ActionParsnip on 2020-07-31
Debian and Ubuntu are different distributions of Linux so the packages in the default repositories may be different.

Mixing debs between the two will cause a big mess because the dependancy packages may not be available. Debs are not standalone installs and reuse libraries are other packages to perform what they need. This keeps the OS small and extremely efficient. Debian debs may expect different versions of libraries to their Ubuntu counterparts and you can be installing more debs from Debian to satisfy them. Eventually you'll have a mutant OS that more than likely won't update due to mangled packages and you'll have to reinstall. 

What package(s) are you wanting? Maybe we can advise a better way to install them that won't break your OS.

---

### Post by aug7744 on 2020-07-31
"Mixing debs between the two will cause a big mess because the dependancy packages may not be available"
The mess if only the software will be installed, but not will run thus having useless files on disk ?

"What package(s) are you wanting? Maybe we can advise a better way to install them that won't break your OS."
I am beginner Linux user.
I wait to understand exactly how softwares are installed in Linux and avoid to download again each software if the system need to be reinstalled because I use an slow metered internet connection.
I understand that Linux not is windows, but not is possible to have all softwares and dependecies saved in folder to avoid to download again ?
Where I can download standalone packages ?

---

### Post by maglin2 on 2020-07-31
> **aug7744 said:**
> 
Where I can download standalone packages ?
You could try snaps, flatpaks or appimages. Of these I have only ever used snaps. The ones I use (Chromium and Zoom) auto update frequently and seem to use a lot of bandwidth in doing so. I doubt if they are what you are looking for.

---

### Post by grahammechanical on 2020-07-31
If we trust the developer or organization that is the source of the software then the software is secure as far as we are concerned. If you cannot trust the applications in the Debian repositories then you cannot trust Debian Linux. If we cannot trust the applications in Ubuntu repositories then we cannot trust the Ubuntu distribution. It comes down to the issue of trust.

Applications in repositories are not the latest releases. It takes time to examine a new version of an application to make sure that it can be trusted. A new version of Ubuntu is released every six months and that is when new releases of application are included in Ubuntu. A few applications like Libreoffice and Firefox get upgrades throughout the support period of the Ubuntu version. I am using Ubuntu 18.04 and it now has the same versions of Libreoffice and Firefox as Ubuntu 20.04. But this requires an internet connection and connection and download charges which you wish to limit.

It is possible to install Ubuntu without having an internet connection. We can also limit updates to important security updates. That will limit download costs. In Ubuntu and Debian it is possible to set up an offline repository.

[https://wiki.debian.org/DebianRepository](https://wiki.debian.org/DebianRepository)

[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

It should also be possible to make an ISO image of the Ubuntu installation and then restore that image to the hard disc instead of doing an online install as from the beginning. A business might do this to upgrade many machines without having to pay download charges for every machine.

[https://help.ubuntu.com/community/IsoImage](https://help.ubuntu.com/community/IsoImage)

Regards

---

### Post by ActionParsnip on 2020-07-31
> 
The mess if only the software will be installed, but not will run thus having useless files on disk ?


The mess is the dependencies of the Debian files being possibly different to the Ubuntu ones. You could satisfy those but there may be further deps of those. There may also be files from one of the Debian debs in a different Ubuntu deb and apt and dpkg don't like that and will throw errors up stating so. You could force this but then updates won't install cleanly for the exact same reason next time.

Can you start to see why it's a bad idea now?

If you want to use packages from Debian.....use Debian.

---

### Post by aug7744 on 2020-08-02
@[**[COLOR=#000000]grahammechanical[/COLOR]**]("https://ubuntuforums.org/member.php?u=1087323")
Thanks very much for the clue :)

Thanks for all replies.

---


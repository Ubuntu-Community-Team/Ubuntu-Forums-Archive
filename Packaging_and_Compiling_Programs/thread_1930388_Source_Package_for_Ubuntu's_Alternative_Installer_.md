---
title: "Source Package for Ubuntu's Alternative Installer Ncurses Installer"
date: 2012-02-23
forum: Packaging and Compiling Programs
---

### Post by beastrace91 on 2012-02-23
I'm wondering where I can find the source code for the Ubuntu ncurses installer than the alternative CD uses to install with.

I know of packages.ubuntu.com - but I'm not sure of the installers package name exactly.

Thanks,
~Jeff

---

### Post by SevenMachines on 2012-02-23
Can't check at the moment but I think its the debian-installer package?

---

### Post by beastrace91 on 2012-02-23
> **SevenMachines said:**
> Can't check at the moment but I think its the debian-installer package?

It is not. That is a package containing only documentation.

~Jeff

---

### Post by SevenMachines on 2012-02-23
Not something I'm well informed on but although the package itself is docs, it does generate installer images. 
[http://wiki.debian.org/DebianInstaller/Build](http://wiki.debian.org/DebianInstaller/Build)

---

### Post by beastrace91 on 2012-02-23
So if I understand this correctly there isn't just a package or two that contains a launch-able ncurses based installer (how ubiquity handles things). Instead this is a method for generating an installer image that ONLY contains the ncurses installer when booted?

Just trying to understand what is going on fully, because it is very different from how things are handled with regards to the Ubiquity GUI installer.

~Jeff

---

### Post by SevenMachines on 2012-02-23
Seems that way, I haven't had a chance to look properly though so I wouldn't take my word for it. That link may be worth a try out to figure out exactly what's going on

---


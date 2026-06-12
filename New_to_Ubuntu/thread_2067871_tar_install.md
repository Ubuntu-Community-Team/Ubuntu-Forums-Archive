---
title: "tar install?"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by Yezinki on 2012-10-07
Hi there,

How does one extract & install a tar.gz package?

Thanks.

---

### Post by jerrrys on 2012-10-07
Hi Yezinki

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=How+does+one+extract+%26+install+a+tar.gz+package&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=How+does+one+extract+%26+install+a+tar.gz+package&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by Yezinki on 2012-10-07
Thanks jerrrys. Extracting is not a real issue but installing is, what command to type in the terminal for it to be installed.

---

### Post by oldos2er on 2012-10-07
> **Yezinki said:**
> what command to type in the terminal for it to be installed.

That depends on what the tar file contains. A tar.gz or tar.bz2 file is just a compressed archive, similar to a .zip file.

---

### Post by alphacrucis2 on 2012-10-07
Often the archive will contain a readme file that explains how to install it. The archive could be source code that you need to compile, or it could be compiled binaries with an install script. If there is no readme file then check the website you obtained it from. They may have install instructions or maybe even a forum where you can ask.

---

### Post by Yezinki on 2012-10-07
When extracted as files & installaer.sh

---

### Post by newb85 on 2012-10-08
Look for a text file containing instructions.  The installer.sh file will have to be set as executable before it can be run.  Only do this if you trust the source of the package.

To do this from the terminal, navigate to the folder where you extracted the archive.  Set it as executable.

```
sudo chmod +x installer.sh
```

and execute

```
sudo ./installer.sh
```

---

### Post by Yezinki on 2012-10-08
```
vaio@VGC-LS1:~$ sudo chmod +x installer.sh
[sudo] password for vaio: 
vaio@VGC-LS1:~$ sudo ./installer.sh
Rootkit Hunter installer 1.2.16

Usage: ./installer.sh <parameters>

Ordered valid parameters:
  --help (-h)      : Show this help.
  --examples       : Show layout examples.
  --layout <value> : Choose installation template.
                     The templates are:
                      - default: (FHS compliant; the default)
                      - /usr
                      - /usr/local
                      - oldschool: old version file locations
                      - custom: supply your own installation directory
                      - RPM: for building RPM's. Requires $RPM_BUILD_ROOT.
                      - DEB: for building DEB's. Requires $DEB_BUILD_ROOT.
                      - TGZ: for building Slackware TGZ's. Requires $TGZ_BUILD_ROOT.
                      - TXZ: for building Slackware TXZ's. Requires $TXZ_BUILD_ROOT.
  --striproot      : Strip path from custom layout (for package maintainers).
  --install        : Install according to chosen layout.
  --overwrite      : Overwrite the existing configuration file.
                     (Default is to create a separate configuration file.)
  --show           : Show chosen layout.
  --remove         : Uninstall according to chosen layout.
  --version        : Show the installer version.

vaio@VGC-LS1:~$ 

```

Thanks.

How do I run rkhunter?

---

### Post by Cheesemill on 2012-10-08
Why are you trying to install from a tar.gz?

The repositories already contain version 1.3.8 of rkhunter which can be installed by simply doing:
```
sudo apt-get install rkhunter
```

---


---
title: "confused about ActivePython 2.7 &lt;SOLVED&gt;"
date: 2013-03-07
forum: New to Ubuntu
---

### Post by al.adab on 2013-03-07
hello,

i need to install ActivePython 2.7 (or later versions) on Xubuntu 12.04 to use it in combination with *PyCrypto 2.1 for 32bit Windows and Python 2.7*, in connection to Calibre, and through Wine. 

can you plz advise on the installation process and how to enable it on wine? On Synaptics I can see a list of "Python" programs, but no "ActivePython". I found the following as a possible installation methods: 

[I]cd /tmp
wget [http://downloads.activestate.com/ActivePython/releases/2.7.2.5/ActivePython-2.7.2.5-linux-x86_64.tar.gz](http://downloads.activestate.com/ActivePython/releases/2.7.2.5/ActivePython-2.7.2.5-linux-x86_64.tar.gz)
tar xzf ActivePython-2.7.2.5-linux-x86.tar.gz
cd ActivePython-2.7.2.5-linux-x86
./install.sh[/I]

or from [http://www.activestate.com/activepython/downloads](http://www.activestate.com/activepython/downloads) (though I came across a number of people who reported error messges when unpacking + installing the tar.gz file, for some reason). 

If either method works - I can't try it right now, as I'm on an extremely slow connection, will be able to in a day or two - how can I enable it into the Wine registry? 

Thanks!

---

### Post by schragge on 2013-03-07
Wait, why would you install Calibre through Wine? It's packaged for Linux and [the package]("http://packages.ubuntu.com/precise/calibre") is in Ubuntu repositories. So is [python-crypto]("http://packages.ubuntu.com/precise/python-crypto") (this is how PyCrypto is called on Debian-based systems, see [Debian Python Policy]("http://www.debian.org/doc/packaging-manuals/python-policy/ch-module_packages.html#s-package_names")).

---

### Post by al.adab on 2013-03-07
sorry, I realise I wasn't clear, I do have Calibre installed. I first of all need to install PyCrypto (for Windows) through Wine. To do that, Wine asks me to install ActivePython 2.7 (and include it in the Wine registry, I suppose). I need PyCrypto for Calibre.

---

### Post by schragge on 2013-03-07
Still, I don't get it. PyCrypto is also packaged for Ubuntu, please re-read my comment above.

---

### Post by al.adab on 2013-03-07
sorry I'm being slow, but after installing PyCrypto - I appreciate there's a version for Debian but I need to stick to a certain installation procedure and install the Windows version on Wine - how can I install ActivePython 2.7.2 for Linux X86, if I need to, and in any case include it in the Wine register?

---

### Post by schragge on 2013-03-07
I'm pretty sure you don't need it. The installation procedure is for Windows users. You want to install a Calibre plugin that requires python and PyCrypto. So
```
sudo apt-get install python-crypto
``` python 2.7 is already installed on your system. Then put the plugin into folder where Calibre would see it, install and configure it from inside Calibre. That's all.

---

### Post by al.adab on 2013-03-08
gotcha. thanks tons for your help.

---

### Post by schragge on 2013-03-22
I guess I need to give you a step by step guide.
Install Calibre and PyCrypto:
```
sudo apt-get install calibre python-crypto
```
Download zip archive with plugins.
Unpack. 
You'll get three folders. The plugins for Calibre are in *Calibre_Plugins*. Notice where you are in the directory tree.
Read the ReadMe files there. They explain how to install the plugins in Calibre.
Launch Calibre.
Open *Preferences* / *Change calibre behavior* (three gears icon) or press **Ctrl**+**P**
In the **Advanced** row select *Plugins*
Click on the button *Load plugin from file* in the bottom row.
Navigate to the folder *Calibre_Plugins* where you've unpacked plugins.
Select plugin you want to install and click on the *Open* button.
Confirm your choice.

---


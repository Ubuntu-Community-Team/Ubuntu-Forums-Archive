---
title: "Wrong architecture 'amd64'"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by Jozefff on 2012-04-19
Hello

i have UBUNTU 11.10 and i am tying to install virtual box from here
[http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html)

and  here

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

i downloaded i3[86]("http://download.virtualbox.org/virtualbox/4.1.12/virtualbox-4.1_4.1.12-77245%7EUbuntu%7Eprecise_i386.deb") and also  [AMD64 version]("http://download.virtualbox.org/virtualbox/4.1.12/virtualbox-4.1_4.1.12-77245%7EUbuntu%7Eprecise_amd64.deb")

but in all cases i get written Wrong architecture 'amd64'

virtualbox-4.1_4.1.12-77245~Ubuntu~oneiric_i386.deb
virtualbox-4.1_4.1.12-77245~Ubuntu~natty_amd64.deb
virtualbox-4.1_4.1.12-77245~Ubuntu~oneiric_amd64.deb

do you know what to do?

---

### Post by jerome1232 on 2012-04-19
edit: How did you try installing the .deb's btw, did you try simply double clicking the desired .deb, should be the i386 one that will work for you.

----------------------------------------------------------------------------------------------------

Add their repo to your sources file.

Click gear icon in the top right, click system settings, click software sources. Click the other sources tab, click add in the bottom left corner. Copy and paste the following line, then click add source.

```
deb http://download.virtualbox.org/virtualbox/debian oneiric contrib
```

Close all windows, open a terminal with ctrl+alt+t, copy and paste the following. It simply add's their gpg key so you can verify their software.

```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
```

Now update your cache of software and install virtualbox

```
sudo apt-get update
sudo apt-get install virtualbox-4.1
```

This is all taken straight from their website [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by oldos2er on 2012-04-19
Why not install virtualbox from the repositories?

---

### Post by jerome1232 on 2012-04-19
> **oldos2er said:**
> Why not install virtualbox from the repositories?

Your right, I didn't notice the repo version is 4.1.

---

### Post by rhss6-2011 on 2012-04-19
If you have the deb files you can try moving one or the other to your home folder and then:

sudo apt-get install -y gdebi (application that installs deb files)

If that program reads the wrong architecture on both packages try:

```
cd
sudo dpkg --force-architecture -i FILENAME.deb
```

---

### Post by dzponce11 on 2012-04-19
You need the Intel or x86 .iso, because that's what VirtualBox was meant to emulate.

---


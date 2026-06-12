---
title: "lubuntu 12.04 cannot see the deb package to install though ..."
date: 2014-01-14
forum: New to Ubuntu
---

### Post by piadex2 on 2014-01-14
Dear Readers,

Here is what I tried: I navigated into the directory where the deb package was placed. After that I said:
```
sudo apt-get install -f slimboat_i386.deb
```
(remark: I checked several times if slimboat_i386.deb was the name of the package but it was)

Result:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package slimboat_i386.deb
E: Couldn't find any package by regex 'slimboat_i386.deb'

```
How is that possible?
Thank You in advance.

piadex2

---

### Post by howefield on 2014-01-14
The error is telling you that it cannot locate the package, so that most likely means either the path is wrong or the file name is wrong.

Try using the tab key to autocomplete the file name when typing it.

(just realised you were using apt-get)... or try

```
sudo dpkg -i slimboat_i386.deb
```

---

### Post by mastablasta on 2014-01-14
double clicking the deb doesn't work? or opening it in software center? or running it from filemanager?

anyway you can try this type in the comand then drag the file from file manager. it should give the whole path in terminal and proceeed with install.

---

### Post by piadex2 on 2014-01-15
Dear howefield,

I would like to use the apt-get because others said if there is dependency problem it can handle it.
I tryed to use TAB key. It lists the sli... files but there is no slimboat... Why?

In the file manager I definitelly saw the slimboat_i386.deb file. Is it possible that apt-get cannot handle .deb files?

Thank You in advance.

piadex2

(dear mastablasta, thanks for the help but I would like to understand why apt-get does not work)

---

### Post by mörgæs on 2014-01-15
Lubuntu 12.04 is out of support. Before investing more time in this old fella I suggest you consider a fresh install of Lubuntu 13.10.

---

### Post by oldos2er on 2014-01-15
apt-get doesn't "see" *deb files you have on your hard disk, it's restricted to the sources (i.e., repositories) listed in /etc/apt/sources.list and /etc/apt/sources.list.d/*list
dpkg *will* install a local package, and you can resolve any dependency errors it generates with ```
sudo apt-get install -f
```

---

### Post by steeldriver on 2014-01-15
another option for resolving dependencies automatically would be to use gdebi instead of dpkg I think?

---

### Post by piadex2 on 2014-01-15
Dear Ann,

Thank You for your help. There is one thing I do not understand. How does " sudo apt-get install -f " command know which .deb file has dependency problems? Does it check all the .deb files in the working directory (thus solves all the dependency problems of all the files)?
Thank You for your help in advance.

piadex2

---

### Post by piadex2 on 2014-01-15
Dear mörgæs,

I know there is a newer version of Lubuntu. My problem is that I have only an old **Pentium M 1.4** (banias) and they say the newer Lubuntu needs certain features that this CPU does not have. At least before I decided to install Lubuntu I found this information so 12.04 was installed instead of the newest.

piadex2

---

### Post by Dennis N on 2014-01-15
I would second steeldriver's suggestion about using **gdebi package installer**. **gdebi** will check the repositories for dependencies needed to install the .deb file, and automatically download them (if available) as part of the installation process. Also, it's a GUI, no terminal commands involved. Just right click on your .deb file, and in the menu select "open with gdebi" or similar phrasing. **gdebi** is available in the Ubuntu repositories if not already installed.

---

### Post by mörgæs on 2014-01-15
Here's something about the [PAE]("https://help.ubuntu.com/community/PAE") problem (and solutions).

---


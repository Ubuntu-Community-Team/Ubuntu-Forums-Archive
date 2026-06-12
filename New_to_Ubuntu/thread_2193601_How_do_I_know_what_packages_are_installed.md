---
title: "How do I know what packages are installed?"
date: 2013-12-13
forum: New to Ubuntu
---

### Post by zaphod.control4 on 2013-12-13
I have just signed up for a VPS service.  This service runs Ubuntu 12.04 64 bit.  I will be using this as a seedbox and I want to install rtorrent and rutorrent.  This machine already has Transmission and Transmission-daemon installed.  The rutorrent instructions that I have found include installing Apache - I already have Apache installed.  Does it matter that I may have some of the packages that I need already installed?  If the package is already installed will this be skipped?  Is there a command that shows which packages are already installed.

For example [here ]("http://torrentfreaknews.blogspot.ca/2013/06/how-to-install-rtorrentrutorrent-on.html")is the tutorial that I am looking at using. Here is some of the install procedure:
> [FONT=Trebuchet MS]sudo apt-get update[/FONT] 
[FONT=Trebuchet MS]sudo apt-get install subversion  build-essential automake libtool libcppunit-dev libcurl3-dev libsigc++-2.0-dev  unzip unrar-free curl libncurses-dev[/FONT] 
[FONT=Trebuchet MS]sudo apt-get install apache2 php5  php5-cli php5-curl[/FONT] 
I know that Apache is already installed so will this screw up my existing Apache install that was installed for Transmission-daemon?

---

### Post by sandyd on 2013-12-13
> **zaphod.control4 said:**
> I have just signed up for a VPS service.  This service runs Ubuntu 12.04 64 bit.  I will be using this as a seedbox and I want to install rtorrent and rutorrent.  This machine already has Transmission and Transmission-daemon installed.  The rutorrent instructions that I have found include installing Apache - I already have Apache installed.  Does it matter that I may have some of the packages that I need already installed?  If the package is already installed will this be skipped?  Is there a command that shows which packages are already installed.

For example [here ]("http://torrentfreaknews.blogspot.ca/2013/06/how-to-install-rtorrentrutorrent-on.html")is the tutorial that I am looking at using. Here is some of the install procedure:
I know that Apache is already installed so will this screw up my existing Apache install that was installed for Transmission-daemon?
Welcome to Ubuntu!

Packages that are already installed will not be reinstalled - unless you specifically tell it to reinstall.

You can check if a package is installed by running
```
dpkg -l packagenamehere
```

---

### Post by VMC on 2013-12-13
```
dpkg --get-selections
``` Will list all installed packages.

---

### Post by conversationjames on 2014-01-02
```
dpkg --list
```

---

### Post by chkneater on 2014-01-02
Also you can use synaptic to show all installed packages or you can search in the synaptic toolbar for a specific package.

---


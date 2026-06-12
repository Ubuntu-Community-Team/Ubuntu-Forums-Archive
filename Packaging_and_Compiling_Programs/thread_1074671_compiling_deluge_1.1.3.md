---
title: "compiling deluge 1.1.3"
date: 2009-02-19
forum: Packaging and Compiling Programs
---

### Post by fjf on 2009-02-19
I got the source, but they do not provide deb anymore.  How can I compile it?.

---

### Post by lvlo on 2009-02-19
Take a look here: [https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa)

---

### Post by fjf on 2009-02-19
I'll answer myself.  It is in the readme file:

> ==========================
Installation Instructions:
==========================

First, make sure you have the proper build dependencies installed.  On a normal
Debian or Ubuntu system:

sudo apt-get install g++ make python-all-dev python-all python-dbus \
    python-gtk2 python-notify librsvg2-common python-xdg python-support \
    subversion libboost-dev libboost-python-dev libboost-iostreams-dev \
    libboost-thread-dev libboost-date-time-dev libboost-filesystem-dev \
    libboost-serialization-dev libssl-dev zlib1g-dev python-setuptools

The names of the packages may vary depending on your OS / distro.

Once you have the needed libraries installed, build and install by running:

	$ python setup.py build
	$ sudo python setup.py install

It works ;)

---

### Post by Hitman_Forhire on 2009-02-20
> **fjf said:**
> I'll answer myself.  It is in the readme file:



It works ;)

...Ditto

AMD64 Approved.

---

### Post by kaivalagi on 2009-02-21
No need to compile at all, as lvlo mentioned, there are apt based packages available. The 64 bit install works just fine from there.

See here: [http://dev.deluge-torrent.org/wiki/Download](http://dev.deluge-torrent.org/wiki/Download)

e.g. "There are packages at this PPA: https://launchpad.net/~deluge-team/+archive/ppa"

Just add them to your sources.list and add the key (get it from the launchpad site) and no more manual installs/updates...you'll keep up-to-date automatically :)

---

### Post by binbash on 2009-02-21
they have a repo at launchpad?

---

### Post by kaivalagi on 2009-02-21
> **binbash said:**
> they have a repo at launchpad?

Ohhhhhh YES!

About time, I only noticed today...not sure how long it's been around for. Not very long I dont think as I downloaded 1.1.2 recently and didn't see any of the details on the site.

---

### Post by fjf on 2009-02-22
I wanted to compile because I keep having the same problem since v.1.0: when I stop deluge and close it to reboot, and I start it again later most of the torrents do not start, the say ERROR and I have to delete them, reload the torrent file, and deluge then checks it and goes on with the download.  Anyone has any idea of the cause?.

Thanks!

---

### Post by kaivalagi on 2009-02-22
> **fjf said:**
> I wanted to compile because I keep having the same problem since v.1.0: when I stop deluge and close it to reboot, and I start it again later most of the torrents do not start, the say ERROR and I have to delete them, reload the torrent file, and deluge then checks it and goes on with the download.  Anyone has any idea of the cause?.

Thanks!

Compiling from source or installing from a package won't address you issues you've described. Both routes have the same end result.

Can you give more details on the error message?

Are you using full or compact allocation for torrent downloads? I use full allocation, it means the file contents wont end up spread across the disk.

Also where are you downloading to? Could it be the partition is corrupted in some way???

---

### Post by fjf on 2009-02-22
Compact allocation, partition checks fine.  When I reboot, the drop on deluge is red and says ERROR.  No more details.  I have to delete the download (force check does nothing), reload the torrent file, and then deluge checks the existing chunks and goes on fine from where it left.  Weird.

---

### Post by kaivalagi on 2009-02-22
> **fjf said:**
> Compact allocation, partition checks fine.  When I reboot, the drop on deluge is red and says ERROR.  No more details.  I have to delete the download (force check does nothing), reload the torrent file, and then deluge checks the existing chunks and goes on fine from where it left.  Weird.

If I were you I'd switch the settings to full allocation, and see whether new downloads still have the same issues

Strange though...

Have you checked on the deluge support forum to see whether other people has the same issues? I had a quick scan and it some issues posted look very similar...

---


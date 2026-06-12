---
title: "the rtorrent version in the repos isn't allowed at my favorite private tracker"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by energy. on 2008-08-15
```
sudo apt-get install rtorrent
```

gives me rtorrent 0.8.0 which is a banned client (for whatever reason) on a private tracker that I'd like to use.  I'd like to remove 0.8.0 and install one of the allowed clients

> rtorrent/0.7.9/0.11.9  (* rtorrent-0.7.9   * libtorrent-0.11.9) Stable
rtorrent/0.8.2/0.12.2 (* rtorrent-0.8.2   * libtorrent-0.12.2) Unstable

help doing this?

---

### Post by quibbler on 2008-08-15
> **energy. said:**
> ```
sudo apt-get install rtorrent
```

gives me rtorrent 0.8.0 which is a banned client (for whatever reason) on a private tracker that I'd like to use.  I'd like to remove 0.8.0 and install one of the allowed clients



help doing this?
try deluge, it's good.

Regards quibbler

---

### Post by sharks on 2008-08-15
try deluge.its the best (my opinion) under linux. try azureus. 

install wine and install bitcomet under it. it works great under wine.

---

### Post by energy. on 2008-08-15
> **quibbler said:**
> try deluge, it's good.

Regards quibbler

is deluge in the repositories?

---

### Post by sharks on 2008-08-15
yes. its deluge-torrent

---

### Post by tahina on 2008-08-15
The rtorrent is version 0.8.2 in the upcoming ubuntu Intrepid Ibex 8.10.

If it has no newer dependencies, you could download the .deb file from one of the mirrors here: [http://packages.ubuntu.com/intrepid/i386/rtorrent/download](http://packages.ubuntu.com/intrepid/i386/rtorrent/download) To install it, just doubleclick the .deb.

You'll notice if it won't install. 

To compile from source (and get the absolute latest version), download the source from rtorrents homepage and look here: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by sharks on 2008-08-15
but installing from repos is safe.dont compile until u r sure on how to compile.

---

### Post by energy. on 2008-08-15
> **sharks said:**
> but installing from repos is safe.dont compile until u r sure on how to compile.

I installed deluge from the repos, however, the version provided to me isn't the latest beta and is therefore banned from the tracker that I want to use.

---

### Post by mali2297 on 2008-08-15
If you want to try compiling the latest rtorrent, then copy/paste the following commands in the terminal:
```

sudo apt-get remove rtorrent libtorrent11
sudo apt-get install build-essential checkinstall libcurl3-dev libsigc++-2.0-dev libncurses5-dev
wget http://libtorrent.rakshasa.no/downloads/libtorrent-0.12.2.tar.gz
tar xvzf libtorrent-0.12.2.tar.gz
cd libtorrent-0.12.2/
./configure
make
sudo checkinstall
cd ..
wget http://libtorrent.rakshasa.no/downloads/rtorrent-0.8.2.tar.gz
tar xvzf rtorrent-0.8.2.tar.gz
cd rtorrent-0.8.2/
./configure
make
sudo checkinstall

```

---

### Post by dannyboy79 on 2008-08-15
i use bittornado, it's acceptable on the private trackers I use. it's pretty versatile I feel but then again I haven't used any other torrent programs besides the original bittorrent within windows long ago. the only bad thinig about bittornado is that each torrent get's it's own window. but there are many things you can set. my tracker made me use the latest, which is 0.3.18, which you can download and build from source here: [http://www.bittornado.com/download.html](http://www.bittornado.com/download.html). just read the README or INSTALL file.

good luck

---

### Post by hyper_ch on 2008-08-15
compile rtorrent from svn. Very simple, I made a little howto here:

[http://www.howtoforge.com/compile-rtorrent-from-svn-ubuntu-8.04-hardy-heron](http://www.howtoforge.com/compile-rtorrent-from-svn-ubuntu-8.04-hardy-heron)

Besides: Private tracker are evil!

---

### Post by dannyboy79 on 2008-08-15
> **hyper_ch said:**
> 

Besides: Private tracker are evil!

sorry to differ from your opinion but private trackers are where the latest stuff is (great quality I might add) and have way less of a chance of getting caught due to being "private". also, you get booted if your upload doesn't match at least your download rates so it keeps the scum leechers who don't upload the same amount they download off the site!

---


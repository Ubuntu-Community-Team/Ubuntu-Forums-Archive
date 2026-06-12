---
title: "transmission-daemon (tranmission-cli) and 8.04"
date: 2009-04-21
forum: Outdated Tutorials &amp; Tips
---

### Post by peternz on 2009-04-21
I upgraded all my packages a few days ago and found transmission-daemon no longer worked.  When I tried to run it I'd be informed it wasn't installed, even though it was.  When I tried to sudo apt-get transmission-cli it would tell me the most recent version was already installed.  Quite the quandary.

I've found that as of 19 April 2009, the current Transmission version (1.52) is not working with my setup.

My setup being a headless 8.04 installation (of the desktop edition).  I needed to go back a version.

This is a quick tutorial for anyone who faces the same issue.  There may be a more elegant way of doing this (I might be installing a couple of unnecessary packages for example) but it works.  And I need that.  :)  

Note this will download the Transmission 1.51 files to whatever directory you are currently in.  I used my Desktop folder.

```
sudo su
apt-get update
apt-get wget build-essentials automake autoconf libtool pkg-config libssl-dev libcurl4-openssl-dev intltool libxml2-dev libgtk2.0-dev libnotify-dev
wget http://download.m0k.org/transmission/files/transmission-1.51.tar.bz2
tar xvfj transmission-1.51.tar.bz2
cd transmission-1.51
./configure
make
make install
transmission-daemon
```

Mine retained my old preferences, although I did have to turn the whitelist off again.

It will also pay to edit /etc/apt/sources.list to comment out the Transmission repos if you have them, and then run

```
sudo apt-get update
```

To make sure it doesn't try to upgrade to the broken version again.

This should work for any previous version if you replace the URL in the wget command above with another file from: [http://download.m0k.org/transmission/files/]("http://download.m0k.org/transmission/files/")

Rockin'. \m/

---


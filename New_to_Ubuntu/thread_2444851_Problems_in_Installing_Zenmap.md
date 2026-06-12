---
title: "Problems in Installing Zenmap"
date: 2020-06-05
forum: New to Ubuntu
---

### Post by wombat71 on 2020-06-05
After being away from Ubuntu for 2 years I am back and have just installed the latest Ubuntu Mate on my laptop.
All went very smoothly - amazing improvements compared with before !
I installed Nmap successfully thinking it included the Zenmap GUI but it doesnt - or I cant find it !

So I set out to install Zenmap separately using *"sudo apt install zenmap"*
The result was :
[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package zenmap is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ndiff

E: Package 'zenmap' has no installation candidate

[/I]Given I have been away a while I am starting again as an absolute 'newby' so can anyone advise what this means and shove me in the right direction  ?
Thanks,

Mike

---

### Post by TheFu on 2020-06-05
The zenmap project died or didn't make newer packages available.

[https://github.com/nmap/nmap/issues/2022](https://github.com/nmap/nmap/issues/2022) is a bug for supporting 20.04.  In that bug, it seems the zenmap team is being hit with the python2 --> python3 change.  Canonical has deprecated python2 because the python dev team has clearly stated they are done with python2.  Canonical had no choice except to drop zenmap from their repos.

There is good news.  A workaround exists, but it will break getting updates for the dependencies and zenmap as part of your weekly patching efforts. A workaround has been offered:

```
mkdir -p ~/Downloads/zenmap
cd ~/Downloads/zenmap

wget [http://archive.ubuntu.com/ubuntu/pool/universe/p/pygtk/python-gtk2_2.24.0-6_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/p/pygtk/python-gtk2_2.24.0-6_amd64.deb)
wget [http://archive.ubuntu.com/ubuntu/pool/universe/n/nmap/zenmap_7.80+dfsg1-1build1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/n/nmap/zenmap_7.80+dfsg1-1build1_all.deb)

sudo apt install ./*.deb.  
```
I'd only load something like that onto a VM or install specifically used for scanning contracts.  It is a workaround, not a fix. There won't be any fix until zenmap is ported to python3.

---

### Post by wombat71 on 2020-06-06
Thanks Fu.
I am not surprised.
Wombat71

---


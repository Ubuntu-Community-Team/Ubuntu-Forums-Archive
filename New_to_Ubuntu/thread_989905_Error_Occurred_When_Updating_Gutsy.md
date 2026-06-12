---
title: "Error Occurred When Updating Gutsy"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by Andavane on 2008-11-22
Greetings:
Having updated Gutsy with no problems for many months now, it has just
said it is unable to update.
I get this message, and have no idea if there is anything I can "do":

---

### Post by marshall.robert on 2008-11-22
try this in terminal 
```

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by amac777 on 2008-11-22
I'm also still running gutsy and I'm getting the same error. (a couple days so far) 

I'm guessing it's a problem with the repository and will be fixed soon by the package managers.

---

### Post by shifty_powers on 2008-11-22
please bear in mind as well, that although gutsy was a lts, it is due to stop being supported inroughly six months. I would start to think about upgrading distro...

---

### Post by prshah on 2008-11-22
> **Andavane said:**
> Greetings:
Having updated Gutsy with no problems for many months now, it has just
said it is unable to update.
I get this message, and have no idea if there is anything I can "do":

Open System-Administration-Software Sources-Download From, and change to "Main Server" or "Server for India".

---

### Post by amac777 on 2008-11-22
Gutsy was not a lts, however, it does run like one on my computer. Very stable and I've had no reason to upgrade. 

I'm planning to keep running gusty until after its support ends. My plan is to replace it with a fresh install of Ubuntu 9.04 (Jaunty Jackalope) once that version is released around April 2009.

---

### Post by shifty_powers on 2008-11-22
heh yeah, always get gutsy mixed up with dapper for some reason :D

---

### Post by HughReid on 2008-11-22
> **marshall.robert said:**
> try this in terminal 
```

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

```

I've been getting the same messages as Andavane above as has my Father who is also using Gutsy. I tried the first two of the command suggested above (I didn't use the third one as I don't want to upgrade yet). The first two don't solve the problem and furthermore I get the following error messages:
Err [http://debian.tagancha.org](http://debian.tagancha.org) main/non-free Packages
  404 Not Found
Err [http://debian.tagancha.org](http://debian.tagancha.org) main/contrib Packages
  404 Not Found
Fetched 6B in 1s (3B/s)
Failed to fetch [http://debian.tagancha.org/debian/dists/main/non-free/binary-i386/Packages.gz](http://debian.tagancha.org/debian/dists/main/non-free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://debian.tagancha.org/debian/dists/main/contrib/binary-i386/Packages.gz](http://debian.tagancha.org/debian/dists/main/contrib/binary-i386/Packages.gz)  404 Not Found

Any ideas? If I use the third command will this solve the problem? Will it try to upgrade to Hardy Heron?
Thanks muchly

---

### Post by buyyourall3 on 2008-11-22
would u like to buy [the cheapest laptop](http://www.buyyourall.com) form china? please click [here](http://www.buyyourall.com) for more details

---

### Post by prshah on 2008-11-22
> **HughReid said:**
> 

Err [http://debian.tagancha.org](http://debian.tagancha.org) main/non-free Packages
  404 Not Found
Err [http://debian.tagancha.org](http://debian.tagancha.org) main/contrib Packages
  404 Not Found
Fetched 6B in 1s (3B/s)
Failed to fetch [http://debian.tagancha.org/debian/dists/main/non-free/binary-i386/Packages.gz](http://debian.tagancha.org/debian/dists/main/non-free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://debian.tagancha.org/debian/dists/main/contrib/binary-i386/Packages.gz](http://debian.tagancha.org/debian/dists/main/contrib/binary-i386/Packages.gz)  404 Not Found

Any ideas? If I use the third command will this solve the problem? Will it try to upgrade to Hardy Heron?


Why do you have debian listed entries in your sources? Are you using Ubuntu? Please post the result of ```
lsb_release -a
```

In any case, the third command will not upgrade your system to Hardy or any other distribution. All it does is upgrade any packages that are _already_ installed on your system, if a newer version is available.

To upgrade to a new version, you have to use update-manager.

---

### Post by HughReid on 2008-11-22
Can't remember why I have debian sources. Must have been required by some software I wanted. 
I thought Ubuntu is based on Debian, so why does it make a difference?
lsb_realease - gives
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy

I'll have a bash at sudo apt-get update and let you know

---

### Post by HughReid on 2008-11-22
No luck with that either as I get the same response through the terminal:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb)  Size mismatch
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb)  Size mismatch
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb)  Size mismatch
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-gui_2.7.7.dfsg.1-0ubuntu5.1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-gui_2.7.7.dfsg.1-0ubuntu5.1_all.deb)  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

This not surprising as I imagine "Update Manager" is just a wrapper for apt-get.
When it says "maybe run update or try with --fix-missing" does that mean apt-get --fix-missing as a single command?

---

### Post by HughReid on 2008-11-22
Seem to have solved the problem. I noticed the links in my reply above are active so I clicked on each in turn. This fired up gebi package manager in whose dialogue I clicked OK. It downloaded the files and then popped up a dialogue to the effect that the same file was available from the software channel and recommending I should use that. I ignored the recommendation as clearly the software channels were causing the error messages. So I installed each using the links and gebi and that seems to have my system up to date.

---


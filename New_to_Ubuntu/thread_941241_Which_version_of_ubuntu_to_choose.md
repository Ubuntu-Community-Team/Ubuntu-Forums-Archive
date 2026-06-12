---
title: "Which version of ubuntu to choose?"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by Kris2456 on 2008-10-07
Hi.

I have an old-ish PC (1.5Ghz, 512Mb RAM, 40GB HDD) that i would like to use as a home server. It's uses would be:

[LIST]
[*]Media Server for PS3
[*]Sharing files around the network
[*]Hosting the odd game of counter-strike
[*]Possibly hosting a small website (hobby only)
[/LIST]

I have the choice between keeping Windows XP, or going for Linux. I am leaning more towards Linux since i have tried it at work, and really want to learn more. However, I am also unsure what version of Ubuntu to get.

It would seem that the logical choice would be the "Server Edition", however from what i understand it has no GUI. While the server would be remotely administered, i am still a bit worried about letting go of a GUI (at least for setup).

I guess my question is, for what i am doing, is the server version neccesary, or can i go with the normal version?

---

### Post by lisati on 2008-10-07
Your system specs look as if they'll be able to cope with Ubuntu.

If you choose the "Desktop" version, you can add utilities useful for running a server later.
Similarly, if you choose the "Server" version, you can add a GUI afterwards.

From what I understand of what I've read in these forums, it might be easier to install the server version, and then add a GUI.

---

### Post by Tatty on 2008-10-07
The server version is not nessesary.  There are a few small tweaks to its performance, but i do not think these will really affect your purposes for it either way.

The desktop and server editions have the same repos attached to them, they both just come with different default packages installed.

I would recommend you just install the desktop edition for now.  However if you decide to use the server edition, a lightweight gui can be installed easily:
```
sudo apt-get install xubuntu-desktop
```

or if you decide you want the full ubuntu desktop:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by Kris2456 on 2008-10-07
Ok. I thought that the server version may be radically different to the desktop version.

I guess i will go with the desktop version, and install all of the stuff I need.

Out of interest, is it possible in Linux to remote desktop to the server, or is it only possible to SSH?

---

### Post by Therion on 2008-10-07
> **Tatty said:**
> I would recommend you just install the desktop edition for now.
I would have to agree. 

Being brand new to Ubuntu I'd suggest you start off with the desktop version to get your feet wet.  The performance dif isn't going to be noticeable except, most likely, on some synthetic benchmark.

---

### Post by rlogan on 2008-10-07
You could use the server version and install a desktop as well, i guess it is feasible. I did this with the xfce desktop, which is what Xubuntu uses. 

I have effectively done what you are doing at home, My machines are newer, but still not super fast and I am using Ubuntu 8.04. The slowest machine is a P4 3.2Ghz 2.5Gb ram and has 160gb drive which is the document and print server, the other machine performing most of the media server functions is a Dual Core Celeron 1.6Ghz, 2gb ram and 3 hds with total storage of 660Gb. 

Hope this helps

---


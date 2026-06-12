---
title: "Installing Update Problem"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by bern1939 on 2008-05-09
Using Ubuntu 7.10

Installation of Printing updates a few days ago failed to complete.
I am now told to run 'dpkg --configure -a' because the download was interrupted.
When I do that I get the following:

bernard@bernard-desktop:~$ sudo dpkg --configure -a

[sudo] password for bernard:

dpkg: failed to write status record about `kgpg' to `/var/lib/dpkg/status': No space left on device

bernard@bernard-desktop:~$ 


Now my print function has become corrupted!!

Can you help please


Bernard

---

### Post by takuhii on 2008-05-09
I may not be much help, but this sounds as though you have run out of space on your HDD or storage device... At least that's what ubuntu thinks anyway...

---

### Post by kesman on 2008-05-09
Try running
```

sudo apt-get autoclean
sudo apt-get autoremove

```
and report back if they help.

---

### Post by bern1939 on 2008-05-09
Thanks for your replies but.....
Oh dear… from my previous post a short time ago things have got worse.
I cannot get into Ubuntu now.
I got it to close down and auto restart with lots of graphical stuff flying through what I take to be a recovery process. But then everything comes to a full stop with the following message which now remains on my screen.

Gzip: /var/log/dmesg.0.gz: No space left on device
Mv: cannot stat `/var/log/ /dmesg.0.gz`: No such file or directory
root@bernard-desktop: ~# Bernard 

Where can I go from here?……am I destroyed?

All this seems to have arisen from a simple interrupt in inputting some
Upgrades for printing!!

Please tell me that I have not lost my entire system and work.


Bernard

---

### Post by takuhii on 2008-05-19
I had some hiccups with SUDO APT-GET AUTOREMOVE when I first started, it basically wiped out a load of important stuff Ubuntu was actually using at the time, I STILL to this day haven't figured out why...

---


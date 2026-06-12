---
title: "turn off button doesn't shutdown"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by GaussianMonk on 2008-05-21
For some reason the "Turn off" and "Restart" options in my K-menu don't really work. When I click on them the computer acts like it will shut down and the screen goes black, but the system doesn't actually power off unless I hit the power button on my laptop after the screen goes blank. 

Anyone know what is going wrong or have a fix?

Btw, running Kubuntu 8.04.

---

### Post by jamieh on 2008-05-21
I used to have the same problem, but one morning it magically fixed itself.

Weird...

:)

---

### Post by jimrz on 2008-05-21
> **GaussianMonk said:**
> For some reason the "Turn off" and "Restart" options in my K-menu don't really work. When I click on them the computer acts like it will shut down and the screen goes black, but the system doesn't actually power off unless I hit the power button on my laptop after the screen goes blank. 

Anyone know what is going wrong or have a fix?

Btw, running Kubuntu 8.04.

please list the specs on your laptop and also what is the date of your BIOS (this can cause this issue if date is < yr 2000, but is easily rectified)

---

### Post by GaussianMonk on 2008-05-22
It's a dell Inspiron 6400
1.8 MHz Centrino duo
1 gig ram
ATI Radeon Mobility X1400

I got it about 2 years ago, so I'm going to assume the BIOS is >2000. Shutdown worked fine with Kubuntu Gutsy.

---

### Post by stego_s_aurus on 2008-05-26
BINGO!!! ATi CARD + KubuNTU!!!

I just spent all bloody weekend looking for this problem, and Found it!!

[https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/181343/comments/27](https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/181343/comments/27)

Short answer:

1) BACKUP the /etc/ati/authatieventsd.sh file:

  sudo cp /etc/ati/authatieventsd.sh /etc/ati/authatieventsd.sh.old

2) EDIT the /etc/ati/authatieventsd.sh file

3) FIND the entry that reads:

  XDM_AUTH_MASK=/var/lib/xdm/authdir/authfiles/A$1*

4) REPLACE this line with:

  XDM_AUTH_MASK=/var/run/xauth/A$1*

5) because the above command only works After the system is restarted once, shut down your computer safely with:

  sudo shutdown -r now

6) Start your computer up, test that the above edit worked by clicking Shutdown from KDE.

It sure worked on My Girlfriends computer (Gateway MA3 widescreen laptop with ATI Radeon Xpress 200M just installed with 8.04 Hardy), I hope it works for other people!!!

YAY!!

---


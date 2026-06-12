---
title: "Kubuntu Shutdown Black Screen hang ATI SOLVED"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by stego_s_aurus on 2008-05-26
BINGO!!! ATI VIDEO CARD + KUBUNTU = SHUTDOWN HANG!!!

I just spent all bloody weekend looking for this problem, and Found it!!

[https://bugs.launchpad.net/ubuntu/+s...43/comments/27](https://bugs.launchpad.net/ubuntu/+s...43/comments/27)

Short answer:

1) BACKUP the /etc/ati/authatieventsd.sh file:

sudo cp /etc/ati/authatieventsd.sh /etc/ati/authatieventsd.sh.old

2) EDIT the /etc/ati/authatieventsd.sh file

sudo (use_your_favorite_editor_command) /etc/ati/authatieventsd.sh

3) FIND the entry that reads:

XDM_AUTH_MASK=/var/lib/xdm/authdir/authfiles/A$1*

4) REPLACE this line with:

XDM_AUTH_MASK=/var/run/xauth/A$1*

5) because the above command only works After the system is restarted once, shut down your computer safely with:

sudo shutdown -r now

6) Start your computer up, test that the above edit worked by clicking Shutdown from KDE.

It sure worked on My Girlfriends computer (Gateway MA3 widescreen laptop with ATI Radeon Xpress 200M just installed with 8.04 Hardy), I hope it works for other people!!!

---


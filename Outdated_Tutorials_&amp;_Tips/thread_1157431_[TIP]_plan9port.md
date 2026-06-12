---
title: "[TIP] plan9port"
date: 2009-05-12
forum: Outdated Tutorials &amp; Tips
---

### Post by mmix on 2009-05-12
1. install xterm and xorg-dev

2. Download plan9port
[http://swtch.com/plan9port/](http://swtch.com/plan9port/)

3. extract plan9port
sudo mv plan9 /opt

4. install
cd /opt/plan9
./INSTALL

5. add below 2 lines to /etc/profile
PLAN9=/opt/plan9 export PLAN9
PATH=$PATH:$PLAN9/bin export PATH

6. profile update
source /etc/profile

7. make .xsession in your $HOME
#!/bin/sh
exec rio -term xterm

8. before gdm login: 
option -> select session -> choose Xclient script

---

### Post by jpeddicord on 2009-05-13
Thank you for your tutorials & tips submission. I've approved your post with the following change:

Plan9 was being copied to /home, which is not a great idea since /home is reserved for user home folders. I've changed this to /opt, a directory for alternative (optional) software installations.

Thanks! :)

---

### Post by underspecified on 2009-09-07
Greetings,

I maintain debs of plan9ports here: [http://cl.naist.jp/~eric-n/ubuntu-nlp/dists/intrepid/plan9/](http://cl.naist.jp/~eric-n/ubuntu-nlp/dists/intrepid/plan9/)

Jaunty packages are on the way.

--underspecified

---

### Post by staalmannen on 2010-07-28
Sorry for reviving a long-dead thread (let's just call it "graverobbing from outer space" shall we? ;) )

I got inspired by this post and made an ubuntu live CD with plan9port as default user interface. It is still a work in progress, and I hope to reduce its size further by removing redundant parts etc...

Anyone interested can access it at:

[http://dl.suckless.org/9buntu/](http://dl.suckless.org/9buntu/)

If anyone knows of a recent up-to date (and preferrably reasonably "official") apt repository for plan9port, that would be great since this now has been installed from the tarball from swtch.com. Having a pre-built package installed from a repository would save lots of space from all the dependencies that were pulled in by xorg-dev, and would make it easier for curious users to keep their system updated.

[IMG]http://dl.suckless.org/9buntu/9buntu-screendump.png[/IMG]

some overview:
Ubuntu version: 10.04 (built from minimal debootstrap)
Default shell: rc (ofcourse!)
Default DM: slim
Default WM: Rio (ofcourse!)
Default browser: uzbl

EDIT: Username=ubuntu, password is blank for live CD.
I have still not figured out a "plan9:ish" way to get installer and partitioner to look nice so at the moment if anyone want to install, I suppose copying to a pre-partitioned HDD and chroot from there is the only solution.

Might have to add some more symlinks in /usr/local/GNU/sbin for the root stuff (passwd) for example, which do not work using the plan9port binaries, which as much as possible have been set as default by putting /usr/local/plan9/bin first in the PATH

---

### Post by afrodeity on 2011-02-18
very cool

---


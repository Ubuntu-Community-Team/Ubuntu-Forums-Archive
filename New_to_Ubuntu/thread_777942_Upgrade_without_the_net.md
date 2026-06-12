---
title: "Upgrade without the net"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by mac9416 on 2008-05-01
Hello!

I would like to upgrade the base operating system of my Ubuntu 
Ulitmate install off of a DVD that I will burn from a Windoze computer. Is this possible? Remotely possible? I mean, I don't mind working for it.
Thanks in advance!

-mac

PS: I'm not sure what to think of the prefix thing. I have Ultimate Edition and the splash screen that I see at startup says KUbuntu. A little help?

---

### Post by jrlii on 2008-05-01
It's not really a problem: 

1. Download the ALTERNATE (NOT the regular Desktop: it won't work for an upgrade!) ISO disk image and burn it to disk.

2. Boot the disk, run the disk integrity checker to make sure the disk is good (not required, but it is a pain to have an install crash on account of a bad disk!)

3. Boot Gutsy and start the update manager. It should detect the presence of the distribution upgrade disk and then install the upgrade. . . Sometimes it will detect the presence of the distribution upgrade and ask to start on it's own. . .

---

### Post by mac9416 on 2008-05-01
Thanks Jerry-Lee ;)That sounds great. However you'll have to refresh my memory. Is 7.10 Gutsy or is 8.04? I'm running 7.10.
That's one of those "details" I forgot in the first post. :lol:

Oh yes! I completely forgot. I also want to make the upgrade work from a script. After studying the apt-get man page under "Upgrade" I found that apt-get uses a "sources" file (forgot where it was loctated) to decide what to upgrade. I wonder if I could edit that to upgrade off of a disc from the script.

---


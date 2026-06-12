---
title: "how to start Pure-ftpd with -w switch"
date: 2012-02-26
forum: New to Ubuntu
---

### Post by jlivin25 on 2012-02-26
Hello All

First off i am a Ununtu Noob (big time), i understand the concept of programming, i'm just simply no good at it. Long time Windows user so going back to a command line style takes a change of thinking. To help me get used to this i use Ubuntu 11.04 64-bit on a Acer Revo 3700, which acts as my media by running XBMC (eden beta 3). I also use transmission.

Now I've experimented with different Ubuntu ftp servers and settled on pure-ftpd (because i could use pure-admin as a GUI for users)

My problem is that for speed of use i want to be able to do site-to-site (FXP) transfers from the Ubuntu box to my NAS drive.

Now using google i understand i need to stop the pure-ftpd daemon and restart it with the -w switch (i tried to write my own script but got lost).

I have tried the commands

sudo service pure-ftpd stop
sudo pure-ftpd -w 

and it works, but want i cant do is make pure-ftpd do this (pure-ftpd -w) as standard on boot.

Please help what do i need to do?

Thanks

James

(by the way ubuntu has helped me make a kick-*** HTPC so i'm in love :) )

---


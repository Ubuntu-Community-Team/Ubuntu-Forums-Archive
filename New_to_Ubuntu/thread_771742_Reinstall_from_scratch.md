---
title: "Reinstall from scratch?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by alexjohnc3 on 2008-04-27
Ubuntu Hardy Heron has been a real disappointment for me, and I've been have tons of issues with it. I think I should just copy the data on my desktop and start over again with a fresh install of Hardy Heron, meaning I would lose all of my settings, applications, etc. I don't really want to do that, but I'm getting really frustrated with the sound not working randomly, not being able to access Synaptic, Movie Player and VLC not working, etc. Is this a good idea or not?

---

### Post by tamoneya on 2008-04-27
it seems to me like you are going from hardy heron to hardy heron and not really changing anything.  One thing i would recommend however is that you make /home its own partition.  That way if you ever reinstall after this you can then just install over the / partition and just remount /home since it wasnt messed with.

---

### Post by Archmage on 2008-04-27
To be more exactly: If you want to install from scratch, but don't want to lose your application settings, you need to backup your whole /home-partition with all the hidden files. And the next time you should have a separate /home-partition to make things easier.

---

### Post by Solrac924 on 2008-04-27
was this an install or an upgrade?

---

### Post by alexjohnc3 on 2008-04-28
> **Solrac924 said:**
> was this an install or an upgrade?
I upgraded from 7.10 to 8.04 through the Update Manager.

Also, would my applications and settings all be compatible with a fresh install of Ubuntu 8.04 even though they're from 7.10?

---

### Post by zvacet on 2008-04-28
[Here]("http://psychocats.s465.sureserver.com/ubuntu/separatehome") is guide how to make separate home partition.I kow this is not popular thing to say,but if you have problems with Hardy wait for couple weeks and install it then.

---

### Post by mac71 on 2008-04-28
I frequently back up my entire system to dvd using remastersys.You can also pick and choose what you want to leave out. You can get the repos. etc from here:
[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by MrWES on 2008-04-28
Gusty was my first install since running Slackware years ago. Anyhow, I read a very good installation howto, that recommeneded have separate partitions: one for / (root), one for /home and one for swap. This way when you want to do a reinstall you blow away root without loosing everything else. Also, I found some good youtube videos on how to do this.

Bill

---

### Post by Solrac924 on 2008-05-03
yeah, i'd recommend to make a /home partition & do a fresh install on the rest of the space. 
i got mine working perfect with a fresh install of Gutsy, then with an upgrade to Hardy. =D>
the installation of Hardy with an error-free CD didn't work for me originally.

---

### Post by raoulteeuwen on 2008-05-04
Hi.

I upgraded from Gutsy to Haron. I'm on a laptop with Ati Mobility Radeon. I've run into seom problems with graphics. I was running Gutsy with Compiz & Cairo Dock, being very happy with it. I was unable to get compiz and Cairo running on Hardy. I'm now at the point x won't even start anymore :-(. So i would like to reinstall Gutsy or Hardy. The problem:the DVD-drive of my laptop is broke and i don't have a 4GB USB-stick to install from. So is it possible to:

- load XP and install Hardy somehow (like download iso, and have it install on the right partitions (overwrite current screwed up Ubuntu config)?
- load Ubuntu (no X) and give some command to have Hardy reinstall completely (and hope that helps)?
- load either XP or Ubuntu (without X) and have it connect to a PC on my network where the Hardy (or Gutsy) ISO resides and install over the network
- force current Hardy to think it is still Gutsy and do an 'upgrade' to Hardy (basically reinstall)
- other option?

Thanks! (i wish i had waited with upgrading to Hardy :-( )

---


---
title: "ubuntu freezes on resart"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by Yugoo on 2008-11-28
Hardy is great, very intuitive. Just one problem I haven't been able to solve on my own so far. If I attempt to restart the machine it freezes on the shutdown screen and hangs with the Ubuntu logo and sliding bar screen. I then have to do a hard restart (my poor drives)

I'm able to shut down or log off with no problem, just the restart is causing a problem.

I'm running Hardy on a Dell Dimension 9200 with an Intel chip. I use a wireless keyboard and mouse and have a raid 0 array mounted in the file system so I can access my windows folders for music and pictures.

Can anyone help?

---

### Post by Michael.Godawski on 2008-11-28
Is there something useful in the System Logs? 
I mean some errors or warnings at the time of the shutdown?
System > Administration > System Logs

---

### Post by Yugoo on 2008-11-28
The restart appears to be going normally until it hangs, so no obvious errors when it begins to shut down... I'll check the logs when I get home this evening though and hopefully be able to provide a bit more info.

---

### Post by Yugoo on 2008-11-28
Hmm, huge amount of information in the logs and I'm not sure what I'm looking for. I picked something to look at below but not sure where to start really

Nov 28 20:05:07 guy-linux kernel: [   25.891549] attempt to access beyond end of device
Nov 28 20:05:07 guy-linux kernel: [   25.891551] sdb: rw=0, want=618663138, limit=312500000

---


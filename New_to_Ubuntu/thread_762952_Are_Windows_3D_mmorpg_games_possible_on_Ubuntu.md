---
title: "Are Windows 3D mmorpg games possible on Ubuntu?"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by rialto on 2008-04-22
I've been wondering if it is possible to play 3D mmorpg games on Ubuntu? Games like WoW and FFXI??? Maybe with parallels like VMware perhaps? Help me please =)

---

### Post by lswest on 2008-04-22
well, to the best of my knowledge, WoW works well via Wine (the site is [_here_]("www.winehq.org"))

---

### Post by Paqman on 2008-04-22
3D gaming isn't really possible on a Virtual Machine like VMWare. VM's don't yet emulate 3D graphics acceleration cards, and have pretty poor performance overall.

You might be able to run such games on Ubuntu using Wine, however it's far from guaranteed. Check the [Wine Database](http://appdb.winehq.org/) for more info on what will run under Wine.

The best option is to just use Windows for Windows games. A dual-boot is pretty easy to set up.

---

### Post by civic_si on 2008-04-22
I have run WoW under Wine. A while back I ran Beryl and it didnt work so well then but after I switched compiz it worked fine. The FPS were not the same as if I was in windows.

---

### Post by Mauler5858 on 2008-04-22
I run WoW under wine and it runs just about as well as under Winblows.  I dont know about ffxi, but i know another one that runs well is guild wars.  If you are planning to for voice chat using ventrilo you might have some difficulty.

---

### Post by justin whitaker on 2008-04-22
> **rialto said:**
> I've been wondering if it is possible to play 3D mmorpg games on Ubuntu? Games like WoW and FFXI??? Maybe with parallels like VMware perhaps? Help me please =)

World of Warcraft runs under Wine, Cedega, and CrossOver Office. So does Guild Wars, I believe. I have no idea if FFXI runs or not.

Virtualization does not work well for #D graphics.

---

### Post by rialto on 2008-04-22
looks like it might be possible.  I'll wait until 8.04 is finalized and update if FFXI will work with WINE and other programs.  Thanks for all the replies!

---

### Post by Ideastone on 2008-04-22
In the past I've had a lot of success running Cedega to get my windows games running properly. Luckily, a lot of the improvements that are made in Cedega make it into Wine, so I'm sure by now Wine works just as well.

---

### Post by Wazoot on 2008-04-22
Yeah from what ive heard Wine runs WoW pretty good in Ubuntu. Guild Wars i think will too. :KS

---

### Post by namegame on 2008-04-22
I would like to add that this is very hardware dependant, on my Vista partition I can run WoW at around 40 FPS, however, when trying to run it in Wine on Ubuntu, even with the openGL tweaks, I only get 1-5 FPS.

I have an integrated Intel graphics card.

---

### Post by rialto on 2008-04-22
I found this going through the WINE website

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2739](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2739)

Hopefully, this will still work through Ubuntu 8.04

---

### Post by Paqman on 2008-04-22
> **rialto said:**
> 
Hopefully, this will still work through Ubuntu 8.04

Er, that page says that FF XI definitely _doesn't_ work in Wine.

---

### Post by Raistlin355 on 2008-04-22
I have been playing WoW and Guild wars on my Ubuntu boxes for awhile with Wine.  I've even got the Ventrilo Client working, not working really well but working.  I did try to run Guild wars from the live cd of 8.04 and it ran again not really well but I don't think you will have any problems playing games like this with Wine under Ubuntu.

---

### Post by Ptero-4 on 2008-04-22
AFAIK. Parallels does do some 3D accel trick if you're running windoze as guest.

---

### Post by rialto on 2008-04-22
ffxi will not work and going through the "howto". I got to a halt and was unable to finish my install.  I'm wondering when it might be able to.

---

### Post by sjprice on 2008-04-22
Once I found out I could run WoW under WINE, I finally switched to linux last week and have not looked back. I am running 8.04 with a geforce 6600 card and no one would be able to tell the difference if I was on a ubuntu box or a windows box. I dont use voice chat so YMMV. A good guide is here: [http://www.fsckin.com/2007/12/20/how-to-run-world-of-warcraft-wow-in-linux-using-wine/](http://www.fsckin.com/2007/12/20/how-to-run-world-of-warcraft-wow-in-linux-using-wine/)

---

### Post by Xiong Chiamiov on 2008-04-22
With a few registry tweaks, Guild Wars runs just fine and dandy through Wine.  It's actually the only application I used (other than Winamp) that wasn't available on Linux.  The performance isn't quite as good, but I believe that's because I had my XP fine-tuned.  There was hardly any Windows left in it.

---

### Post by T-Virus on 2008-04-23
I had no luck running MU Online under Wine nor Cedega. Maybe anyone had a chance?

---


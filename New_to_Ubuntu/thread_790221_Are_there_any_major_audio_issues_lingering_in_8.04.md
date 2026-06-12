---
title: "Are there any major audio issues lingering in 8.04 right now?"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by diablo75 on 2008-05-11
Someone I know has just upgraded to 8.04 and are saying that sound is not very dependable (meaning it seems to work sometimes, and other times it's mute for apparently no reason and with no errors displayed).  There is only one sound card in the computer (no on-board sound).

Short of keeping a detailed record of events where sound is suddenly not working, are their any lingering issues where certain programs will produce sound sometimes, and then later, not produce?  I'm just trying to gather a little list of all the possibilities.

---

### Post by Joeb454 on 2008-05-11
I've never had any issues with my sound on 8.04 on either of the machines I installed it on.

Does the person have an onboard sound device (built in to the motherboard) or an add-in card (i.e. an X-Fi card etc.)

---

### Post by diablo75 on 2008-05-11
> **Joeb454 said:**
> Does the person have an onboard sound device (built in to the motherboard) or an add-in card (i.e. an X-Fi card etc.)

See first post.  ):P

---

### Post by Joeb454 on 2008-05-11
My mistake :D

Do they have the driver for the sound card installed?

---

### Post by diablo75 on 2008-05-11
Because they are getting sound some of the time, and because lspci shows their sound card as a "nVidia Corporation MCP51 High Definition (rev 2a)", I am assuming the driver is installed and working.... some of the time.

Part of me thinks this problem is associated with VMware.  They have been using it since before 8.04.  Is it possible that the VM they use is directing sound towards something other than Pulse, causing it to conflict with other applications that are also trying to send sound to a non-Pulse sound device?  Like ALSA?  

I just sent an e-mail requesting them to view their System>Preferences>Sound settings and to change everything in there to Pulse Audio as an experiment.  I've also asked them to open VMware, view their VM's sound device configuration and send me a screen shot so I can see what device it's directing sound towards.  I've also asked them to keep an detailed log of any further problems...

So... it'll probably be a while before I get a reply back to all of that...

What other odd ball possibilities might be out there?  I'm looking for any and all theories out there.

---

### Post by TopFan on 2008-05-11
8.04 has killed all sound on my Dell 1525. The only exception is if I use the search function in Firefox. If nothing is found I get a beep. That's the only sound I've had from Hardly Hero.

I've reported the bug, but there has been no software update to correct the problem.

I'm going back to 7.10 (for my laptop) and have just ordered a Mac for my desktop.

Ubuntu is great fun, but it's still an enthusiast / hobby OS. Until stuff 'just works' [as advertised] or is corrected PDQ via software update Ubuntu will remain in the realm of 'also ran'.

---

### Post by diablo75 on 2008-05-11
> **TopFan said:**
> 8.04 has killed all sound on my Dell 1525. The only exception is if I use the search function in Firefox. If nothing is found I get a beep. That's the only sound I've had from Hardly Hero.

I've reported the bug, but there has been no software update to correct the problem.

I'm going back to 7.10 (for my laptop) and have just ordered a Mac for my desktop.

Ubuntu is great fun, but it's still an enthusiast / hobby OS. Until stuff 'just works' [as advertised] or is corrected PDQ via software update Ubuntu will remain in the realm of 'also ran'.
Posts like this make me wish I would have started [this particular thread]("http://ubuntuforums.org/showthread.php?t=754125") sooner than I did.  I feel your pain, and have written some livid posts about how much more trouble than good I think Pulse has brought on.  But I can see it's potential... I just wish that potential would be realized more quickly with some patches, or at least some sort of announcement from Canonical about what they're doing to get this crap ironed out ASAP.  Because it seems like the biggest delay factor right now is finger pointing between devs.

---

### Post by goodmanbrown on 2008-05-11
My sound never stops completely, but I do have intermittent problems with it.  Since the upgrade to Hardy, listening to music through totem or amarok is mostly a miserable experience.  Anytime minimize a window, or click a link, or change virtual desktops, I get skips, scratches, and pauses.  But occasionally everything seems to work fine.

After poking around on launchpad, it seems possible that it is an issue with my soundcard, which is an Audiophile 2496.

---

### Post by jynyl on 2008-05-11
I was having trouble with Kubuntu 8.04, but resetting alsa-utils seems to have fixed it.
[http://ubuntuforums.org/showthread.php?t=782139]("http://ubuntuforums.org/showthread.php?t=782139")

---


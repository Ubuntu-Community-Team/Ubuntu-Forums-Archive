---
title: "How to fix my network connection"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by realist on 2008-11-17
My first post.  I am a complete newbie to Linux.  I did some searching, but didn't find an answer to my question.

Here's what happened:

I have been tinkering with Ubuntu 8.04 for a few weeks, and was thinking I would soon consider pulling the plug on Windows for good until this happened.

All I did was to install the "flashblocker" add-on to Firefox.  After I restarted Firefox, I couldn't connect to my network anymore (using an ethernet connection).  I tried a number of different websites, and could not connect.

I also tried installing one of the recommended Ubuntu upgrades, assuming this would point to Firefox as the cause, but I couldn't connect that way either.

I've pulled my hair out trying to fix this, but I'm completely baffled.  What did I do wrong?  Is Ubuntu potentially vulnerable to all Firefox add-ons?  Any suggestions on how I might fix this?

Thanks!

Edit:  Thanks for the quick replies.  I left out a step.  I should have added that, yes, I immediately tried removing the add-on and restarting Firefox without any success in solving the problem.

--------
Machine: P3/733, 512kb RAM, on-board ethernet
OS: Ubuntu 8.04 (no windows partition on this machine)

---

### Post by echo314 on 2008-11-17
Have you tried removing the add-on in question? I have never had problems with Fx addons. I don't know if the add-on was actually related, since Fx does not control your network. I could remove Fx, and still see other comps. Idk sorry if this was not helpful :(

---

### Post by mapes12 on 2008-11-17
> Is Ubuntu potentially vulnerable to all Firefox add-ons?No.

Does removing the "flashblocker" addon resolve the problem?

---

### Post by frankleeee on 2008-11-17
> **realist said:**
> My first post.  I am a complete newbie to Linux.  I did some searching, but didn't find an answer to my question.

Here's what happened:

I have been tinkering with Ubuntu 8.04 for a few weeks, and was thinking I would soon consider pulling the plug on Windows for good until this happened.

All I did was to install the "flashblocker" add-on to Firefox.  After I restarted Firefox, I couldn't connect to my network anymore (using an ethernet connection).  I tried a number of different websites, and could not connect.

I also tried installing one of the recommended Ubuntu upgrades, assuming this would point to Firefox as the cause, but I couldn't connect that way either.

I've pulled my hair out trying to fix this, but I'm completely baffled.  What did I do wrong?  Is Ubuntu potentially vulnerable to all Firefox add-ons?  Any suggestions on how I might fix this?

Thanks!

Edit:  Thanks for the quick replies.  I left out a step.  I should have added that, yes, I immediately tried removing the add-on and restarting Firefox without any success in solving the problem.

--------
Machine: P3/733, 512kb RAM, on-board ethernet
OS: Ubuntu 8.04 (no windows partition on this machine)

Have you tried a restart plugged in to etho.

---

### Post by realist on 2008-11-17
Sorry.  That's something else I should have also noted.  Yes.  I did try rebooting the machine, but the problem persists.  (I'm accustomed to doing that a lot with Windows, so I tried it with Linux too.) :)

(Rebooted both plugged into network and unplugged.)

---

### Post by wylfing on 2008-11-17
A quick way to determine whether your problem is due to bad settings in Firefox is to wipe out your profile, so that Firefox creates a fresh one with default settings. Close Firefox then open a terminal and do this:
```
mv ~/.mozilla ~/.mozilla-old
```
Launch Firefox again and see if you can connect.

Edit: As a P.S., you will find that rebooting your computer generally does not solve Linux problems.

---

### Post by shredder12 on 2008-11-17
hey then i think you should first of all try to remove that add on and then reboot your system and try again.. well if you are not able to connect through firefox then are you able to ping any site..or not..
jst execute this command on your terminal..
```
ping www.google.com 
``` 
are you able to see any messages saying that packets sent are being received..
If this is happening then you are connected to internet but its jst that you are unable to access it through firefox..
well then you may try to reinstall firefox..
i think that will help..

---

### Post by wylfing on 2008-11-17
> **shredder12 said:**
> hey then i think you should first of all try to remove that add on and then reboot your system and try again

He did already say he tried to remove the add-on, and rebooting a Linux computer typically has little effect on its behavior.

However, the suggestion about running ping in a terminal is a good one. It will help determine whether the problem is with Firefox or the network connection in general.

---

### Post by realist on 2008-11-18
Thanks, everyone for your suggestions.

I got home and turned on my linux machine, prepared to follow your advice.  Lo and behold, the problem has resolved itself!  I guess it's another of those great mysteries.

I'll try re-installing the same add-on and see if the problem repeats itself.  (I'm guessing it won't.)

---


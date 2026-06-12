---
title: "having problems booting, please help!"
date: 2012-10-16
forum: New to Ubuntu
---

### Post by stottrupbailey on 2012-10-16
Hi, I am very new to Linux. I installed Ubuntu 12.04 this weekend and am having fun with it so far but have run into an issue already and need help. Sometimes when I turn on my computer the screen turns purple and nothing happens, it just stays that way. The ubuntu logo doesn't pop up like it usually does on start ups, just a purple screen. What I've done is just hold down the power button to turn off my laptop and then I turn it back on again. Every time it's worked the second time. I'm starting to worry about this and am wondering why it doesn't boot up properly a lot of times. I'm shutting down the computer fine, so that's not the issue. ?? Please help, thanks!

---

### Post by Linux_junkie on 2012-10-17
How have you installed Ubuntu? From liveCD/USB or Wubi. Also, are you duel-booting with Windows?
Without having full knowledge of your system it is difficult to find out what is wrong.  It could be the way the GRUB has been set up or that it could be trying to set up a piece of hardware during boot but it's failing.
A little more information would be useful, please.

---

### Post by bcbc on 2012-10-17
> **stottrupbailey said:**
> Hi, I am very new to Linux. I installed Ubuntu 12.04 this weekend and am having fun with it so far but have run into an issue already and need help. Sometimes when I turn on my computer the screen turns purple and nothing happens, it just stays that way. The ubuntu logo doesn't pop up like it usually does on start ups, just a purple screen. What I've done is just hold down the power button to turn off my laptop and then I turn it back on again. Every time it's worked the second time. I'm starting to worry about this and am wondering why it doesn't boot up properly a lot of times. I'm shutting down the computer fine, so that's not the issue. ?? Please help, thanks!

Never force shutdown your laptop. Use [Alt+SysRq R-E-I-S-U-B]("http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses") instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

As to your issue, it sounds like a graphics card problem. What card(s) do you have?

---

### Post by stottrupbailey on 2012-10-19
Hi, I talked to some computer people on campus and they agreed that it probably is a graphics card issue. I have an HP Pavilion g6 computer with: AMD A6-3420M APU with Radeon(tm) HD Graphics × 4 .

---

### Post by stottrupbailey on 2012-10-19
And thanks for letting me know about the force shutdown. When I  brought the laptop in to have the IT guys check it out they were force shutting it down like a million times so I wouldn't have guessed you weren't supposed to do that. I'm completely new to ubuntu, so I'm a little afraid to try fixing stuff on my own since I don't want to screw it up even more. I googled some and found that lots of other people with HP g6 laptops have had graphics issues with ubuntu but none of their issues were similar to mine so I never really found a solution.

---

### Post by bcbc on 2012-10-19
> **stottrupbailey said:**
> Hi, I talked to some computer people on campus and they agreed that it probably is a graphics card issue. I have an HP Pavilion g6 computer with: AMD A6-3420M APU with Radeon(tm) HD Graphics × 4 .

This appears to be a howto for this sort of graphics setup: [http://ubuntuforums.org/showthread.php?t=1942151](http://ubuntuforums.org/showthread.php?t=1942151)

I would review it and see if it solves your problem, and if not, post on that thread and you'll likely get better help! ;)

---


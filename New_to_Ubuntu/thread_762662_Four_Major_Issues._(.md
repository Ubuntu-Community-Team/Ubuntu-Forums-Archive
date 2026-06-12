---
title: "Four Major Issues. :("
date: 2008-04-22
forum: New to Ubuntu
---

### Post by adi116 on 2008-04-22
i've been using ubuntu 7.10 for a few months now... and lately i've had some really strange problems.

1) Pidgin Internet Messenger Crashes directly after i open it... it leaves a deadspace where it should have an icon in my top desktop panel that wont respond to any clicks, and the actual program never starts. if i try to open it again... it gives me the same problem again, leaving two deadspaces on my desktop panel. this has also extended to the power button in the panel, as it causes the button to respond very slowly - i only get my popup about 60 seconds later. same thing when i press the actual power button on my laptop. i've uninstalled and re-installed, but that hasn't helped. is there any way to get Pidgin to start working again? i dont want substitutes... they dont tend to be as good. but if it's the last option... then i guess i'll go for it.

2) my laptop (HP dv2000t - i can give more specs if necessary) tends to overheat when i'm using ubuntu, and automatically shuts off. is there any way to make the laptop cool down without having to shut off my computer... and if not, how can i be warned ahead of time, so i can shut it down manually and not have to go through a fsck? i installed xsensors, but all that happens when i open it is the window pops up and it's an empty window.

3) My computer will not suspend. if i click suspend, it just goes to the login screen that appears after you return from suspended state... it's like it skip the suspend process altogether. is there any way to get my computer to suspend again?

4) this one isn't a big issue, but sometimes, the audio just tends to die out on me. i'll be listening to music on imeem, and the music will just stop playing, even though it's on play.  this only seems to happen in flash players on the internet.

if i could get some troubleshooting help, i would be very happy. :) i am, though, quite a n00b.... so if you could please bear with me... i'd be extremely grateful.

---

### Post by MONODA on 2008-04-22
> 1) Pidgin Internet Messenger Crashes directly after i open it... it leaves a deadspace where it should have an icon in my top desktop panel that wont respond to any clicks, and the actual program never starts. if i try to open it again... it gives me the same problem again, leaving two deadspaces on my desktop panel. this has also extended to the power button in the panel, as it causes the button to respond very slowly - i only get my popup about 60 seconds later. same thing when i press the actual power button on my laptop. i've uninstalled and re-installed, but that hasn't helped. is there any way to get Pidgin to start working again? i dont want substitutes... they dont tend to be as good. but if it's the last option... then i guess i'll go for it.
go to your home folder and press ctrl+h, this will show the hidden files and folders, delete .purple, this should reset your pidgin settings

> 2) my laptop (HP dv2000t - i can give more specs if necessary) tends to overheat when i'm using ubuntu, and automatically shuts off. is there any way to make the laptop cool down without having to shut off my computer... and if not, how can i be warned ahead of time, so i can shut it down manually and not have to go through a fsck? i installed xsensors, but all that happens when i open it is the window pops up and it's an empty window.
do you have visual effects enabled? if so, turn them off and see if it still happens. did this happen in windows also?

> 3) My computer will not suspend. if i click suspend, it just goes to the login screen that appears after you return from suspended state... it's like it skip the suspend process altogether. is there any way to get my computer to suspend again?
did suspend ever work, if so ,when did it stop?

> 4) this one isn't a big issue, but sometimes, the audio just tends to die out on me. i'll be listening to music on imeem, and the music will just stop playing, even though it's on play. this only seems to happen in flash players on the internet.
this may be a conflict between visual effects and flash.

---

### Post by adi116 on 2008-04-22
1) FIXED. thank you!
2) yeah, i have visual effects enabled. (i'm assuming you mean all the animations and what not in advanced desktop settings) it only seems to happen when i have a few progs running at the same time, ie. rhythmbox, skype, mednafen, firefox... and they're all active. it never happened in windows, no matter how many progs i had open. i'll shut them off, see if it works. :)
3) it stopped working about a month ago. while it DID work, it would sometimes freeze up when i tried to log back in... it would just give me a blank screen. that was only occasionally, though.
4) turned off visual effects, let's see if things work for the better! :D

thank you so much for all you help so far. :)

---

### Post by MONODA on 2008-04-22
I have an hp dv6000 and have had similar problems with desktop effects so that may be it, hopefully hardy will fix these problems :D. Do you remember doing anything before suspend stopped working? and does hibernate work?

---

### Post by billgoldberg on 2008-04-22
> **adi116 said:**
> i've been using ubuntu 7.10 for a few months now... and lately i've had some really strange problems.

1) Pidgin Internet Messenger Crashes directly after i open it... it leaves a deadspace where it should have an icon in my top desktop panel that wont respond to any clicks, and the actual program never starts. if i try to open it again... it gives me the same problem again, leaving two deadspaces on my desktop panel. this has also extended to the power button in the panel, as it causes the button to respond very slowly - i only get my popup about 60 seconds later. same thing when i press the actual power button on my laptop. i've uninstalled and re-installed, but that hasn't helped. is there any way to get Pidgin to start working again? i dont want substitutes... they dont tend to be as good. but if it's the last option... then i guess i'll go for it.

2) my laptop (HP dv2000t - i can give more specs if necessary) tends to overheat when i'm using ubuntu, and automatically shuts off. is there any way to make the laptop cool down without having to shut off my computer... and if not, how can i be warned ahead of time, so i can shut it down manually and not have to go through a fsck? i installed xsensors, but all that happens when i open it is the window pops up and it's an empty window.

3) My computer will not suspend. if i click suspend, it just goes to the login screen that appears after you return from suspended state... it's like it skip the suspend process altogether. is there any way to get my computer to suspend again?

4) this one isn't a big issue, but sometimes, the audio just tends to die out on me. i'll be listening to music on imeem, and the music will just stop playing, even though it's on play.  this only seems to happen in flash players on the internet.

if i could get some troubleshooting help, i would be very happy. :) i am, though, quite a n00b.... so if you could please bear with me... i'd be extremely grateful.

1. **Completely** remove pidgin in synaptic package manager (system -> administration) and reinstall it.
If you only use the msn network (like so many of us) try emesene (google for the .deb), it's great.

2. I had the same problem with my pavilion dv4000 (with ubuntu and xp)  It shuts down because the bios tells the pc to turn of when it get to warm (this is good or the laptop would be toast). Bring it to the shop and fix it, this is **not** an ubuntu problem, it's the hardware. You could try to elevate the laptop a bit when using it. That will help. Also don't run compiz fusion and unneeded processes.

3. I never use that feature but I heard hardy heron (the new version of ubuntu that comes out on the 24th) has better suspend support.

4. It's a flash problem. Make sure you have the latest version from the repo's. Besides that, there isn't much you can do. 

Besides the obvious thing to do: download them.

I hope this helped you a bit.

---

### Post by adi116 on 2008-04-22
i dont think i did anything... and i haven't tried hibernate.

but yeah, hopefully hardy takes care of the power management issue. :)

---


---
title: "firefox flash and no other sound"
date: 2008-04-21
forum: New to Ubuntu
---

### Post by medivh on 2008-04-21
When i open a website with flash content it sucks the cpu so much(~%40 of Intel C2D 2.0Ghz) and no other program can play sounds. But rhythmbox and moviplayer can work and sound at the same time.

---

### Post by Incredulous Moose on 2008-04-21
[http://ubuntuforums.org/showthread.php?t=279990](http://ubuntuforums.org/showthread.php?t=279990)

---

### Post by medivh on 2008-04-21
where should i exactly look at in this post you send?
i already have flash 9.0.124 and that posts describes how to install flash 9 beta. do i miss something?

---

### Post by tango_ninja on 2008-04-21
what version of firefox are you running? I've heard those with 3 experience problems with flash

---

### Post by medivh on 2008-04-21
i am using a clean install of hardy which means ff 3.0b5
i would prefer ff2 but when i try to install 2 and remove 3 then everything gets worse.a few updates before flash could sound simultaneously with other apps but i was experiencing too many firefox crashes because of flash. Now crashes are gone but here is the sound problem.only 2 days left before release and there are many problems i think.

---

### Post by Incredulous Moose on 2008-04-21
> **medivh said:**
> where should i exactly look at in this post you send?
i already have flash 9.0.124 and that posts describes how to install flash 9 beta. do i miss something?

My apologies.

---

### Post by medivh on 2008-04-21
> **Incredulous Moose said:**
> My apologies.

No problem. It was a 16 pages post and i thought maybe you were talking about some information deep inside there.

---

### Post by medivh on 2008-04-22
still waiting for a solution

---

### Post by Nevyn on 2008-04-22
Are you using the 32 or 64 bit version of FF? 
(Look in the Help -> About Mozilla Firefox. Mine says "Mozilla/5.0 (X11; U; Linux x86_64;" = I use the 64 bit version).

I solved my flash problem by installing the 32 bit version of FF. If you also have the 64 bit version I'll find the how-to for doing that.

---

### Post by livingtarget on 2008-04-22
Make sure you are running the latest flash plugin even though you say you do, checking the url: about:plugins in firefox will tell you more.

Another thing to try is killing pulseaudio, close firefox and try again.

Basically a "sudo killall pulseaudio" should do the trick or disable the sound daemon somewhere in preferences -> sound settings. Basically that's what restored flash sound for me, probably not the problem you have.

The high CPU is unfortunate but does happen quite a bit with flash on linux I think.

---

### Post by Greg T. on 2008-04-22
The changeover to Pulseaudio in Hardy has resulted in a bug with Flash. In particular, using the libflashsupport package can result in a lot of crashes, so it has been made into an optional package when the flashplugin-nonfree is installed. 

Unfortuantely, a side effect of making libflashsupport an optional package is the problem you're describing; Flash can commandeer the sound card and not let other apps use it. 

A fix for this being worked on. The gory details are in [bug #192888]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/192888").

---


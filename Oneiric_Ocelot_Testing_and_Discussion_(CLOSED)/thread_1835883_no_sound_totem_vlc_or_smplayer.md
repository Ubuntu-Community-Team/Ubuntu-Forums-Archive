---
title: "no sound totem vlc or smplayer"
date: 2011-08-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rbrick49 on 2011-08-30
I have no sound on any of my video players installed on oneiric .vlc smplayer or totem will play video or dvd from disc but no sound .I have tried these discs on fedora15 and they all work any ideas 
regards Ron
I have installed all the extra codecs

---

### Post by cariboo on 2011-08-30
I changed the thread to unsolved, as you won't get any replies if it is marked solved.

---

### Post by kbaumen on 2011-08-30
Or if the OP *did* manage to solve the problem, then he/she should post some details because other people looking for a solution to a similar problem might stumble upon this thread.

---

### Post by cariboo on 2011-08-30
> **kbaumen said:**
> Or if the OP *did* manage to solve the problem, then he/she should post some details because other people looking for a solution to a similar problem might stumble upon this thread.

The op usually does post if he found a solution.

---

### Post by hyperdude111 on 2011-08-30
This is common in 11.10, If one application has made a sound output in it's current process then it has to be closed before another application can also make a sound. I personally find it very annoying.

Eg. If you're playing a video on youtube in chrome banshee will refuse to play a song until chrome is closed. 

It might be by design but I hope it's a bug !

---

### Post by kbaumen on 2011-08-30
> **hyperdude111 said:**
> This is common in 11.10, If one application has made a sound output in it's current process then it has to be closed before another application can also make a sound. I personally find it very annoying.
 
Eg. If you're playing a video on youtube in chrome banshee will refuse to play a song until chrome is closed. 
 
It might be by design but I hope it's a bug !
 
Seriously? I remember this being an issue when I was in primary school and running win98.
 
I googled this a bit and the only thing I could find that is even remotely relevant was [http://osdir.com/ml/ubuntu-bugs/2011-08/msg05691.html](http://osdir.com/ml/ubuntu-bugs/2011-08/msg05691.html)

---

### Post by buzzmandt on 2011-08-30
wow, talk about a regression, all the way back to oss.... ugh lol

---

### Post by rbrick49 on 2011-08-30
heres how I solved the problem I uninstalled vlc,smplayer and totem I had installed vlc and smplayer via apt-get I did a reinstall via synaptic and they all worked fine

---

### Post by rbrick49 on 2011-08-30
> **cariboo907 said:**
> I changed the thread to unsolved, as you won't get any replies if it is marked solved.
thanks mate me thinks my problem was a broken codec via apt-get but not sure
regards Ron

---

### Post by apollothethird on 2011-08-30
> **hyperdude111 said:**
> This is common in 11.10, If one application has made a sound output in it's current process then it has to be closed before another application can also make a sound. I personally find it very annoying.

Eg. If you're playing a video on youtube in chrome banshee will refuse to play a song until chrome is closed. 

It might be by design but I hope it's a bug !

You're probably having that problem in 11.10 because of the testing that is going on with it.  I never experienced that problem in 10.10 or 11.04.  I just when to my music directory, right clicked on an mp3 file three times (three different music apps)  while a youtube video is playing.  I can distinctly hear the audio of all four applications (the three music apps installed plus the youtube video).  If I had more music apps installed I would have added more to the mix.  So Ubuntu has this ability.  I'm sure once 11.10 is released it'll retain this ability.

> **kbaumen said:**
> Seriously? I remember this being an issue when I was in primary school and running win98.
 
I googled this a bit and the only thing I could find that is even remotely relevant was [http://osdir.com/ml/ubuntu-bugs/2011-08/msg05691.html](http://osdir.com/ml/ubuntu-bugs/2011-08/msg05691.html)

It isn't an issue with the two current releases of Ubuntu.  I started with version 10.10, so I can't speak of the previous versions.  I'd be surprised if they didn't work equally well... and again, I'm sure version 11.10 will work just as well when it's released.

> **rbrick49 said:**
> heres how I solved the problem I uninstalled  vlc,smplayer and totem I had installed vlc and smplayer via apt-get I  did a reinstall via synaptic and they all worked fine

Glad to see you got your issue resolved.  I was going to suggest the step you performed.

You might consider marking the problem solved so that others having a similar problem can easier find this solution.

I thought about suggesting a solution for Hyperdude111, but there's a chance there might be some experimental conditions in the build he's using.  I'm glad we have testers out there to put the OS through lots of test before its released.  You're doing a good thing, Hyperdude111.  Make sure you report this current unique condition to the development team.  Hopefully you have a production computer with a released version so that you can at least have the normal stability when you need it.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by kbaumen on 2011-08-31
> **apollothethird said:**
> 
[..]

It isn't an issue with the two current releases of Ubuntu.  I started with version 10.10, so I can't speak of the previous versions.  I'd be surprised if they didn't work equally well... and again, I'm sure version 11.10 will work just as well when it's released.

[..]


I was surprised because I hadn't heard about anyone having such a problem in Ubuntu. Then again, I have never been involved with testing.

---


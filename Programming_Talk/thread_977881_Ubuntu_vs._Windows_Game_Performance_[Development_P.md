---
title: "Ubuntu vs. Windows Game Performance [Development Perspective]"
date: 2008-11-10
forum: Programming Talk
---

### Post by signal_ on 2008-11-10
Hi.  I use Code::Blocks IDE and OpenGL with SDL on both Ubuntu 8.10 and WindowsXP latest updates.  I have my laptop setup for dual boot.  I built my game in both Ubuntu and WindowsXP using the same header and cpp files.

As far as I know, all other things are equal.  Here is the result: the WindowsXP system runs the game better performance wise.  I tried to adjust the settings for things like graphics card and compiler options, etc., to be the same from Ubuntu to WindowsXP; I tried to make everything as similar as possible in order to achieve similar performance results.

Why does the Windows version outperform the Ubuntu version?  Any ideas?  Thanks for any replies.

---

### Post by LaRoza on 2008-11-10
> **signal_ said:**
> 
Why does the Windows version outperform the Ubuntu version?  Any ideas?  Thanks for any replies.

Possibly hardware related. Just because a driver exists, even official, doesn't mean it is the same quality.

For a truer test, try Windows XP fresh install, nothing installed after, and a default Ubuntu.

---

### Post by signal_ on 2008-11-10
Thanks for the reply, LaRoza.

> Possibly hardware related. Just because a driver exists, even official, doesn't mean it is the same quality.

I am definitely not using an official driver.  I am using an ATI/AMD proprietary FGLRX graphics driver in order to have 3D-acceleration enabled.

I think, however, it may be an issue with cpu usage.  For my game, I have an entity system for the entities or game objects in the game.  As the number of objects increase the cpu is taxed on both Ubuntu and WindowsXP, but the Ubuntu system forces the game to run more choppily.  This choppiness could also be described as stuutter.  

For example, under Ubuntu with 1000 entities it will still run at ~60fps; however, periodically the fps will drop to ~50-something fps temporarily, thus forcing the user to experience a "stutter" or "glitch".  Under WindowsXP there is no glitching only smooth scrolling and constant frame rate.

> For a truer test, try Windows XP fresh install, nothing installed after, and a default Ubuntu. 

Yes, I could do this.  However, I am not really interested in a true test.  I am mostly interested in squeezing out the best performance for my game since I need that performance for testing, etc.  With that in mind I am searching for a way to run my game with a performance quality similar to that of the quality which WindowsXP provides.

I have yet to test it under Wine, but that is not exactly the desired solution since I am using cross-platform tools.

I still have some other strategies to try, but I fear my strategy may quickly degrade into a trial-and-error type of thing.

Again, thanks for the reply.  Best wishes.

---

### Post by LaRoza on 2008-11-10
> **signal_ said:**
> T
I think, however, it may be an issue with cpu usage.  For my game, I have an entity system for the entities or game objects in the game.  As the number of objects increase the cpu is taxed on both Ubuntu and WindowsXP, but the Ubuntu system forces the game to run more choppily.  This choppiness could also be described as stuutter.  

For example, under Ubuntu with 1000 entities it will still run at ~60fps; however, periodically the fps will drop to ~50-something fps temporarily, thus forcing the user to experience a "stutter" or "glitch".  Under WindowsXP there is no glitching only smooth scrolling and constant frame rate.


Also, keep in mind Windows XP is seven years old. It is hard to compare to modern distros. I'd bet, that on the same hardware you have, Vista would have issues (unless you have abnormal hardware for typical XP setups)

---

### Post by pavel989 on 2008-11-10
any chance you have compiz running whiling testing on Ubuntu?

---

### Post by signal_ on 2008-11-10
> any chance you have compiz running whiling testing on Ubuntu? 

I am not running compiz.  I just verified this.  When I had this enabled, it made performance much worse.

> Also, keep in mind Windows XP is seven years old. It is hard to compare to modern distros. I'd bet, that on the same hardware you have, Vista would have issues (unless you have abnormal hardware for typical XP setups) 

I see.  That is a good point.  My brother just got a new Vista box.  He is planning to put ubuntu on it so I can perform another test on that.

It is just distressing because although I am a new Ubuntu user I enjoy coding under Ubuntu since things like virus scanners and other windows annoyances are absent.  

Thanks for the help, guys.  Best wishes.

---

### Post by pavel989 on 2008-11-11
i was going to say that compiz could have been the culprit, guess not

---

### Post by Cracauer on 2008-11-11
ATI's Linux drivers suck, that's all.

Depending on what card you have you might want to see whether DRI does any better.

How come you don't tell us what hardware you have exactly when asking a performance question?

---

### Post by Desty on 2008-11-11
Have you tried them in different screen modes? The colour depth might be different on your Ubuntu desktop than it is in XP, for example. These differences could be noticeable in a CPU/GPU intensive program.

---

### Post by signal_ on 2008-11-11
Cracauer:

> Depending on what card you have you might want to see whether DRI does any better. 

I don't know what DRI is so I will have to get back to you on that.  I will google it though.

> How come you don't tell us what hardware you have exactly when asking a performance question? 

I probably should have, but I thought it was not as important since I was running same hardware/software just under different OS's and getting differing results in performance.

I am using an old Dell Inspiron 9300 with 1.66 GHz cpu, 2 gig ram, and ATI mobility radeon x300 (64Mb).  I am planning to upgrade my comp soon though and I will research on what to buy so that both windows and ubuntu run as efficiently as possible.


Desty:

> Have you tried them in different screen modes? The colour depth might be different on your Ubuntu desktop than it is in XP, for example. These differences could be noticeable in a CPU/GPU intensive program.

No, I haven't tried that.  I will look into that as well.

Thanks for the replies, guys.

---

### Post by skullmunky on 2008-11-22
If you think the issue might be cpu related do a test on those classes with no graphics running.

Then do a pure opengl benchmark, just drawing lots and lots of polys, and see if the ATI linux driver is the culprit.

---

### Post by skullmunky on 2008-11-22
Let me elaborate on that some more.  Do your entities have a lot of cpu work going on in them, like heavy AI, or are they all in a rigid body simulation?  if so, look at compiler optimization.  If you're using a library like ODE, are you using OPCODE?  etc.  

Are they on screen all the time?  Does the framerate loss happen when more entities were flying around off screen and come on screen?  If so, that suggests a driver issue's more likely.  Look at the underlying opengl code and see if there's something you can optimize there with display lists, etc.  

Also you could try a performance comparison between SDL and GLUT just for comparison.  Anyway in general, isolate the different parts of your code and test them individually to see whose fault it is.

Then give that part of your code a stern talking to.

---

### Post by kripkenstein on 2008-11-23
It can be **very** hard to figure out why a project as complicated as a game runs faster on one OS rather than another. Simply because games are complicated things. I've encountered this with my own game-related project (link in my sig), but the opposite of what you have: Windows XP is **slower** than Ubuntu 8.10 (FWIW, this is on NVidia hardware, using SDL+OpenGL).

As suggested above by skullmunky, a place to start is to do a CPU-only test (no rendering). Then a graphics-only run with as little CPU as you can.

Also try disabling components one by one. So for example if you have a physics system, try to run it without that.

Another thing you can try is to match compilers between the platforms: Use GCC on both, that is, MinGW on Windows, and choose the exact same parameters. In particular, make sure both are in 'release' mode, or both are in 'debug' mode, and that both have the same optimization flags, etc. (Also check about external libraries that you use - were they compiled in debug or release mode?)

---


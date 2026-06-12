---
title: "Do I have a virus?"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by erans on 2008-07-11
I just installed Ubuntu a few days ago and it's suddenly acting extremely sluggish. The gnome system monitor is listing my CPU usage at always 90% split between two CPUs (I have a P4 with hyperthreading). My system is MUCH, MUCH slower than when I first installe nt of resources--the highest listed is gnomesystemmontior. :\ My system is EXTREMELY sluggish right now. even typing this message has been a chore.

Any ideas?

---

### Post by aktiwers on 2008-07-11
Thats not normal.. something is eating your CPU but I am pretty sure it is not a virus.. 
Probably an app that is acting wrong or maybe the tracker program (which I disables as the first thing on all installs).

Go to Terminal (applications = accessories = Terminal) and type:
```
top
```

then copy/paste the output to let us see whats running

---

### Post by jimmy the saint on 2008-07-11
Just a thought, but if you just installed Ubuntu, have you run the update program?  Firefox 3b5, which is installed by default before you update had a huge bug that crippled system performance.  If you haven't run the updates, there should be an icon in the taskbar that is an orange thingy, click on it and install all the updates.  If you have run the updates... well then you have some troubleshooting ahead of you!!

---

### Post by hyper_ch on 2008-07-11
why do you think it's a virus? did you run some strange binaries from shady sites?

---

### Post by zxscooby on 2008-07-11
try running the command 
```
top
```
in the terminal, it will tell you what percentage of the cpu each program running is using.
pressing shift+m will sort the programs by memory usage

I had a similar problem with an intel laptop of mine, it showed no specific program using up resources but was running sluggishly. It turned out i had a problem with a cpu throttling module called powernowd , i believe it is designed for amd processors. It was not allowing my cpu to be fully utilized. (only about 20%). I disabled it from loading at startup and it corrected the problem.

---

### Post by erans on 2008-07-11
Thanks guys. I was having so many problems even navigating to this website last night that I decided to reinstall Ubuntu this afternoon. Hopefully something like that doesn't happen again. I did install the updates, by the way.

I thought it was a virus because I've had some weird Windows viruses like that.

---

### Post by Dr Small on 2008-07-11
Well, you should not worry about such things on Linux. Generally it is a good "cause-and-effect" case. There was no need to reinstall Ubuntu. You could have just did as was suggested, (using top to see what the highest resource hog was, and kill it.) instead of reinstalling.

Dr Small

---

### Post by andrewt522 on 2008-07-11
Question regarding this thread...

If I was to run "top" and find the resource hog, how would I go about killing it?

---

### Post by tuxxy on 2008-07-11
killall <process>

---

### Post by philinux on 2008-07-11
> **andrewt522 said:**
> Question regarding this thread...

If I was to run "top" and find the resource hog, how would I go about killing it?

you might not need to kill it just disable it at startup.

Many people have disabled trackerd but for me now this is not a problem app.

---

### Post by andrewt522 on 2008-07-11
Thanks.  So my next question would be how do I disable?  Also, is there a way to know the difference between when I would disable or kill?  And, if I kill an app, is it completely dead?

---

### Post by philinux on 2008-07-11
Hypothetical answers could end up killing your session by disabling some crucial app.

But for instance when/if firefox, a non system app, hangs which is the most likely scenario. I use system monitor highlight the process and right click to kill the app. There are other ways too, like use the force quit, from "add to panel", or using terminal and "killall firefox" for example.

---

### Post by andrewt522 on 2008-07-11
Thanks for the answer, Philinux.  I added the force quit to my panel already, so you've made me feel good about myself!  As you can tell, I'm pretty new, so I always assume when people discuss the terminal that the solution is more complicated than it really is.  I suppose you could say that I'm a little intimidated by the terminal.  That said, I'm trying!

Thanks again!

---

### Post by Dr Small on 2008-07-11
> **andrewt522 said:**
> I suppose you could say that I'm a little intimidated by the terminal.

Don't be.
The terminal is the most powerful tool on your system. Learn to use it, and use it wisely. You will come to realize that it can really simplify matters compared to doing it the GUI way alot of times.

Dr Small

---

### Post by aimpau on 2008-07-11
ctrl+2 for the terminal shortcut in your desktop

if all things fails, try pressing the ctrl+alt+backspace.

---

### Post by Paqman on 2008-07-11
> **philinux said:**
> 
Many people have disabled trackerd but for me now this is not a problem app.

I think they just get freaked out when they do see Tracker chewing up all the resources after installing. The thing is, until it does all its indexing, Tracker will work quite hard. After that it'll settle down.

Having said that, i've disabled Tracker on my laptop because i've only got 512MB and never use it.

---

### Post by hyper_ch on 2008-07-11
btw, I prefer to use htop over top... it's just a lot nicer ;)

---

### Post by philinux on 2008-07-11
> **Paqman said:**
> I think they just get freaked out when they do see Tracker chewing up all the resources after installing. The thing is, until it does all its indexing, Tracker will work quite hard. After that it'll settle down.

Having said that, i've disabled Tracker on my laptop because i've only got 512MB and never use it.

It's got smart pausing now too, if indexing might degrade performance.

---

### Post by hyper_ch on 2008-07-11
if tracker is running you can renice it at a lower priority so it won't interfere (too much) with the rest...

---


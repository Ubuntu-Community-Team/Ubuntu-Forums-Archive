---
title: "HD Playback Intel HD 3000 Graphics"
date: 2013-01-11
forum: New to Ubuntu
---

### Post by DanielWEWO on 2013-01-11
Sorry if this has been posted already, I tried searching already, but I didn't find anything within a couple minutes. 

So I was trying to watch a video in 720p HD on youtube, and was having some trouble, the video was lagging behind the audio a little bit and was generally bad. Switched to 360 or 480 and its fine. I've got an i3 380M with Intel HD 3000 graphics, and I've had no problems watching any videos in HD before on windows. I checked "About this computer" and graphics says "Unkown" I'm assuming it's not loading a graphics driver then? 

Sorry about the noob status, this is day one for me!

Thanks,
Daniel

---

### Post by MadmanRB on 2013-01-11
What version of Ubuntu are you running?
This is a good start for us so we can establish possibly getting you drivers, just be warned that intel graphics cards are not all that great and the reason why they usually work in windows is due to preinstalled drivers.

---

### Post by pqwoerituytrueiwoq on 2013-01-11
was the video buffering, that would be from a slow connection

my Intel(R) Pentium(R) CPU B970 @ 2.30GHz handles 1080p just fine (2 at the same time on 2 screens one 1080p and one 720p)
not using unity, i am using xubuntu (xfce)

---

### Post by DanielWEWO on 2013-01-11
Sorry, forgot to mention I'm running Ubuntu 12.10 x64. I'll add system specs into my signature or profile as soon as i've got 25 comments, ha. And yes, I'm sure it wasn't buffering, I've got an 85Mbps connection, and the video was fully loaded, I also tried it on separate videos, also fully loaded.

For further info this is on a Dell Inspiron N5040

---

### Post by pqwoerituytrueiwoq on 2013-01-11
you can try it without unity on
```
sudo apt-get install xubuntu-desktop
```
logout 
click the gear in the login section and select xubuntu

---

### Post by DanielWEWO on 2013-01-11
Its installing at the moment, So are you just trying to see if its the GUI that's causing bad video performance? I'll update as soon as I've tried.

I have two questions, does Ubuntu not recognize the type of graphics that I have? Because it says Unknown, when I'd expect it to say something along the lines of Intel HD 3000 Integrated Graphics, or something like that.

Second question is, do you guys just memorize the names of these install packages???

---

### Post by pqwoerituytrueiwoq on 2013-01-11
i know the ones i usually install, meta packages are nice
meta packages are packages that are really a long list of packages
type part of name and hit tab key, the tab key is magic

your cpu/gpu are better than what is in my laptop
and i can play 2 1080p vids at once on 2 screens and have no playback errors, aside from overlapping audio tracks of source

intel drivers are open source and just work on linux, no extra work needed

---

### Post by DanielWEWO on 2013-01-12
So the 1080p playback was just as bad. 

What I didn't really think to try was the 720p playback, which worked just fine, and given, its only a 1366x768 screen so I guess its problem solved?

I still don't get why the 1080p video wouldn't play properly, not sure if this is normal or if I should dig deeper for a cause?

---

### Post by SeijiSensei on 2013-01-12
If you're watching in Flash player at YouTube, make the video full screen then right click on the image and bring up the settings dialog.  Try clicking the hardware acceleration box if it is not already checked, then close the browser and see if that helps.

---

### Post by DanielWEWO on 2013-01-12
It was already checked.

---

### Post by DanielWEWO on 2013-01-12
I just used the terminal to tell me my memory usage and it shows total:3755 and used: 3234

Why the heck am I using so much RAM? Is this normal for Ubuntu x64?

---

### Post by MadmanRB on 2013-01-12
Well the core reason why ubuntu doesnt detect your card is probably  due to intel graphics card support being so so in linux.
It doesnt mean its incompatible, it just may not be a graphics card that works too well with linux.
This is not the fault of linux mind you, remember this is a Microsoft ruled world so a lot of devices and drivers primarily work with windows only and or work best with windows.
Now most of the time the linux drivers do okay but issues are bound to pop up.
Actually your issue may be more of an issue with flash then with your card, after all adobe pretty much droipped the ball on linux support and in a few years flash for linux will be gone as the latest version for linux 11.2 will be done for.
But there is some hope, you could try google chrome as it does use a built in flash plugin of its own.
This is the consequence of those morons at adobe, so maybe using gooogle chrome as your primary browser may fix any issues you have.

> **DanielWEWO said:**
> I just used the terminal to tell me my memory usage and it shows total:3755 and used: 3234

Why the heck am I using so much RAM? Is this normal for Ubuntu x64?

No this is unusual.
Sounds like flash to me, its a memory hog.

---

### Post by DanielWEWO on 2013-01-12
Great, so thank you for the extremely detailed response.
So, I'll try google chrome, but I really like Opera mainly because of the fit-to-width capability that I use all the time on my laptop.


That memory reading was done when I wasn't watching a video, I checked the command 'top' and it looked like nothing was really using up the memory.

Going to try with chrome, then uninstall flash and see if my memory usage goes down.

Once again, thanks so much for the help here.

---

### Post by DanielWEWO on 2013-01-12
Okay, now I'm just confused. So, is Chromium any different than Chrome? Because I know the windows Chrome DOES have flash player built in, but I uninstalled flash player and attempted to watch a video in Chromium and was asked to install flash player.

Sorry for not being too great at Linux, its my first day! lol

---

### Post by DanielWEWO on 2013-01-12
So I discovered chrome is in fact different than chromium. Chrome does have flash player built in, and flawless 1080p video playback.


so... Shame on adobe /solved /thread? lol


and... as a side note should I start a new thread about my memory usage? lol. It's still high after flash has been uninstalled.

---


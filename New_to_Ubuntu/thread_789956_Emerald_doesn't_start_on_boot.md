---
title: "Emerald doesn't start on boot"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Rukaru on 2008-05-11
Update: I'm really getting used to ubuntu.  it took a while...well...2 days.  I've tried XP, Vista, and Mac.  I think ubuntu is the best based only on the most important aspect of OS's: the way it looks.  I like that you can make ubuntu look any way you want and have awsome 3D eye candy.

Okay, now for the point of this topic.  i need to get emerald to start on boot. I went to sessions > boot but I didn't know the command.  Is this all i would need?  If that is the case, then someone please tell me the command.  I'd also like to know how to change the splash screen.

And if anyone knows the sieze in pexels that skydome uses, that would be great.  I couldn't find anything good for that so I'll have to make my own.

---

### Post by nynoah on 2008-05-11
you have to manually edit your startups.

Go to upper Left corner

system-preferences- sessions - add

Then type in   
Name - **Emerald**
command - **emerald --replace**
comment - **start emerald**

---

### Post by tjwoosta on 2008-05-11
1. to make emerald start with a theme at boot just go to Preferences-Sessions then click the startup programs tab then click add

for the command to use put 
```
emerald --replace
```

2. i dont know how to change splash screen sry

3. to make animated skydome its like 2048 x 1024  (ive also heard 4096 x 1024 but i cant make it work)

---

### Post by Rukaru on 2008-05-11
> **tjwoosta said:**
> 1. to make emerald start with a theme at boot just go to Preferences-Sessions then click the startup programs tab then click add

for the command to use put 
```
emerald --replace
```

2. i dont know how to change splash screen sry

3. to make animated skydome its like 2048 x 1024  (ive also heard 4096 x 1024 but i cant make it work)

Okay thanks.  I actually think it depends on your resolution...duh.  I can't believe I didn't realize it.  Anyway...I'll figure it out. 

Oh great!  it didn't work.  I mean...emerald is included in the startup list....but there's no way to get it on after rebooting!  Anyone have any solutions? 

This is kinda off topic, but does anyone know how to change the password?

---

### Post by tjwoosta on 2008-05-11
go to terminal and type passwd

> I actually think it depends on your resolution...duh. I can't believe I didn't realize it

ha, yea i guess that makes since

---

### Post by inportb on 2008-05-11
password... to your account? passwd.

---

### Post by Rukaru on 2008-05-11
> **inportb said:**
> password... to your account? passwd.

got it.  Okay, now how about emerald?  it just refuses to start.  I go to it in system>preferences, and select what I want from the list, but nothing happens!

---

### Post by nynoah on 2008-05-11
Did you try what I said?  Do that and reboot and it should work.

---

### Post by Rukaru on 2008-05-11
> **nynoah said:**
> Did you try what I said?  Do that and reboot and it should work.

Yeah man I did exactly what you said.  It still just shows the custom theme (set at linsta2 right now)...you know....not emerald.  Everything else starts up just fine.  But emerald starting up on bootup isn't even the problem, since when I go to emerald i can't select anything...I mean nothing happens when I click it.

---

### Post by nynoah on 2008-05-11
OK sounds like you have something else going on.  Do you have compiz settings manager installed?  If not, install it.  Also do you have your proprietary drivers installed?  If not Emerald will not work till they are enabled.

---

### Post by nynoah on 2008-05-11
looks like we have a troll on the board.

---

### Post by Rukaru on 2008-05-11
> **nynoah said:**
> OK sounds like you have something else going on.  Do you have compiz settings manager installed?  If not, install it.  Also do you have your proprietary drivers installed?  If not Emerald will not work till they are enabled.

All my driverss are enabled....and compiz works perfectly. I don't know if what I use is compiz settings manager...but i go to a windwo that has tons of stuff like desktop cube, cube rotate, etc.  That's all compiz stuff.

---

### Post by Rukaru on 2008-05-11
> **nynoah said:**
> looks like we have a troll on the board.

Who?  And what exactly is a troll?  Is someone giving me bad info or something?

---

### Post by nynoah on 2008-05-11
Don't worry rukaru..........seems the admins deleted that idiot already.  He kept on cutting and pasting something like a fresh Ubuntu install will fix everything.

---

### Post by nynoah on 2008-05-11
I know that in my synaptic I have emerald installed and libemeraldengine0  installed.  See what you have when you type in emerald into the search field of synaptic.

---

### Post by Rukaru on 2008-05-11
> **nynoah said:**
> Don't worry rukaru..........seems the admins deleted that idiot already.  He kept on cutting and pasting something like a fresh Ubuntu install will fix everything.

Oh okay thanks.  Anyway, I've been trying stuff to get emerald working but nothing's happening.  It was working before I rebooted.  I double checked in the sessions>boot and emerald was there.  

and btw, why are there two CPUs running?  I saw them both in system monitor.

---

### Post by nynoah on 2008-05-11
If you have a 64 bit system you have 2 cpu's in your computer.  Each runs different things at a different time so your system does not bog down.

---

### Post by Rukaru on 2008-05-11
> **nynoah said:**
> If you have a 64 bit system you have 2 cpu's in your computer.  Each runs different things at a different time so your system does not bog down.

Well I have a dual processor.  This doesn't mean the dual booted XP is running while I'm running ubuntu does it? I don't want that!

Oh, and I was able to get emerald running again by hitting alt+F2 and typing in "emerald --replace", so I guess it is a start up thing.  It's kinda annoying having to do that each time if i want my beautiful emerald theme.

---

### Post by nynoah on 2008-05-11
Try what I said before again.  if you can get emerald running right with alt f2 then you should be able to permanently add it to your start up programs.  This is how I got mine to run at startup.

---

### Post by Rukaru on 2008-05-11
> **nynoah said:**
> Try what I said before again.  if you can get emerald running right with alt f2 then you should be able to permanently add it to your start up programs.  This is how I got mine to run at startup.

Wow...it works now.  Weird.  I must have capitalized something.  Anyway, thanks a lot!  Now on to my next problem.  I'll need a new thread for that since it's completely unrelated.

---

### Post by crashnburn007 on 2010-01-17
> **tjwoosta said:**
> To make emerald start with a theme at boot just go to Startup Applications then click Add, for the command to use put:
```
emerald --replace
```

Thanks for posting this - worked fine!

---


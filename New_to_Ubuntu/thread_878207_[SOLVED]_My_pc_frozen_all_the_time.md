---
title: "[SOLVED] My pc frozen all the time"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by BSG Fan on 2008-08-02
Hello, i am new here and new with Ububtu8.04

My pc freezes every second
what can be?
the memory and/or mother board?
Or I need a software?

Please help
:(

---

### Post by VitaLiNux on 2008-08-02
Hello, mate!

I think you should give more information to know what the problem is:

) Does it happen with a fresh install?
) When does it happen?
) Have you got a specific program opened when it happens?
) Which graphic card you got?
) What's the specific behavior(describe it completely ;) )?

Maybe if you give us more info we can tell you what to do...

---

### Post by jualin on 2008-08-02
Also do you have enough space left in your hard drive. I have heard that having little space causes freezes.

---

### Post by BSG Fan on 2008-08-02
My system is:
hardy (8.04)
Kernell Linux 2.6.24-19
memory: 978.5 MiB
Processor: VIA Samuel 2
I use Firefox

graphic card? Not idea.

Yes, is the first time my pc uses Ubuntu: I have Windows all my life :(
That happen really when I don't move the mouse (or I leave the arrow on any firefox page).
If I go to another place for 3 minutes it is already frozen too.
I have to restart it like 20 times a day, hehe

well, I can not give more details because I am a new in Ubuntu

Thanks for reply

Galactica Fan
[http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif](http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif)

---

### Post by BSG Fan on 2008-08-02
> **jualin said:**
> Also do you have enough space left in your hard drive. I have heard that having little space causes freezes.

My sistem have 135.2 GiBhttp://ubuntuforums.org/images/smilies/new_popcornsmiley.gif

---

### Post by jualin on 2008-08-02
Have you run all of the updates? And also check under System, Preferences, screensaver and maybe disable the "Idle" option. Sorry I can't give you more details, I am not on my Ubuntu machine right now. I had similar crashes before and disabling that solved the problems.

---

### Post by BSG Fan on 2008-08-02
> **jualin said:**
> Have you run all of the updates? And also check under System, Preferences, screensaver and maybe disable the "Idle" option. Sorry I can't give you more details, I am not on my Ubuntu machine right now. I had similar crashes before and disabling that solved the problems.

yes, i ran all the updates.
I disable the idle option

but the problem continues :(

I appreciate Vitalinux and Jualin replies :)
I really can not describe further my pc and properties :(

---

### Post by jualin on 2008-08-02
I'll try helping you out when I get home (I am at work now). But I as of right now I ran out of ideas, maybe checking the logs to give us an idea of why the system is crashing.

---

### Post by jamesrfla on 2008-08-02
When it dose that press Ctrl+Alt+F2. The login in with user name and password. Type in ```
htop
``` and find the procces taking up the most CPU usage. Then after you find the process do ```
kill (process taking up CPU usage)
```Then to get back to the desktop do Ctrl+Alt+F7. Remember to change (process taking up CPU usage) to the process you found. Hope this works

---

### Post by BSG Fan on 2008-08-03
> **jamesrfla said:**
> When it dose that press Ctrl+Alt+F2. The login in with user name and password. Type in ```
htop
``` and find the procces taking up the most CPU usage. Then after you find the process do ```
kill (process taking up CPU usage)
```Then to get back to the desktop do Ctrl+Alt+F7. Remember to change (process taking up CPU usage) to the process you found. Hope this works

Hey
Thanks you for the information.
I did what you tell me but the process that is taking more cpu is the same name have my pc. Sorry but I dont remember what i saw, hehe
I think I surrender: i dont know anything of pc almost :(

I appreciate all ur efforts, really
Thanks u!
:)
[http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif](http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif)

---

### Post by jualin on 2008-08-04
> **BSG Fan said:**
> Hey
Thanks you for the information.
I did what you tell me but the process that is taking more cpu is the same name have my pc. Sorry but I dont remember what i saw, hehe
I think I surrender: i dont know anything of pc almost :(

I appreciate all ur efforts, really
Thanks u!
:)
[http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif](http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif)

Don't give up just yet. The idea of seeing which process is using more of your CPU will help us identify your problem. Maybe the solution is something like making that application not run when your computer turns on.

---


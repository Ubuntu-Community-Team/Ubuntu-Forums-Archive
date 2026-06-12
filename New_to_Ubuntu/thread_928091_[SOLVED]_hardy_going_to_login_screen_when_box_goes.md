---
title: "[SOLVED] hardy going to login screen when box goes idle"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by crazypenguin2008 on 2008-09-23
it started doing this last night. when my box goes idle i get logged out of hardy and it goes to teh login screen.....any ideas on how to fix this? 

possiable bug maybe??

---

### Post by twitch2197 on 2008-09-23
maybe it's set in your preferences to lock the computer if it goes into a screensaver. look in the screensaver preferences. there's a checkbox that says 'lock screen when screensaver is active'. is it checked? if so, uncheck it.

---

### Post by crazypenguin2008 on 2008-09-23
nope thats not it either.

any other ideas??

---

### Post by twitch2197 on 2008-09-23
how long does your computer go idle, and does it go into any power saving modes before it makes you log in again?

---

### Post by crazypenguin2008 on 2008-09-23
ok i just went into the screensaver menue it logs out of ubuntu too......


verry verry strange

---

### Post by twitch2197 on 2008-09-23
so it also logs out in a screensaver?

---

### Post by forger on 2008-09-23
which screensaver are you currently using? ripples?

---

### Post by crazypenguin2008 on 2008-09-23
i went into systep>preferneces>screensaver and it logs me out of ubuntu and back ot the signin screen. 

its getting verry annoying now. i went downstairs and came back and boom, im logged out....

---

### Post by crazypenguin2008 on 2008-09-23
the screensaver with the planets and moonscapes on it. it does slide shows for about 15mins then goes black when it works correctly. i sat here and watched it a few mins ago. it goes idle,then black then back ot the human themed login screen for ubuntu

---

### Post by twitch2197 on 2008-09-23
hmm after a little googling i found out that this was a bug in ubuntu a while ago. have you installed all the kernel updates and any other system updates?

---

### Post by crazypenguin2008 on 2008-09-23
yep. my system checks for updates and i update on a daily basis as they come in.

---

### Post by twitch2197 on 2008-09-23
how long does your computer go before it goes into any power saving modes?

---

### Post by crazypenguin2008 on 2008-09-23
i dont have it set to powersave. just my notebooks are set to powersave.

its set to be considered idle and go to screensaver after 5 mins when it works corectly

---

### Post by twitch2197 on 2008-09-23
hmm... this one really has me stumped. so tell me exactly what happens. you say it logs off when it goes idle. like, during the screensaver? or does it just log off and the screensaver doesn't happen?

---

### Post by crazypenguin2008 on 2008-09-23
it never makes it to the screensaver. after 5mins it goes black,for 15 seconds then blinks twice then its back ot the human themed loginin screen for ubuntu

---

### Post by twitch2197 on 2008-09-23
I don't know. did you change anything or install anything before this started happening? anything that could have an effect, i mean.

---

### Post by crazypenguin2008 on 2008-09-23
i havnt changed anything. i dont mess with the settings on the desktop too much.....

its got me stumped as well :confused::confused::confused::confused:

---

### Post by twitch2197 on 2008-09-23
let's experiment. are you able to change your screensaver? if you can, try changing to a different one. maybe your screensaver is crashing something, and it logs you out as a way to 'fix' the crash.

---

### Post by crazypenguin2008 on 2008-09-24
i got it fixed. or at least a fix for now. i went thru my commands and found the gnome disable screensaver command and now it never goes idle or goes to screensaver. ill juts have to flick the monitor off at nights til li can find a proper fix.

---

### Post by forger on 2008-09-26
You can also set your monitor to go to sleep through bios i think

---

### Post by Floyd770 on 2008-11-08
Well, this issue may not be exactly fixed yet..  

I have a fresh install of 8.10 and when I start open the screensaver options window, I start clicking on different screensavers to preview and I get booted back into the login screen as well...

I haven't touched any of the powersave settings, and this is the first time i've even opened the screensaver settings window...

Any other ideas?

Thanks..

---

### Post by pg159 on 2009-04-27
Did you ever resolve this issue? I have the exact same behavior. I'm running 8.0.4 with the latest upgrades on a Virtual installation of Ubuntu under Parallels 3 on a MacBook Pro.

I opened the Screensaver preferences to play with the different screensavers. As soon as I selected one, the system kicked me out to the login screen. Now all attempts to open the Screensaver Preferences cause the same thing. If I let the system sit idle for more than 15 minutes, back to the login screen.

On a mac, I would just trash the screensavers plist file. Is there something similar on Ubuntu?

---

### Post by Floyd770 on 2009-04-27
I never really found a solution to this myself, but then again, I just disabled the screensavers anyway, along with all powersaving features, and haven't looked back since.  (Yeah, I know, some hippy I am...)

Good luck!

---


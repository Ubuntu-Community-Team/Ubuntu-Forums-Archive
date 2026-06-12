---
title: "Uncool sound and login 'glitch'!"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by Redptc on 2008-06-29
I have just done a clean install of 8.04 and it all seems to be going well except for a couple of 'glitches'. 

The login screen Resolution is incorrect and we lose a large part of the screen. I had to change the resolution, once logged in, to 1280x800 from 1440x900. After log in, all goes well but it seems that the screen resolution change is not passed on or remembered by the login screen when restarting.

Is there some way to access the login in order to change the screen resolution because, as it is, it looks very uncool!

My second 'glitch' has to do with the sound. There is no sound at login, that is, no 'tom-toms' and no follow-up fanfare. I can initiate sound by moving the 'Master' control bar at the top of the screen. After that the sound is perfect.

I get the feeling that something is *missing* at start up, or there is a failure to detect changes made during a session. 

I am not running any special sort of sound card so that shouldn't be a complication!

---

### Post by wolfen69 on 2008-06-29
for resolution, try:```
sudo dpkg-reconfigure -phigh xserver-xorg
```
not sure about your sound problem.

---

### Post by Redptc on 2008-06-29
Thanks Wolf, I ran that even tho I didn't know what to expect but nothing happened or changed. 

Is there more information I need? I didn't get an opportunity to change the resolution or anything like that. Asked to enter the password got a warning about affecting 'user' changes but to no effect on the problem.

---

### Post by RequinB4 on 2008-06-29
Start-up manager will do all of this and more -- BUT BE CAREFUL as changing the boot process always runs the risk of you making your computer unbootable!

```

sudo apt-get install startupmanager

```

---

### Post by Redptc on 2008-06-30
That sounded like it was to be the answer, thanks RequinB4, but sadly, no luck.

'Startup Manager' doesn't consider audio in any way.

As far as screen resolution on startup the choices provided don't compare to my requirements nor do they improve the situation if I select something close. The 'login' screen remains out of position by about 3" or 8mm.

Not only does it not work but every time I boot I now get a story about "undefined video mode" and I have to wait "30 seconds" while a suitable "mode" is found. I'll probably have to reinstall to get that fixed.

Appreciate your ideas.

---


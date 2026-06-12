---
title: "Strange lines watching videos?"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by thevjm on 2008-04-28
Whenever I am watching a video, I get these strange horizontal lines across the video. It looks like it was split in half then reconnected. The appears for a second and then go away. It keeps doing this.

Have any of you guys experienced this? It's really annoying. I would take screenshot, but it's hard to capture.

Ubuntu 8.04 AMD64
Nvidia 8400GS

---

### Post by Barrucadu on 2008-04-28
Is it in any video? What media player are you using? Does it happen in other media players?

---

### Post by thevjm on 2008-04-28
It does it in every video.

The players I have tried are:

MPlayer
VLC
Totem
xine

It also seems to do it on a few desktop effects. Most noticable while zooming in and out of expo.

I tried installing updated drivers following [this](https://help.ubuntu.com/community/NvidiaManual) guide, but it didn't help.

---

### Post by jacob01 on 2008-04-28
it may be your graphic drivers. i used to get a similar problem on my old integrated gpu but it seem that you have a decent graphics card.

what drivers are you using?

and is direct rendering enabled?
glxinfo | grep direct

and if it is yes then your drivers are good

---

### Post by thevjm on 2008-04-28
Yep, it looks like direct rendering is enabled.

---

### Post by linuxlizard on 2008-04-28
make sure you enable antialiasing in each video player (usually preferences-video-enable antialiasing).
This is never active by default in almost every linux app for some reason and without it you will get those "scanlines".

---

### Post by thevjm on 2008-04-28
I don't seem to see an option for antialiasing. L have looked in both SMplayer and VLC.

I should also mention this happens in YouTube videos as well.

---

### Post by linuxlizard on 2008-04-28
if it's youtube videos playing in your browser, can't help you there. Maybe it's not the problem I'm thinking of. But try this:

In vlc- if you look at the menus in the top bar of vlc you will see:

File View Settings Audio Video Navigation Help

click the word video and a menu will drop down

highlight deinterlace in the menu

select blend

there you go

sorry- confused the word deinterlace with antialias in last post. My bad. Wasn't looking at it and recalled the word incorrectly.

---

### Post by thevjm on 2008-04-28
These do not feel like lines of interlacing.

They occur unpredictably, and only on my computer.

Could someone recommend an application that would allow me to record the screen so I could describe it better?

---

### Post by thevjm on 2008-04-29
Bump.

---

### Post by davemolloy64 on 2008-04-29
This is a problem I have with my ATI onboard graphics card.

As far as i know, in my case, it's a driver problem, and it's to do with having compiz enabled.

If it's the same issue, turning off desktop effects while watching videos should solve the problem.

However, I'm not sure if this will work, as I'm led to believe that nvidia cards don't sufer from this problem. Try switching off desktop effects- at least that'll narrow it down to a compiz problem or not.

---

### Post by thevjm on 2008-04-29
Yep, problem goes away when I turn off desktop effects.

I guess I will just keep off desktop effects while watching videos. Unless, there is a compiz alternative?

---

### Post by thevjm on 2008-04-29
Do you guys think a new video card would solve the problem?

I've been looking into an upgrade anyways.

---

### Post by mysticmatrix on 2008-04-29
any decent Nvidia card would do the job.

---

### Post by thevjm on 2008-04-30
> **mysticmatrix said:**
> any decent Nvidia card would do the job.
My current card (8400GS) *should* be able to do just fine.

I'm just wondering if this is a problem with all nvidia cards.

---


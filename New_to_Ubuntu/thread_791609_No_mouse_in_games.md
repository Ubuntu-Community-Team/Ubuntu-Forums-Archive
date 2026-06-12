---
title: "No mouse in games"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Bölvaður on 2008-05-12
I installed hardy yesterday and now I don't seem like be able to use the mouse in ET:QW and Alien Arena, which are the first 2 games I installed.

In ET:QW the application doesn't grab any mouse at all, so I am unable to go beyond the "select user" menu at the start.

In Alien Arena I can start playing using arrow buttons but when in-game I am unable to control the player with my mouse (mouse buttons work fine though). Every time I touch the mouse I look down (or up if I invert mouse up/down direction then I will look up).

*added*
In Warsow the mouse movements will only result in right hand turn of the player. No matter what direction I move the mouse, up, down, left, right. And these are way faster movements than they should. I turned the sensitivity down to minimum and still it is at least 2x what I am used to.


ET:QW worked fine in Gusty, and Open Arena also.*added* Warsow worked perfectly in Gusty.

_Can anyone help?_


I have not encountered any other problems in Hardy, except that Firefox 3 beta seems extremely sluggish.

---

### Post by nukecoder on 2008-05-15
I'm having the same problems with the mouse in all the fullscreen games I have tried.  I can't even get past any menus as any time I move the mouse, the cursor will jump back to the bottom right corner.  If I use the keyboard to get into a game it isn't playable at all.  Every little mouse movement makes it go crazy in all different directions.  Anybody got any clues to what would cause this kind of behavior?

---

### Post by Bölvaður on 2008-05-20
I got it.

Disable Xinerama.

My problem was that I have 2 monitors.
I was unable to use TwinView, then when I fullscreen programs they go to my right monitor in very small display of it. And also half of the game is out of boarder (that is, it is too far to the right.. so it goes out of the monitors view)

Then in Separate X screen, I can fullscreen but I am unable to have Xinerama on because then the mouse goes all crazy.

But when I leave it off, I dont have 2 monitors working... well I can put my mouse to the blank monitor, but I am unable to use it for anything else... cant enter it with mouse or anything (this is kUbuntu now).

---

### Post by nukecoder on 2008-05-21
Bölvaður, thanks for your reply!

I have 2 monitors also but xinerama is already disabled.  The problem happens in fullscreen mode and in windowed mode.  It worked perfectly in 7.04 so I don't get it.  If anyone has a clue to what is causing this problem (is it X11, display driver, or something else?) I would really appreciate any help or direction to fix it.

---


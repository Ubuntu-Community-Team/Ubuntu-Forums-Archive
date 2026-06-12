---
title: "xrandr and panning (or lack thereof)"
date: 2013-02-21
forum: New to Ubuntu
---

### Post by madpraxis on 2013-02-21
So, I tried asking elsewhere in the forums and got less then a hundred views and no responses or questions in over a week...so...I'll try here in the section I didn't even realize existed when I first asked ;) Straight up copy and paste from the old one, here we go:

     ```
xrandr --fb 1280x1024 --output LVDS --mode 1280x800 --panning 1280x1024 
```I do this in terminal. It works brilliantly and resizes the display...except I can't actually **access**  the nice new happy space I have created off screen. This is making me  sad inside when the little mouse cursor goes bonk against the physical  limits of my screen and nothing happens other then me chanting 'pan pan  pan'.

I wish for you all to help me so I'm not sad inside anymore.  I wish to be happy inside.

So what do I have to do so I can actually do the panning part  of..er...panning? I've tried looking up this problem on the great skynet  except what information I do find either isn't answered, or is not  really the problem and more concerned with doing what I had already done  with xrandr, and even then people seem to be contradicting the advice  others give (at least it seems that way).

Totally computer inept I guess, so the simpler the better (I still  haven't gotten around to making ubuntu boot from hd instead of the  install flash drive thinger...). I'm rather sure I'm forgetting some  important information that is really really needed and will make it so  someone wiser in the ways of ubuntu can solve my conundrum instantly, so  feel free to not just ask, but demand more information...

So...uh...pimp my crappy dell second(fifth?)hand laptop...

As an addendum to the original, seriously, someone help me :D
I get a few hours each week in total that I'm not working, sleeping, eating, or commuting to work and I'd really like to add playing Aurora to the recreation list in my spare minutes, yet I can't because my monitor will only go up to 1280x800, which isn't big enough, yet it would work great (like it did with xp) pretending to be bigger and letting me pan. Except I can't. And not totally computer inept, just mostly unix inept...

---

### Post by Michael Dooley on 2013-02-22
I'm trying to get the same affect in elementary OS, a ubuntu variant. Take a look at this page:

[http://ryancreich.wordpress.com/2012/05/01/ubuntu-on-a-netbook-screen-revisited/](http://ryancreich.wordpress.com/2012/05/01/ubuntu-on-a-netbook-screen-revisited/)

and see if you can fix panning. There is a launchpad page referenced there that provides a possibly useful repository:

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/883319/comments/32](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/883319/comments/32)

I'm busy at the moment or I'd test it for you (and for myself). Let us know if you have any success.

Thanks for posting to the forums madpraxis.

---

### Post by madpraxis on 2013-02-22
Words! Many words! I'll maybe try it in the morning or worse case find my inverter and take laptop with me in truck to try on a break or something (really need to fix/find a new battery for this sad sack laptop ;) )
Though...I don't think I've found that page before, I found something that looked similar I do believe.

---

### Post by Michael Dooley on 2013-03-16
See the following page for a functioning pan using xrandr:

[https://wiki.ubuntu.com/X/Config/Resolution#Panning_viewport](https://wiki.ubuntu.com/X/Config/Resolution#Panning_viewport)

I just tried this command (modified for my particular circumstances) and it produced the expected result. I was able to effortlessly pan a much larger area than my apparent screen area. The second command let me return to the initial display situation. This evening, I'll try these commands on my netbook.

```
$ xrandr --output HDMI-0 --rate 60 --mode 1280x1024 --fb 2560x2048 --panning 2560x2048
$ xrandr -s 1280x1024
```

---

### Post by Michael Dooley on 2013-03-16
Works with my NB205 toshiba too. Glad to find this out.

```
$ xrandr --output LVDS1 --rate 60 --mode 1024x600 --fb 2048x1200 --panning 2048x1200
$ xrandr -s 1024x600
```

---


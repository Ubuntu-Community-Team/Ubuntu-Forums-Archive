---
title: "Tons and tons of problems with games!  (Please help a noob out)"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by Psythik on 2008-06-10
No matter what game I try to play, I always run into problems that prevent me from actually playing it.  To start, I have to disable Compiz before I start a game otherwise my screen flickers rapidly and the game is unplayable.

When running Linux-native games (Nexiuz, for ex), there's a tremendous amount of mouse lag equivalent to playing in a high-ping server.  The keyboard works fine, though.  I've noticed that this doesn't happen in the menus before a game starts, but as soon as it does, the mouse goes to hell, and doesn't stop until I quit the game.  Also, there's no sound at all (although I get sound just fine in every other program I try ('cept for Windows apps in Wine).

Steam games don't run at all (even though the Wine App DB says they should).  No matter what game I pick, it loads as normal, but as soon as it comes time to render 3D, the screen goes black and all that's there is a flickering mouse cursor.  I'm pretty sure sound wouldn't work in it either.

While we're on the topic of graphics, I noticed that as soon as Ubuntu automatically installed my GPU drivers, I lost the ability to individually control my monitors.  Instead of showing two displays (in "Screen Resolution"), there's only one, and it says "Unknown".  Both screens show the same thing, and turning off "Clone Screens" doesn't do a damn thing.  Neither does clicking "Detect Displays".

I'm guessing that most of my problems are caused by my GPU drivers (except probably for the mouse lag issue), but when I went to get the drivers from the AMD website, I took one look at the instructions and said "**** it".  Why do they have to be so complicated?

I'd really appreciate it if I could get some games running properly!  Normally I'd just dual-boot Windows for that, but due to circumstances beyond my control, that's not an option right now!

Here are my specs (don't go blaming my problems on the specs because all my Steam games ran just fine in XP on the same machine!):

PIV 3.40GHz HT
1024MB DDR 400
128MB AMD Mobility Radeon 9700
Creative SB Live! 24-Bit external (using PulseAudio ASLA to get the sound working in Firefox, Songbird, and every other Linux-native app -- but not in games or anything in Wine, for some reason...)



*(Oh, and sorry for making so many topics here; I'm just trying to get everything working!)*

---

### Post by Psythik on 2008-06-11
Dang, this place moves fast.

---

### Post by Xiong Chiamiov on 2008-06-11
> **Psythik said:**
> Dang, this place moves fast.
It sure does.

I take it when you say games, you mean 3d games, those that require glx.
Run
```

glxinfo | less

```
and take a look at the third line (direct rendering).  Does it say "Yes"?

You may need to do some mucking around with video card drivers (though Compiz runs, so...).  It would be helpful if you posted the chipset of your graphics card.

---

### Post by raedbenz on 2008-06-11
> **Psythik said:**
> 
Here are my specs (don't go blaming my problems on the specs because all my Steam games ran just fine in XP on the same machine!):

Although i prefer Linux, but games on Windows run much better and more stable, specifically on Xp not Vista

---

### Post by chronographer on 2008-06-11
From my experience (admittedly limited) I would recommend you play games in windows. if you want to play games on Linux, turn off compiz ("metacity --replace") then when you're finished playing games, turn it back on again "compiz --replace". I tried dual monitor with my new radeon card, then new official drivers support dual screens, easily using "aticonfig" but I like using the open source drivers, which work with with compiz and xrandr to put a picture on my tv temporarily (like when I watch a movie).

So bottom line... try installing proprietary (restricted) drivers, mess around with aticonfig and xorg.conf to get games and productivity working. Or. Use Ubuntu for work, xp for play.

---

### Post by sherin on 2008-06-11
backing [Xiong]("http://ubuntuforums.org/member.php?u=440346") :)

---

### Post by Psythik on 2008-06-11
> **Xiong Chiamiov said:**
> Run
```

glxinfo | less

```
and take a look at the third line (direct rendering).  Does it say "Yes"?

You may need to do some mucking around with video card drivers (though Compiz runs, so...).  It would be helpful if you posted the chipset of your graphics card.Yes it does.  Exactly what kind of mucking around do I have to do?  And what do you mean by "graphics card chipset?"

> **chronographer said:**
> From my experience (admittedly limited) I would recommend you play games in windows. if you want to play games on Linux, turn off compiz ("metacity --replace") then when you're finished playing games, turn it back on again "compiz --replace". I tried dual monitor with my new radeon card, then new official drivers support dual screens, easily using "aticonfig" but I like using the open source drivers, which work with with compiz and xrandr to put a picture on my tv temporarily (like when I watch a movie).

So bottom line... try installing proprietary (restricted) drivers, mess around with aticonfig and xorg.conf to get games and productivity working. Or. Use Ubuntu for work, xp for play.I wish I could play on XP, but considering that my laptop's internal hard drive is fried, I can't even install XP (unless you know of a way to get it to install properly on a USB hard drive).

Oh, and I never knew about ATi config.  How can I use it to turn off my laptop's display and use only my external LCD?  And why don't the settings in "Screen Resolution" work anymore?

---

### Post by S1xp4ck on 2008-06-11
I use the Compiz Switch App for games.  When installed you can pin to your desktop or panel and it will instantly toggle your compiz on or off for game playing.

[http://forlong.blogage.de/article/pages/Compiz-Switch](http://forlong.blogage.de/article/pages/Compiz-Switch)

---

### Post by Psythik on 2008-06-13
Thanks for that, but Steam games still won't run, and I still can't get any sound in *any* Wine app, let alone games.

---

### Post by markbuntu on 2008-06-13
Pulseaudio has some issues with wine. Try switching your Sound preferences to alsa instead of automatic.

---


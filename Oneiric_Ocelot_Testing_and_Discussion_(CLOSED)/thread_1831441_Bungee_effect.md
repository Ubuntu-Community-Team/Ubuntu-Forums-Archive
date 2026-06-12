---
title: "Bungee effect"
date: 2011-08-23
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by coffeecat on 2011-08-23
Try this in Natty Unity: click and hold on the title bar of a window. Move it around. Move it up and down quickly. Nothing remarkable there. The mouse cursor stays in place where you clicked and the window moves around in time with your hand movement.

Now try it in Oneiric. If you are seeing what I am seeing - weird, isn't it? The window moves around behind the cursor as though the two are connected with a bit of elastic. Moving it up and down nearly gives me motion sickness.

That's with a permanent installation of Oneiric with an ATI card and open source driver - 3d just fine. And also running from the live USB on a machine with Intel graphics and another where I temporarily fitted a nvidia 8400GS card. That latter was with the default nouveau driver and was the most laggy of the lot - which I'm not surprised about.

I guess this is a compiz issue, but I can't find anything in ccsm that would appear to be relevant. To those who are using a proprietary driver: are you seeing this? I tried installing the fglrx driver in my Radeon HD5450 system, but the result was a disaster (nothing new there then! :rolleyes:).

---

### Post by sgage on 2011-08-23
Not seeing it here:

Oneiric 32-bit, nvidia-current proprietary drivers.

---

### Post by fjgaude on 2011-08-23
Mouse and program locked together as the mouse is moved rapidly taking the window with it.

Latest build, x64, 3D, on my main box, Intel i5, GMA HD graphics. Notice signature.

---

### Post by coffeecat on 2011-08-23
Thanks for the feedback.

Since there was a spare partition on the machine I'd put the GeForce 8400GS into, I installed Oneiric from today's daily live. First boot into the installation and the bungee effect is very noticeable. Also associated with a general lagginess - very bad when typing into the terminal. I installed nvidia-current and rebooted and things are much better, although there is still a slight dis-synchrony between the cursor movement and window movement.
 
> **sgage said:**
> Not seeing it here:

Oneiric 32-bit, nvidia-current proprietary drivers.

Which nvidia card is that? The 8400GS is getting on a bit now.

> **fjgaude said:**
> Mouse and program locked together as the mouse is moved rapidly taking the window with it.

Latest build, x64, 3D, on my main box, Intel i5, GMA HD graphics. Notice signature.

Sounds like a fairly recent Intel chipset. The Intel graphics I tried is about 3 years old now.

Re the general lagginess. This is what I also noticed on my main machine with ATI graphics although not nearly as bad as with the nouveau driver. I've only noticed it recently, so perhaps a recent update has introduced this. Clearly some issue somewhere between the video driver and compiz.

---

### Post by ventrical on 2011-08-23
Yes.. I have it slightly with wobbly windows. I think it's neat and does not make me sick. I think there was a problem with compiz and the windows titles not showing up. That has been fixed (here) but there is a sort of a bug (mabey I should start another thread) where there is a sawtooth between the top title bar of each window and the main window field, as if it was actually patched together.

---

### Post by ventrical on 2011-08-23
If you look closely at the title bar you can see the sawtooth/line and bungee effect.

[http://www.youtube.com/watch?v=607X127yTSU](http://www.youtube.com/watch?v=607X127yTSU)

---

### Post by Quackers on 2011-08-23
I have that effect just slightly. As you move a window the cursor/pointer can actually move outside and ahead of the window being moved.
Not annoying though :-) Just a bit different.

---

### Post by lucazade on 2011-08-23
> **coffeecat said:**
> Try this in Natty Unity: click and hold on the title bar of a window. Move it around. Move it up and down quickly. Nothing remarkable there. The mouse cursor stays in place where you clicked and the window moves around in time with your hand movement.

Now try it in Oneiric. If you are seeing what I am seeing - weird, isn't it? The window moves around behind the cursor as though the two are connected with a bit of elastic. Moving it up and down nearly gives me motion sickness.

That's with a permanent installation of Oneiric with an ATI card and open source driver - 3d just fine. And also running from the live USB on a machine with Intel graphics and another where I temporarily fitted a nvidia 8400GS card. That latter was with the default nouveau driver and was the most laggy of the lot - which I'm not surprised about.

I guess this is a compiz issue, but I can't find anything in ccsm that would appear to be relevant. To those who are using a proprietary driver: are you seeing this? I tried installing the fglrx driver in my Radeon HD5450 system, but the result was a disaster (nothing new there then! :rolleyes:).

I've noticed this behaviour only in Oneiric, if you move the mouse quickly the window moves with a notable delay, like an elastic movement.
This happens only with my intel gma500 card, tried on other machines (nvidia 250gts 1gb, ati 3200 hd, ati 7500 mobility) but this issue is not present. In natty instead was always quite fast.
Don't know how much related to compiz itself.. I get this in unity2d with metacity compositor enabled, disabling it is fast, so maybe related to opengl extensions.

---

### Post by ventrical on 2011-08-23
Yes.. because I have the same with Lucid with compiz running.

---

### Post by mc4man on 2011-08-23
> **coffeecat said:**
> 
Now try it in Oneiric. If you are seeing what I am seeing - weird, isn't it? The window moves around behind the cursor as though the two are connected with a bit of elastic. Moving it up and down nearly gives me motion sickness.

I guess this is a compiz issue, but I can't find anything in ccsm that would appear to be relevant. To those who are using a proprietary driver: are you seeing this? I tried installing the fglrx driver in my Radeon HD5450 system, but the result was a disaster (nothing new there then! 
Did see that exactly for a short time, maybe around A2 (nvidia, either 7800 OC or 8400m), not lag or delay but as you say like a bungee
Did go away, probably from a re-install

Overall compiz, putting aside it's performance and mem issues, does still  seem  very inconsistent. For ex. here windows generally open and close fine, then out of the blue there'll be some lag.

So I've now taken to using just the min. plugins needed & a few add. I want, (there are certainly some default enabled that should be dropped 
currently - 
 > gconftool-2 --get  /apps/compiz-1/general/screen0/options/active_plugins
[core,composite,opengl,decor,move,gnomecompat,compiztoolbox,
regex,mousepoll,place,text,cube,vpswitch,scale,resize,rotate,expo,scaleaddon,unityshell]

If anything's going to kill unity it won't be design, it'll be compiz

---

### Post by ventrical on 2011-08-23
Then why not just develop a compiz desktop environment?

---

### Post by coffeecat on 2011-08-23
> **lucazade said:**
> I get this in unity2d with metacity compositor enabled, disabling it is fast, so maybe related to opengl extensions.

Interesting. I didn't think to try it on the other desktops. This with my main machine with Radeon HD5450 and ati/radeon driver where I first noticed this. I get a pronounced bungee effect in Unity 3d, and absolutely no bungee effect or lag in Unity 2d or gnome-session-fallback - the mouse cursor and window title bar stay glued together. In gnome shell, if I try very hard, I can just get the window to lag slightly behind the cursor, but I wouldn't have noticed this if I hadn't seen it in Unity 3d. Everything is fine with this card and the ati/radeon driver in Unity 3d in Natty.

> **ventrical said:**
> If you look closely at the title bar you can see the sawtooth/line and bungee effect.

[http://www.youtube.com/watch?v=607X127yTSU](http://www.youtube.com/watch?v=607X127yTSU)

Thanks. I'll have a look when I'm next in Natty, since the flash plugin is broken in Oneiric at the moment! Ironic. :|

---

### Post by godhika on 2011-08-23
I have seen this on my old laptop (which broke a week ago, so i can't test this now) also with an ati card. fglrx and unity diddnt work with unity at all, but i found that changing in ccsm from active blur to static blur in the unity plugin solved the bungee-windows-issue.

---

### Post by coffeecat on 2011-08-23
> **godhika said:**
> i found that changing in ccsm from active blur to static blur in the unity plugin solved the bungee-windows-issue.

Thanks. Changing to either no blur or static blur reduces the bungee effect to almost nothing. It also solves the slight but distracting lag with other things - mouse clicks, typing - and makes the desktop feel more responsive.

Interestingly, the Unity plugin in Natty only gives you no blur and static blur - no active blur.

To be honest, I can't quite see what the different blur effects are doing to the dash. The colour is more intense with active blur, but I can't see any other difference.

---


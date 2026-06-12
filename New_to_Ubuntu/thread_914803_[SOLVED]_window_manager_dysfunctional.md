---
title: "[SOLVED] window manager dysfunctional"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by Elephantman5 on 2008-09-09
I installed through cli with the minimal installation cd for ubuntu in order to customize.
The problem is, 

I don't know what I'm doing. :)
So, funny as it may seem. I install: synaptic, gdm, blackbox, xorg.

I like how, everywhere I've looked, people tell you to sudo apt-get install x-window-manager. And yet, this command doesn't even work. So, the terminal asks you what to pick. Ok. Fun. I picked one.
Black box.
I've already installed blackbox. But I'm not seeing anything. I restarted. I tried doing this without gdm installed...
Still not seeing this window manager I supposedly installed. (did the themes too)
I tried openbox. I tried flux box. 
Eventually, after realizing the inept futility of the situation, I began muddling around with all the different kinds.
They're even better to experience when everything you install is not visible. Guess what? I've got Blackbox on my system.
Can't see it, but it's there I promise you.

---

### Post by urukrama on 2008-09-09
Are you sure blackbox doesn't load? Blackbox, like Openbox, doesn't come with fancy desktop effects (including wallpapers), and if you are not used to that, it seems it just loads a blank screen. Right click and you have your root menu. That is Blackbox.

I strongly suggest you use Openbox, though. Blackbox hasn't been developed for years now, and Openbox will provide you a much nicer experience and since many people here use it, you'll find a lot of support for Openbox on these forums.

Have a look at my guide for Openbox (link in my signature). It should 
help you install and set up Openbox.

---

### Post by Elephantman5 on 2008-09-09
> **urukrama said:**
> Are you sure blackbox doesn't load? Blackbox, like Openbox, doesn't come with fancy desktop effects (including wallpapers), and if you are not used to that, it seems it just loads a blank screen. Right click and you have your root menu. That is Blackbox.

I strongly suggest you use Openbox, though. Blackbox hasn't been developed for years now, and Openbox will provide you a much nicer experience and since many people here use it, you'll find a lot of support for Openbox on these forums.

Have a look at my guide for Openbox (link in my signature). It should 
help you install and set up Openbox.
Origionally I tried to install openbox.
Basically all I have to work with is the terminal on the left of the screen. And when I open firefox or any window through terminal, it has no top on it. You know, the x, and stuff.
I'll look at your guide

---

### Post by Elephantman5 on 2008-09-09
K. Don't understand why this won't work. Isn't this sufficient:?
xorg, xterm gdm, menu, gksu, synaptic, openbox

dpkg-reconfigure xserver-xorg

???

I'm following the minimal guide you linked to.
What else is there to install that I'm obviously missing?

_edit.
Ok. Well I'm in it now, I think. I guess it was the second command that did it. I don't know.
Is there a way I can change the splash screen? Do I need GNOME display manager?

---

### Post by zeththedarkmage on 2008-09-09
I had a similar problem, if it still isn't working going to system>administration>hardware drivers and make sure you have everything installed. For me it was simply I needed the drivers to properly run the effects.

---

### Post by snowpine on 2008-09-09
(edit) Never mind, I see your problem is solved. :)

---

### Post by Elephantman5 on 2008-09-09
> **zeththedarkmage said:**
> I had a similar problem, if it still isn't working going to system>administration>hardware drivers and make sure you have everything installed. For me it was simply I needed the drivers to properly run the effects.
But there was no option for Hardware drivers. I was working with synaptic, and picking out gnome apps like a cherry picker. And aligning them along with the openbox.

It's A LOT easier to do all this with an already installed system. I just went back to normal, can't handle it.

---

### Post by urukrama on 2008-09-09
> **Elephantman5 said:**
> Is there a way I can change the splash screen? Do I need GNOME display manager?

I think you can change the splash screen, but I never use it. I prefer text over image when I boot (I don't have usplash installed).

You don't need GDM, and you can easily do without it if you prefer so. In that case, you'll login on a console (text mode) and then start X with the command "startx". You'll need to 
use your ~/.xinitrc to specify what applications (including window managers or desktop environments) load when you log in. See [this page]("https://wiki.ubuntu.com/CustomXSession") on the wiki for more info.

---

### Post by Elephantman5 on 2008-09-09
> **urukrama said:**
> I think you can change the splash screen, but I never use it. I prefer text over image when I boot (I don't have usplash installed).

You don't need GDM, and you can easily do without it if you prefer so. In that case, you'll login on a console (text mode) and then start X with the command "startx". You'll need to 
use your ~/.xinitrc to specify what applications (including window managers or desktop environments) load when you log in. See [this page]("https://wiki.ubuntu.com/CustomXSession") on the wiki for more info.

Oh cool! Thanks, I bookmarked it.

---


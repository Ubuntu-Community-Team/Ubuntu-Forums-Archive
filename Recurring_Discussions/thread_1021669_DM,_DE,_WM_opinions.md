---
title: "DM, DE, WM opinions?"
date: 2008-12-25
forum: Recurring Discussions
---

### Post by Mulenmar on 2008-12-25
DM being Display Manager (GDM, KDM, XDM, WDM, Enter, Orthos, SLiM, etc),
DE being Desktop Enviroment (GNOME, KDE, Xfce)
WM being Window Manager (many examples)

I've always used either GNOME or Xfce, having found Kubuntu not to my liking (might still install a KDE session on my next megainstall), but I'm wanting to try some other options.

So, I could use some advice on what you consider the best comboniation of login manager + final user enviroment is. 
Here are the combos I'm considering trying:

KDM login, Xfce with Xfce, KDE, GNOME apps (in that order of preference) for my AMD dual-core 2GB mem rig

WDM login, Fluxbox WM with Xfce, GNOME apps for my eMachines (good CPU but  256MB mem)

Anyone else used these combos, how did they work? Anyone used the SLiM login manager, or the ROX Desktop Manager, and how was your experience? (They're not in the repos, I know)
Opinions, suggestions, objective bashing? :popcorn:

---

### Post by Mulenmar on 2008-12-25
Ugh, majorlly wrong subforum. Sorry! I'll repost in General Help...:redface:

---

### Post by Mulenmar on 2008-12-25
DM being Display Manager (GDM, KDM, XDM, WDM, Enter, Orthos, SLiM, etc),
DE being Desktop Enviroment (GNOME, KDE, Xfce)
WM being Window Manager (many examples)

I've always used either GNOME or Xfce, having found Kubuntu not to my liking (might still install a KDE session on my next megainstall), but I'm wanting to try some other options.

So, I could use some advice on what you consider the best comboniation of login manager + final user enviroment is. 
Here are the combos I'm considering trying:

KDM login, Xfce with Xfce, KDE, GNOME apps (in that order of preference) for my AMD dual-core 2GB mem rig

WDM login, Fluxbox WM with Xfce, GNOME apps for my eMachines (good CPU but  256MB mem)

Anyone else used these combos, how did they work? Anyone used the SLiM login manager, or the ROX Desktop Manager, and how was your experience? (They're not in the repos, according to Synaptic)
Opinions, suggestions, objective bashing? :popcorn:

---

### Post by saulgoode on 2008-12-25
I don't use a DM on my main machine; 'startx' works just fine and is more flexible switching run levels (I do a lot of graphical development). I have some remote machines in my house on which I have either KDM or XDM running -- I don't care which one (XDM does not allow session changing but I don't find I need that). I understand SLiM does not support remote X logins so it is useless for my purposes.

I don't use a DE, at least not in the traditional sense (every desktop technically has an environment).

I use UWM for my window manager. It is sort of the polar opposite of a tiling WM, though even more lightweight. I am constantly resizing and repositioning windows, but the WM makes this trivially simple and ergonomic.

---

### Post by albinootje on 2008-12-25
> **Mulenmar said:**
>  Anyone else used these combos, how did they work? Anyone used the SLiM login manager, or the ROX Desktop Manager, and how was your experience? (They're not in the repos, according to Synaptic)

DE : I use Gnome, because I like the combination of theming, icons, panel.
I don't feel so comfortable with XFCE4 unless it's tweaked properly.
Years ago I've used KDE for a long time, but I started to like Gnome better.

DM : gdm
Although gdm has a few annoying little bugs, I have sticked with it.
I've tried SLiM, kdm and wdm in the past, but didn't like it enough to replace gdm.
I liked the idea and screenshots of [http://qingy.sourceforge.net/](http://qingy.sourceforge.net/) a lot, but couldn't get that to work properly.
I've never heard of "Enter" and "Orthos", do you have urls for those ?

WM: I use the default metacity with Gnome. 
Years ago I liked icewm and WindowMaker a lot. Later I met some fluxbox fanatics, it was nice to see their customizing with it.

---

### Post by smartboyathome on 2008-12-25
DE: None. See below.
WM: E17. Technically it is a WM but is more like a desktop shell on Windows, with modules which extend its functionality.
DM: Again, none. Since I am the only user on my laptop, I just set it to automatically log in at boot without a DM (see [here]("http://wiki.archlinux.org/index.php/Start_X_at_boot#Starting_X_as_preferred_user_without_logging_in") for how I did it). I'm getting a new USB drive in the mail anyway, so once I get it I can use it as a "key", with my boot partition stored on it, so that you can only boot up my laptop if it's plugged in. I may even encrypt my root partition (since my boot partition will already be separate) so that if someone gets my laptop, they will only get the hardware, not any info.

---

### Post by MaindotC on 2008-12-25
I've never taken the time to understand precisely what I have or what others there are.  I've just stuck with whatever is the default, like I believe I have Gnome with metacity and whatever desktop effects is called - compiz-fusion I believe.  I've always taken this for granted and just never really delved into these things you speak of like E17, SLiM, or Orthos.  But I may google them sometime now that you mentioned it.  So many choices for Linux...possibilties are endless.

---

### Post by handy on 2008-12-25
I don't use a DM either.

I have edited ~/.xinitrc & just login which starts Xfce on Arch.

---

### Post by OutOfReach on 2008-12-25
No login managers for me, I think they're overrated.

I just login into the console and I execute 'startx' which starts either KDE or Openbox depending on my mood.

Anyways, handy thanks for reminding me that I need to change it so it'll start X once I log into the console.

---

### Post by hessiess on 2008-12-26
Dwm

---

### Post by kerry_s on 2008-12-26
dm = none, i use rungetty and .profile to auto log in.
de = none, i prefer a window manager on a custom install.
wm = jwm, it's my favorite, i don't even bother with anything else.

---

### Post by hrod beraht on 2008-12-26
[LIST]
[*]DM: None, just console login. If I had to pick a graphical login manager, it would be SLiM.
[*]DE: None, the all-in-one thing tends to be to bloated. Although, I do use XFCE's Thunar file manager.
[*]WM: Openbox, no panel.
[/LIST]

Bob

---

### Post by ushimitsudoki on 2008-12-26
SliM + XFCE + Compiz

This combo has been working out pretty good for me on my desktop.

---

### Post by p_quarles on 2008-12-26
> **Mulenmar said:**
> Ugh, majorlly wrong subforum. Sorry! I'll repost in General Help...:redface:

Threads merged. Please don't start a new thread when something just needs to be moved. Ask someone to move it.

And, no, General Help is not the right place for a thread like this.

---

### Post by Eisenwinter on 2008-12-26
I don't use a DM, I only use a standalone Openbox, which is configured to start up in ~/.xinitrc

---

### Post by Mark76 on 2009-01-10
SLiM for DM, Rox-Session for DE and Openbox for WM.

Setting up SLiM to start ROX-Session can be tricky, mind.

---

### Post by Tux Aubrey on 2009-01-10
Like smartboyathome, I use e17 as my desktop but have gdm to manage login and multiple sessions (I sometimes have several users on a machine).

---

### Post by sertse on 2009-01-10
DM: None (good old startx :) )
DE: None
WM: Fluxbox. 

Anyone know how make it auto login? Single/sole user; Want to skip even typing my login and pass.

---

### Post by Rokurosv on 2009-01-11
Fluxbox + startx, that's all I need :D

---

### Post by RiceMonster on 2009-01-11
No login manager + xfce4

or sometimes its openbox (with no de, of course).

---

### Post by cardinals_fan on 2009-01-11
DM: Slim or none
DE: Usually none, but Xfce is my favorite
WM: dwm (but I'm on Fluxbox at the moment)

---


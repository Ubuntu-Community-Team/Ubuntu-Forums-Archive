---
title: "Where does xrandr put its settings?"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by inanutshellus on 2008-07-14
I used the "xrandr" command to set up my dual monitor setup on my laptop, then checked that it worked undocked, and it did, but when I redocked all my settings were gone!

Since xrandr doesn't change xorg.conf, grabbing my (unchanged) backup file was useless... So what the heck *should* I have backed up? What does xrandr change? Why is it so $&&#&(#! fragile?

---

### Post by tamoneya on 2008-07-14
im guessing it is probably ~/.xrandr/

---

### Post by Delkster on 2008-07-14
> **inanutshellus said:**
> What does xrandr change?

As far as I know, it doesn't.

Xrandr is used to change certain display settings on the fly, switching between different configurations supported by the X setup. For example, if you don't have a certain display mode configured for X (in xorg.conf), you can't switch to that display mode using xrandr.

As far as I understand, any permanent changes, including the addition of new modes and the selection of default ones, need to be done elsewhere, e.g. xorg.conf (or perhaps in some kind of Gnome configuration, because Gnome can at least to some extent switch to the desired mode automatically when it gets control of things after login).

If you used xrandr on the command line, have you tried if **System > Preferences > Display Resolution** has the options you need? I haven't tried but I'd expect that the settings made using that control panel should be automatically applied to subsequent sessions after login.

---

### Post by inanutshellus on 2008-07-14
> **Delkster said:**
> As far as I know, it doesn't.

Xrandr is used to change certain display settings on the fly, switching between different configurations supported by the X setup.

So why use it then, if you can't get consistent results using it? Well, I guess if I were on a desktop instead of a laptop that I undocked, my X configuration wouldn't change... But it's pretty annoying to have this awesome little tool that is xrandr set up your screen perfectly then have it change its mind the next time you boot up in a different hardware environment.

---

### Post by Delkster on 2008-07-15
> **inanutshellus said:**
> So why use it then, if you can't get consistent results using it?
You get consistent results, but they're only used for the session, not stored for subsequent ones automatically.

> But it's pretty annoying to have this awesome little tool that is xrandr set up your screen perfectly then have it change its mind the next time you boot up in a different hardware environment.
Perhaps you could include the xrandr command in a script somewhere that is executed automatically after your user logs in?

Did you try the GNOME screen resolution control panel already? If it has enough settings to produce a setup you need or want, it'll probably do the "automatically re-apply for next session" part for you.

Or did I misunderstand the problem? Is it somehow specific to losing settings when the physical display setup is changed, not between logins?

---

### Post by panosy on 2008-11-18
Well you can either modify xorg.conf according to results verified by xrandr (to avoid restarting X till you get proper settings)

OR placing a startup script in /init/rc.d executing the proper xrandr command

OR aliasing the proper xrandr settings in your .bashrc (or which shell you use) like someone suggested in another thread (don't remember which) like that:

alias single='xrandr --output VGA-0 --off'
alias clone='xrandr --output LVDS --auto --output VGA-0 --auto --same-as LVDS'
alias dual='xrandr --output LVDS --mode 1280x800 --pos 0x0 --output VGA-0 --mode 1280x1024 --right-of LVDS'

after that you can place a line with the config you prefer, for example "dual". This way first time you run a console you get the proper config (no flickering next time you open one don't worry)

hope this helps

---

### Post by sergiovalenzuela on 2009-09-12
I believe **System > Preferences > Display Resolution** saves the settings in **~/.config/monitors.xml**

---

### Post by jprupp on 2010-07-21
Thank you sergiovalenzuela,

I've been looking for this configuration file for some time now.

---

### Post by jtarin on 2010-07-21
[To set up and persist]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html")

---

### Post by roMancer on 2011-07-09
hi there, 
on Fedora 15 LXDE, I put the xrandr command line into:
/etc/lxdm/PreLogin

---


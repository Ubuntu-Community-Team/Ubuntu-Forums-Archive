---
title: "Contents of original 'autostart' file?"
date: 2012-04-11
forum: New to Ubuntu
---

### Post by TheRealJimT on 2012-04-11
OK, I've done my due diligence and performed the 'Search', both in the forum and across the entirety of the InterWebs.  I shall ask my question, then will explain why I am asking:

What is the default content of the /etc/xdg/Lubuntu/autostart file?

Long story explanation that is probably boring and unecessary:

I am trying to set up an old eMachines (AMD Sempron 2.1 GHz, 768 MB RAM) as a media box to play videos and music while connected to my TV.  I set up Lubuntu 11.10 successfully, and everything appeared to be working as I wanted.
Then...
I wanted VNC access, and started following some instructions to get X11VNC to run at startup.  The instructions themselves are fine, it's just my incompetence that - using vi - removed two or three lines from the autostart file, subsequently saving and closing the file.  I was hoping to find a copy of a default, virgin autostart file somewhere so that I could see what I removed.  The machine is just sitting there now, and I'm afraid to reboot it as I don't know what won't be started automatically.

So...  beyond my own recognition of ignorance and recklessness, how bad off am I?

(Note:  I'm somewhat technically proficient, I just freakin hate vi.)

With humble regards,

TheRealJimT

---

### Post by chamber on 2012-04-11
Not 100% sure as I've never used lxde however the mint lxde livecd has the following,

```
@setxkbmap -option terminate:ctrl_alt_bksp
@lxpanel
@xscreensaver
@pcmanfm --desktop
@gnome-power-manager
```

I would not trust these settings though as the path is different,

running from /etc/xdg/lxsession  

What you could do is run a quick install in a vm and have a look at the virgin autostart file or wait until someone who knows better has a look.

---

### Post by cortman on 2012-04-11
Doesn't vi create a backup file with a ~ suffix, like Gedit and Emacs? Check the /etc/xdg/Lubuntu/ folder.
Not a vi fan here either. Emacs makes more sense to me.

---


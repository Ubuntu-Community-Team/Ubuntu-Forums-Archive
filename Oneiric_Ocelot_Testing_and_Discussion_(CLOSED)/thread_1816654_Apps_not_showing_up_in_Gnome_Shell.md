---
title: "Apps not showing up in Gnome Shell"
date: 2011-08-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sgage on 2011-08-02
For the last couple of weeks (not exactly sure), apps that I've installed don't show up in Gnome Shell. Not in the Applications area of the Dash, not in the Applications lens, not even in Alt-F2 - if I type the command name, it says "not found", if I type in complete path, the run command box just freezes.

If I reinstall a package, it shows up as you'd expect, but this does not survive a log out/log in cycle.

What gives? Where does GS keep track of apps? I see appropriate .desktop files for the un-findable apps in both /usr/share/applications and /usr/share/app-install. 

I'd like to keep testing GS, but it's a real pain having to open a terminal to launch programs!

TIA

---

### Post by mc4man on 2011-08-02
I've seen that also and on a much lesser scale in unity.
Can't offer a real solution, hopefully time will fix.

What you can do for the moment is copy the missing app's  .desktop to ~/.local/share/applications, then it will always show (pretty much..

---

### Post by sgage on 2011-08-02
> **mc4man said:**
> I've seen that also and on a much lesser scale in unity.
Can't offer a real solution, hopefully time will fix.

What you can do for the moment is copy the missing app's  .desktop to ~/.local/share/applications, then it will always show (pretty much..

Thanks - I'm content just to have a workaround for now, so I can continue testing GS without going nuts...

---

### Post by lucazade on 2011-08-02
this should be the bug report and I thought it was already fixed (don't know if gshell rely on this)
[https://bugs.launchpad.net/bugs/798951](https://bugs.launchpad.net/bugs/798951)

---

### Post by mc4man on 2011-08-02
If any in particular maybe post name - there may also be an edit to the .desktop that could allow being found in GS, though the whole deal seems to be a moving target of sorts

---

### Post by mc4man on 2011-08-02
> **lucazade said:**
> this should be the bug report and I thought it was already fixed (don't know if gshell rely on this)
[https://bugs.launchpad.net/bugs/798951](https://bugs.launchpad.net/bugs/798951)
That was fixed a ways back and completed  yesterday for  - alacarte fixed.

---

### Post by sgage on 2011-08-02
> **mc4man said:**
> If any in particular maybe post name - there may also be an edit to the .desktop that could allow being found in GS, though the whole deal seems to be a moving target of sorts

Well, copying the .desktop file to ~/.local/share/applications seems to work for every one I've tried. 

E.g., audacious2.desktop exists in /usr/share/applications, but is not discoverable by GS, but if I copy it to local, it works. If I remove it from local, it no longer works. Why would GS find it in local but not in usr, where it finds any number of other apps?

---

### Post by mc4man on 2011-08-02
audacious I don't know, shows up here though I have 2 - one in ~/.local named Audacious Cd Player that I created and the normal one in /usr 
Both show up
Maybe a variance in installs, mine's from Sun. evening

An ex. of 2 where .desktop makes a difference 
dconf-editor doesn't show up in GS, removing or editing this line to false and it shows
NoDisplay=true

gnome-tweak-tool doesn't show  in unity, editing this line adding blue and then it does
OnlyShowIn=GNOME;[COLOR="Blue"]Unity;[/COLOR]
Now this is here, for other installs maybe these show, no consistency yet other than ~/.local

---

### Post by sgage on 2011-08-02
> **mc4man said:**
> audacious I don't know, shows up here though I have 2 - one in ~/.local named Audacious Cd Player that I created and the normal one in /usr 
Both show up
Maybe a variance in installs, mine's from Sun. evening

An ex. of 2 where .desktop makes a difference 
dconf-editor doesn't show up in GS, removing or editing this line to false and it shows
NoDisplay=true

gnome-tweak-tool doesn't show  in unity, editing this line adding blue and then it does
OnlyShowIn=GNOME;[COLOR="Blue"]Unity;[/COLOR]
Now this is here, for other installs maybe these show, no consistency yet other than ~/.local

There is no OnlyShowIn or NoDisplay entry in any of the .desktop files I've tried. Even the rhythmbox.desktop file does not have those entries. But then neither do .desktop files that work fine from usr.

Too weird - like you said, a moving target.

---

### Post by mc4man on 2011-08-02
An update/re-install should overwrite an existing .desktop? Those 2 examples where as delivered on Sun's  iso

 Another one here
software-properties doesn't show in Gs - this is the 'problem' line
```
Categories=GNOME;GTK;Settings;X-GNOME-SystemSettings;X-GNOME-Settings-Panel;
```
Without trying all the combo's this allows it to show
```
Categories=GNOME;GTK;Settings;
```
More just a curiosity/exercise in .desktop's, .local is much simpler till unity and GS get on the same page, if ever

Edit: if curious you could always try a purge and install of the prior 2 and see what happens

---

### Post by jfernyhough on 2011-08-02
If this is the same problem as I had with a clean oneiric install, then installing gnome-shell, it's down to lightdm not setting the session type correctly. As such, the correct menu list is not loaded.

I'm looking for the post I made which solved this; until I find it you essentially have to link applications.menu to gnome-applications.menu, e.g.:

$ sudo ln -s /etc/xdg/menus/gnome-applications.menu /etc/xdg/menus/applications.menu

Ah, here it is: [http://ubuntuforums.org/showthread.php?t=1787104](http://ubuntuforums.org/showthread.php?t=1787104)

My memory worked - amazing. :D

---

### Post by mc4man on 2011-08-02
> **jfernyhough said:**
> If this is the same problem as I had with a clean oneiric install, then installing gnome-shell, it's down to lightdm not setting the session type correctly. As such, the correct menu list is not loaded.
$ sudo ln -s /etc/xdg/menus/gnome-applications.menu /etc/xdg/menus/applications.menu

The issue with the gnome-applications menu for gnome-shell was fixed in link lucazade provided (gnome-applications.menu was removed in favour of applications.menu

This has more to do with some diff's on how .desktop entries are treated and different categories, and possibly what is the last listed


Using  software-properties as an example
If edited as shown above then in Gs > applications it will show in the 'other' category

If I change it to this it will then show in the system category instead
Categories=GNOME;GTK;System;
So it would appear some balance is needed between what works best in unity and GS, obviously unity comes first. In this case both would be fine if whatever was on the Categories= line ended in System;

(lumping gnome-fallback in w/ Gs and unity-2d w/ unity

---

### Post by sgage on 2011-08-02
> **mc4man said:**
> I wonder if an update/re-install overwrites an existing .desktop? Those 2 examples where as delivered on Sun's  iso

 Another one here
software-properties doesn't show in Gs - this is the 'problem' line
```
Categories=GNOME;GTK;Settings;X-GNOME-SystemSettings;X-GNOME-Settings-Panel;
```
Without trying all the combo's this allows it to show
```
Categories=GNOME;GTK;Settings;
```
More just a curiosity/exercise in .desktop's, .local is much simpler till unity and GS get on the same page, if ever

Edit: if curious you could always try a purge and install of the prior 2 and see what happens

Completely purging, e.g., audacious and then re-installing it allows GS to discover it as expected, until you log out/log in, and then it's gone again.

OK, so I went into the audacious2.desktop file (in usr), and added GNOME to categories, and it worked!

So I went to check out the rhythmbox desktop file, and it already had GNOME in there, and it wouldn't work. But when I moved GNOME to the end of the categories line, it worked!

None of my other "problem" desktop files had GNOME in the categories, and when I added it in at the end of the line, they all worked as expected.

Now I'm assuming that this will survive a log out/log in cycle. Let's see...

NO! WTF? The GNOME entry is still there. This is crazy - I'll just move 'em to .local and forget about for a while :-)

---

### Post by mc4man on 2011-08-02
Rhythmbox is fine here in both - shows in  multimedia in unity, sound & video in Gs

The main problem ones here are ones that have 'Settings' or an extended 'Settings-', for many of those "System" works better for both.

Settings = Other in Gs & <whatever> and or "Themes & Tweaks " in unity
I'm sure they'll work it out,

---

### Post by sgage on 2011-08-02
> **mc4man said:**
> Rhythmbox is fine here in both - shows in  multimedia in unity, sound & video in Gs

The main problem ones here are ones that have 'Settings' or an extended 'Settings-', for all of those "System" works better for both.

Settings = Other in Gs & <whatever> and or "Themes & Tweaks " in unity
I'm sure they'll work it out,

Just out of curiosity - are using GS from the repos or from ricotz? GS from ricotz doesn't even load from login for me...

---

### Post by mc4man on 2011-08-02
> **sgage said:**
> Just out of curiosity - are using GS from the repos or from ricotz? GS from ricotz doesn't even load from login for me...
On this install I only use ubuntu sources and packages - no way  or not comfortable filing bugs otherwise
(The 2 exceptions are nautilus-actions and vlc, N-A from O doesn't work and vlc-1.11.1 is ....
Ot - I see a fixed gnome-settings-daemon is here, now I can automount/autoplay cd's

---

### Post by jbicha on 2011-08-02
sgage, I just tested with today's daily CD and I installed gnome-shell and the Applications part of the Activities dash works just fine. All the normal apps show up there.

---

### Post by mc4man on 2011-08-03
A fresh install either now or with A3 would be a good thing, most apps inc. or added show up w/ the exception of the couple I mentioned.
Myself do a new install weekly till beta or so, though that's just personal choice.
Just tried todays dailly live and works quite well - again saw that minor issue with first use of a quicklist or dash - if affected - 

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/819721](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/819721)
May need fixing or may just go away - not that important, just a small glitch

---

### Post by sgage on 2011-08-03
I think I'll probably do a fresh install with A3 tomorrow - I'll also be able to get a sense of the state of the installation routine.

---


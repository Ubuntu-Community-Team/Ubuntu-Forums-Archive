---
title: "Battery icon missing in gnome-shell panel"
date: 2011-07-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-07-15
Using gnome-shell, when I boot up and get to the login screen I see the shtdown icon and the battery icon top right. When I have logged in and get to the desktop the battery icon has gone and it never returns.
Is there a setting I'm missing?

---

### Post by jfernyhough on 2011-07-15
I think this is due to a change in gnome-power-manager. I have exactly the same issue running GNOME3 both in gnome-session-fallback in Oneiric and gnome-panel 2.3 in Natty.

In GNOME3 I have a not-found icon, with gnome-panel I have a blank space (screenshot).

I too would love to get this fixed. :)

(Possibly similar is that nm-applet has no icon in gnome-session-fallback either for me)

---

### Post by wojox on 2011-07-15
I don't know? I'm missing everything on the left hand panel and in applications. I had to switch back over into Unity. :P

---

### Post by mc4man on 2011-07-15
Shows here - 
You could check something in dconf-editor, though I find it can have graphic glitches in some settings so I use gsettings instead

Ex. - see what this says
```
gsettings get org.gnome.power-manager icon-policy
```
These are the available values - always is 'present'

> :~$ gsettings range  org.gnome.power-manager icon-policy
enum
'present'
'charge'
'low'
'critical'
'never'
So if not on what you'd like than set as such, ex. setting to present
```
gsettings set org.gnome.power-manager icon-policy present

```
If not this then maybe just another inconsistency of present state...

---

### Post by Quackers on 2011-07-15
The output of the line is 
'present'
but no icon shows.

---

### Post by mc4man on 2011-07-15
Not sure then - shows fine here
(was not showing in unity but that's been taken care of with todays unity upgrade

Decided to dump the 4 day old A2 install for todays iso. (shows there also), due to some issues with shut down after all those updates the other day.

It works fine with 2 exceptions - 
was pre-warned in a bug I placed on lightdm that lightdm has gone from semi to very broken
So on todays iso there is no password box for any user, one can use 'other' or install/switch to gdm, I switched, but now use lightdm - gdm has bigger issues here.
The wireless icon doesn't respond to l. click, had to set up thru the edit menu.

additionally
gnome-shell is ok - fairly full apps list in lenses
zeitgeist in unity does nothing ...
There is a continuing 'stuck' cursor issue for touchpads, may be very annoying to some like myself, will link bug report if interested (fair degree of absurdity there
vlc can cause a fairly serious xserver issue if opening things like playlist, tools > pref.'s ect. due to default qt gui (at least on nvidia
And more...

---

### Post by Quackers on 2011-07-27
After today's updates I am pleased to report the return of my battery icon in the top panel (gnome-shell) :-)
It's been gone for so long I've incorporated a battery display into my conky!
Nevermind - now I've got 2 :-)

---

### Post by jfernyhough on 2011-07-27
You lucky thing - I'm still without. :D

---

### Post by Quackers on 2011-07-27
Sometimes life just ain't fair :-)

---


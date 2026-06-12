---
title: "File manager crashes in 11.10"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2011-10-14
I upgraded from 11.04 to 11.10 and the file manager crashes frequently.  Specifically if I open home via Ctrl+Tab then try to click to go to another folder it crashes.
It seems to happen more frequently when I try to go to the file system rather than another folder that is inside home.

Has anyone else had this problem?
I'm going to try a clean install and see if that helps.

---

### Post by TeoBigusGeekus on 2011-10-14
Open it with 
```
nautilus
```
from a terminal and post us any error messages you get.

---

### Post by sikander3786 on 2011-10-14
The 'nautilus-open-terminal' has been causing problems for me as well so I just removed it. From Terminal:

```
sudo apt-get remove nautilus-open-terminal
nautilus -q
```

And that did the trick. This package lets you launch the Terminal from any location via the right click menu but it better not sit there if it renders the file browser un-usable. ;)

---

### Post by drs305 on 2011-10-14
[COLOR="DarkRed"]UPDATE 17 Oct 11: The launchpad mailing list indicated this problem has been fixed. Once I updated to *ubuntuone-client-gnome 2.0.1-0ubuntu2* nautilus no longer crashes for me.[/COLOR]

This is a bug which to my knowledge has not been officially solved.

For me, the solution was to uninstall *ubuntuone-client-gnome*. In fact, I just had to perform this operation on my laptop a couple of minutes ago. Disclaimer: I don't use UbuntuOne. If you do, you might want to disregard this 'fix'. Additionally, this works for some users but not for others. What sikander3786 recommends has also worked for some users.
```

sudo apt-get purge ubuntuone-client-gnome
```

---

### Post by GrouchyGaijin on 2011-10-14
Hmmm I hope getting rid of Ubuntu one solves the problem.  I use dropbox so not having Ubuntu one is no big deal.  I really like the open terminal here though, I'd hate to have to remove that.

---

### Post by GrouchyGaijin on 2011-10-14
Thanks Guys,

Removing Ubuntu One seems to have solved the problem.

I have another issue though.  My cursor freezes every once in a while.  Usually when writing email in Gmail or trying to use a menu in a DVD.  Has anyone else had this happen?

---

### Post by mc4man on 2011-10-14
> **GrouchyGaijin said:**
> Thanks Guys,

Removing Ubuntu One seems to have solved the problem.

I have another issue though.  My cursor freezes every once in a while.  Usually when writing email in Gmail or trying to use a menu in a DVD.  Has anyone else had this happen?

Random cursor freeze is an ongoing issue for some myself included - Are you on a laptop using a touchpad?

---

### Post by GrouchyGaijin on 2011-10-14
> **mc4man said:**
> Random cursor freeze is an ongoing issue for some myself included - Are you on a laptop using a touchpad?
Why, yes I am as a matter of fact.

---

### Post by mc4man on 2011-10-14
Currently the cause is not confirmed & it would be great for those seeing this to test a few things.

The easiest 1st test would be to go to System Settings > mouse and touchpad > touchpad & disable the "disable touchpad while typing ' option - screen

Then run as usual for a time frame Longer than what you see this happen & see if it stops
(here that is a couple of days

another test would be to to disable as above but then run the option directly thru syndaemon using the same commands that gnome-settings-daemon uses.
That can be done thru a command at every login or better from creating a startup application to do so.
syndaemon -i 0.5 -K -R

The 3rd would be the same as above but remove a certain option from the command
syndaemon -i 0.5 -K 

The most relevant current bug on - 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/868400](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/868400)

No matter where you'd like to start it would be useful & do report what happens

( the issue with ubuntuone & open-terminal has been fixed with a new ubuntuone-client-gnome package currently in proposed, should be seen in SRU0

---

### Post by GrouchyGaijin on 2011-10-14
> **mc4man said:**
> Currently the cause is not confirmed & it would be great for those seeing this to test a few things.

The easiest 1st test would be to go to System Settings > mouse and touchpad > touchpad & disable the "disable touchpad while typing ' option - screen

Then run as usual for a time frame Longer than what you see this happen & see if it stops
(here that is a couple of days

another test would be to to disable as above but then run the option directly thru syndaemon using the same commands that gnome-settings-daemon uses.
That can be done thru a command at every login or better from creating a startup application to do so.
syndaemon -i 0.5 -K -R

The 3rd would be the same as above but remove a certain option from the command
syndaemon -i 0.5 -K 

The most relevant current bug on - 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/868400](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/868400)

No matter where you'd like to start it would be useful & do report what happens

( the issue with ubuntuone & open-terminal has been fixed with a new ubuntuone-client-gnome package currently in proposed, should be seen in SRU0

Will do.  Are you having the same problem? If so, what did any of these tests show you?
PS What is SRU0?

---

### Post by mc4man on 2011-10-14
> **GrouchyGaijin said:**
> Will do.  Are you having the same problem? If so, what did any of these tests show you?
PS What is SRU0?

I see it here but (un)fortunately it may only happen once every couple of days, or out of the blue several times a session

For 4 days last week I ran with the option disabled, no occurrences

2 days ago I did a new install, got it within 20 sec.'s. Decided to leave the option enabled to see if it re-occurred. Took till today but it did.

So now I'll run for a couple of days thru syndaemon using the default command in a startup app, 
If it re-occurs then I'll try without the -R option

The biggest issue here is how random it is - hard to confirm what the cause is by waiting it out to re-occur or not.

(myself don't need this option & I'm fairly convinced it is the cause - then the question would be is it syndaemon, the options used or g-s-d implementing this.

How often do you get?

A SRU is a stable release update - typically there will be a couple or so, the first one should have some nice fixes inc.  compiz & unity upgrades

---

### Post by GrouchyGaijin on 2011-10-14
> **mc4man said:**
> 

How often do you get?

A SRU is a stable release update - typically there will be several, the first one should have some nice fixes inc.  compiz & unity upgrades

I just upgraded today and have had it happen 3 or 4 times throughout the day.  Always at the worst possible time.

---

### Post by mc4man on 2011-10-14
> **GrouchyGaijin said:**
> I just upgraded today and have had it happen 3 or 4 times throughout the day.  Always at the worst possible time.
That's unfortunate but maybe also good - try disabling the option as in screen and see what happens thru tonight/tomorrow
A logout isn't totally needed but I'd do so anyway

edit:
if it does re-occur this may get it back
Open a terminal (ctrl+alt+t
```
synclient TouchpadOff=0
```

---


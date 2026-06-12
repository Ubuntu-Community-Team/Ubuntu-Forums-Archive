---
title: "What the hell is wrong with Ubuntu?"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by azathrael on 2008-10-22
This is the most random thing that has ever happened in all my life using a computer.

The only thing that catches my mind on what could've been the cause is either me installing Skype (not likely), or me opening xorg.conf and closing without making any changes (again, not likely).

Here's my problem:
My desktop wallpaper seems pixelated, as if my color depth was downgraded.  None of my Advanced Desktop Effects work, and I mean NONE.  When I open the Advanced Desktop Effects Settings everything is configured the way it was before this breakdown and I only have 2 desks instead of 4.

Anyone have any idea what happened to my Ubuntu that made it like this?

---

### Post by mordantae on 2008-10-22
I've also had something similar happen to me before but in my case it has always been after force restarting X (Ctrl+Alt+Backspace)or something similar...although i must admit it has happened straight off a fresh reboot/power-on...i was having some trouble with X at the time...sort of like it was getting buggy? My system would sometimes just fade to a greyed out screen and i'd be stuck there unless i pressed the reboot button **shrug** Never had the wacky desktop colour depth problem but i've had desktop numbers decrease and desktop effects i previously mapped to a shortcut stop working...it was just a case of looking for all the settings i'd configured previously and enabling them though..

---

### Post by azathrael on 2008-10-22
Ok I found the problem.

For some reason I have no idea how, my nvidia graphics driver had been turned off and my visual effects under Appearance had been put on "none".  I have no idea how this could've happened, but what a pain in the ***.

Ubuntu is becoming just as annoying to use as Vista...

---

### Post by dasunst3r on 2008-10-22
What were you doing before this issue appeared?

---

### Post by Kevbert on 2008-10-22
> **azathrael said:**
> Ok I found the problem.

For some reason I have no idea how, my nvidia graphics driver had been turned off and my visual effects under Appearance had been put on "none".  I have no idea how this could've happened, but what a pain in the ***.

Ubuntu is becoming just as annoying to use as Vista...

I had this about two weeks ago and concluded it must have been an 'upgrade' that caused it. Also using Nvidia graphics. There have been a lot of changes to the Nvidia graphics drivers, so maybe one of the old drivers was blacklisted, for some reason.

---

### Post by hyper_ch on 2008-10-22
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse brackets around (each) output. That makes it also easier to read.

---


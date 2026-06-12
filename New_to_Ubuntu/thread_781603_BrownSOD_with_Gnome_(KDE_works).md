---
title: "BrownSOD with Gnome (KDE works)"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by Lord_Davos on 2008-05-04
Hi there,

I'm absolutely new to Ubuntu, but have a very experienced friend who has been able to help so far, although he's stumped now too.

When I log in under Gnome, nothing happens - just a brown screen, mouse control but nothing more.

I've installed KDE and that works absolutely perfectly.

I'm updated everything on my system through apt-get, including getting the latest video card drivers and settings which are what my friend first thought was causing the problems.

I have a Dell Vostro 1400, the video card is an 8400M GS, and ubuntu is booting and running off a USB stick (basically an attempt to have the best of both worlds and have live CD functionality as well as persistance and carrying around a few GB of necessary files with me, so I can work whereever I am). 

I'm looking forward to receiving help: I may not know if I'll prefer gnome to KDE, but I at least want to try them both out.

---

### Post by SunnyRabbiera on 2008-05-04
hmm, are you using kubuntu as opposed to ubuntu?
have you tried to install ubuntu-desktop?

---

### Post by Lord_Davos on 2008-05-04
Yes I'm using ubuntu (8.04), so Gnome was on there as default. I only installed KDE after running out of ideas to get Gnome to work, and to see if it worked (because obviously if it did it at least helped narrow down things that could be wrong).

---

### Post by SunnyRabbiera on 2008-05-04
hmm, have you tried to re install gnome?
it might be possible you had a bad burn of some kind, I assume you had to install KDE via the command line?

---

### Post by Lord_Davos on 2008-05-04
Yeah, I used apt-get: 


would apt-get install ubuntu-desktop   reinstall the ubuntu desktop, or does it need uninstalling first?

---

### Post by halitech on 2008-05-04
you should be able to just install ubuntu-desktop but if it fails, try to remove it first then reinstall it

---

### Post by Lord_Davos on 2008-05-04
Okay, I'm going to go drop out of windows here and reboot into linux and try that, I hopefully won't be back saying "help" in an hour or two!

---

### Post by SunnyRabbiera on 2008-05-04
yeh give it a shot.
at least you know how to make apt work for you though if you need it.
If gnome doesnt work, I would not worry about it as KDE is pretty fair on its own.
Like I said its possible you had a bad burn here, it happens if you use too much speed on it.

---

### Post by Lord_Davos on 2008-05-04
Reinstalled gnome etc (actually did some other stuff too while I was at it) absolutely nothing helped though.

Oddly, if I boot into failsafe gnome it displays the "failsafe gnome is when no scripts are run blah blah blah" and I can click OK, and then it just does absolutely nothing again - it's as if it's just hitting a wall and giving up.


Another problem just arised - I can't get my wireless connection working, as it's not picking up my access point. As far as I'm aware, the b43 driver is installed fine.

---

### Post by llamakc on 2008-05-04
You need to rename some directories in your /home/USER directory.

One way that you can be certain that GNOME is fine (but your user's files are messed up) is to add another user to your system while in KDE. Logout and log back in as this NEW user. If GNOME works fine, do this for your original problematic user account.

[hint: this is going to rename the directories that hold your GNOME settings, so the appearance and setup will fall back to the default]

Open a Terminal while in KDE. Rename the following directories in ~ (that means /home/USER)

```

mv .gconf .gconf-backup

mv .gconfd .gconfd-backup

mv .gnome .gnome-backup

mv .gnome2 .gnome2-backup

mv .gnome2_private .gnome2_private-backup

```Now log out and log back in using GNOME. 

Voila!

If you have questions about the above please ask before proceeding.

---

### Post by Lord_Davos on 2008-05-04
Afraid that didn't help, plus I've developed a new problem, number 3 below. My problems now are:

1) Gnome isn't working
2) wifimanager in KDE isn't finding my access point, which means I have to either boot into windows or crawl under a desk to plug into the network when I want to do something
3) when I click "unlock" or "use as administrator" in anything in KDE, suddenly it's telling me my password is wrong. Oddly, it's starting to take 2, sometimes 3, attempts in Konsole before sudo accepts my password. I accept that sometimes I type my password in wrong, but that's about 1/100 times that I do that, not 30% of the time!

---

### Post by Lord_Davos on 2008-05-04
New update, I've got it down to just two problems, one of which is extremely small

1) Gnome isn't working
2) I need to run something when the computer launches - I'm in windows right now but it's wpa_somethingorother blah blah blah - needs to run to authenticate the wireless connection but I don't know how to run this at launch

Of course, getting Gnome to work is my priority

---


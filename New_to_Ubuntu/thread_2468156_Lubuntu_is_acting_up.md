---
title: "Lubuntu is acting up"
date: 2021-10-19
forum: New to Ubuntu
---

### Post by spadesama on 2021-10-19
so i downloaded Lubuntu 2 months ago using the help of a youtube video, some issues happened like the grubhub got installed on the flash drive(solved) and certain games wouldn't run(have to run a command before opening them)

But i couldn't solve some other problems like:
 
some sever screen tearing that's highly noticeable

and i tried installing a new theme but it wasn't apllied correctly
  only the colors of the themes would get applied if that makes any sence? the interface didn't change at all basically nothing changed, i tried the recommended theme format and that didn't workd i tried the Kvantum ones and they still didn't work,
what's weird though is that when i looked at a tutorial it said to go to prefrences then go to customize look and feel, i couldn't find "customize look and feel" though the closest thing to it was "appearance".

i originally downloaded Lubuntu because i have an extremely old pc that was struggling with windows10 but somehow it got slower when i installed Lubuntu.

so i don't get it, is Lubuntu not compatibale with my cpu(core 2 duo) or something?

---

### Post by QIII on 2021-10-19
Some things that would help you get assistance:

1.  Tell us which *release* of Lubuntu you are using.

2.  Give us a more complete picture of your hardware.

3.  Ask for assistance with *one* problem per thread.  You have listed several and this thread will become exceptionally confusing if people try to start answering so many questions.

In your response, please address points 1 and 2 and then let us know which *one* item you would like help with in this thread.

---

### Post by spadesama on 2021-10-19
1. 21.04
2. CPU: Intel(R) Core(TM)2 Duo CPU     E7200  @ 2.53GHz
    3.5 Gigs of RAM
    320 Gigs hdd
3. i need help with the screen tearing please

---

### Post by guiverc on 2021-10-19
I have a couple of boxes (using nvidia) that don't like the default `flurry` screensaver issue.

I've reported the issue [here]("http://launchpad.net/bugs/1855220") , as I'd like Lubuntu to default to another, but its really easily changed so something that's more appealing to you & doesn't have the issue. See [https://manual.lubuntu.me/stable/3/3.2/3.2.19/screensaver.html](https://manual.lubuntu.me/stable/3/3.2/3.2.19/screensaver.html)

Note:  I've provided the *impish* or 21.10 manual link, 21.04 is no longer the *stable* release so it's online manual has gone already; 21.04 being in the last final months of its supported life.

**Themes**

That is a difficult area, and you've provided few specifics.  There are GTK2 themes, GTK3 themes, Qt5 themes and if you start wanting dark themes there are specific choices you need to pick.  I'll add some links
- [https://manual.lubuntu.me/stable/3/3.2/3.2.2/appearance.html](https://manual.lubuntu.me/stable/3/3.2/3.2.2/appearance.html)

and a number of users have posted their experiences on the Lubuntu discourse, eg. 
- [https://discourse.lubuntu.me/t/20-04-contribution-manual-to-customize-lxqt-and-different-color-schemes-for-breeze/992](https://discourse.lubuntu.me/t/20-04-contribution-manual-to-customize-lxqt-and-different-color-schemes-for-breeze/992)

where some of these contain clues too. They may not be your exact version, but if *modern* Lubuntu with LXQt few changes need to be made (you'll have more options given you're on a later release is all).

**Core 2 Duo**

The c2d doesn't impact anything; in fact I do much of my QA (*Quality Assurance*) on c2d-e6320, c2d-8400, c2d-6850, c2d-8300, c2q-.... & like boxes.  The cpu doesn't have any impact on themes, what appears on screen though.. eg. the screensaver (*flurry choppy/tearing*) issue occurs on

- hp dc7700 (c2d-e6320, 5gb, nvidia quadro nvs 290)
- hp 8200 elite sff (i5-2400, 8gb, nvidia quadro 600)

where the CPUs are rather different; it's the GPU that links them there; both use nvidia quadro type.  Other c2d, c2q etc boxes aren't impacted as they have different GPUs (*be they on a card on on the motherboard*).

I tend to use `lshw` to list hardware (ie. get hardware details). If I only want to list the video details I'll likely use `sudo lshw -C video`  (*list hardware but limit results to class video, the `sudo` elevates my privileges for accurate results*)

---

### Post by ActionParsnip on 2021-10-20
What is the output of
```

sudo lshw -C display

```
Thanks

---

### Post by grahammechanical on 2021-10-20
If you follow a tutorial it helps us if you provide a link to the tutorial. It helps if we know the instructions that you are following. It may even be that the tutorial does not apply to the version of Lubuntu that you are using.

I do not use Lubuntu but I am sure that it has a Help application. These help programs point the way to switching themes but are not meant to give instruction on applying a theme downloaded from the internet. If that is what you are trying to do.

Regards

---


---
title: "New gnome-session 3 soon in repos"
date: 2011-05-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-05-24
The package set gnome-session (3.0.2-0ubuntu1) will soon hit the Oneiric repos (the first build trial failed).
Here:
[https://launchpad.net/ubuntu/oneiric/+source/gnome-session/3.0.2-0ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/gnome-session/3.0.2-0ubuntu1)

The default sessions are Unity, Unity2D or gnome-shell.
In case you want to use gnome-panel, you need to install also the package gnome-session-fallback.
Then you can choose the Ubuntu Classic (Gnome-panel GTK+2).
That is, however, not the default option, because Canonical do not want it to be.

But where is Gnome-panel GTK+3?
There is no such package in Gnome3 PPA either.
However, the source does exist (Gnome.org).

---

### Post by JMB74 on 2011-05-24
> **Harry33 said:**
> But where is Gnome-panel GTK+3?
There is no such package in Gnome3 PPA either.
However, the source does exist (Gnome.org).

Someone appears to have done some builds here?

[https://launchpad.net/~jbicha/+archive/ppa?field.series_filter=oneiric](https://launchpad.net/~jbicha/+archive/ppa?field.series_filter=oneiric)

No idea if that is usable in any way though.

---

### Post by ronacc on 2011-05-24
> **Harry33 said:**
> 
That is, however, not the default option, because Canonical do not want it to be.

(Gnome.org).

ask me how much I care what canonical wants ! the ONLY thing that matters on MY system is what I want .

---

### Post by MacUntu on 2011-05-24
> **ronacc said:**
> ask me how much I care what canonical wants !

A lot, given the numerous times you complained about what Canonical wants. ):P

---

### Post by dino99 on 2011-05-24
gnome-session-fallback gone ?

---

### Post by Skelator on 2011-05-24
Sounds like a key set of packages... Do you know roughly when these will be rolled out? I'm looking forward to this historic moment when Gnome2 is no longer in my vm :-)

---

### Post by Harry33 on 2011-05-24
> **dino99 said:**
> gnome-session-fallback gone ?

No no, it is not gone. It will be in the repos.
It is just that the fallback means gnome-panel GTK+2 session (the Ubuntu Classic).

I would have just wanted a package gnome-panel_3.0 into the Oneiric repos.

---

### Post by Harry33 on 2011-05-24
> **Skelator said:**
> Sounds like a key set of packages... Do you know roughly when these will be rolled out? I'm looking forward to this historic moment when Gnome2 is no longer in my vm :-)

The gnome-session package set is already in the official repos.
Here: 
[https://launchpad.net/ubuntu/oneiric/+source/gnome-session/3.0.2-0ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/gnome-session/3.0.2-0ubuntu1)

1) if you use Unity, Unity 2D or gnome-shell only, install/upgrade these packages:
 - gnome-session, gnome-session-common, gnome-session-bin

2) if you need in addition to that Ubuntu Classic session,
also install the package gnome-session-fallback.

3) if, however you only use Ubuntu Classic, and you do not have installed Unity, Unity2D nor Gnome-shell at all, then you need to install these packages:
gnome-session-fallback, gnome-session-common and gnome-session-bin.
But note, that gnome-session is not installable then.

---

### Post by satanselbow on 2011-05-24
Be very careful Gnome3 fans - I just did a dist-upgrade and it broke Gnome3 big style (previously using mini install w gnome3-team repo + "official" updates to date). No Unity involvement at all.

Purging Gnome3-team now - so will see where it gets me too... Fedora 15 tomorrow looks all the more sweeter all of a sudden :(

---

### Post by cbowman57 on 2011-05-24
> **satanselbow said:**
> Be very careful Gnome3 fans - I just did a dist-upgrade and it broke Gnome3 bit style (previously using mini install w gnome3-team repo + "official" updates to date). No Unity involvement at all.

Purging Gnome3-team now - so will see where it gets me too... Fedora 15 tomorrow looks all the more sweeter all of a sudden :(

Say it ain't so. :)

I've still got a bunch of PPA's active, ubuntugnometeam, gnometeam-g3 & ricotz/testing & staging so upgrades are a little tricky.  I'll just hold off until I hear a favorable report.

Thanks guys.

---

### Post by Quackers on 2011-05-24
Me too. No gnome-shell any more. No desktop backgrounds available. A few icons missing from panel and Applications screen :-(

---

### Post by bulldog on 2011-05-24
Same here,did a fresh install with cbowman57's version,and up and running again.

No updates for me for a while though.:(

It brakes Gnome-Shell and you can't login anymore to the shell.

Maybe it was possible to repair,but a fresh install is faster :)

---

### Post by bmbaker on 2011-05-24
everything wks fine :-) you can even log into unity now!!!!

---

### Post by Skelator on 2011-05-24
The new gnome-session is in the repos... So it wont automatically replace the classic gnome session with the new gnome session without manual intervention? I thought Ocelot was going to force the new gnome/unity/unity2d on people?

---

### Post by Starks on 2011-05-24
Everything's broken now except for the ever-bulletproof failsafeX.

gnome-panel is still present for some reason but we are at a crossroads that I wasn't expecting to happen so early.

Right now, we as Ubuntu users need to decide whether Ubuntu is still for us. Choice is being restricted and Unity development is not keeping up with that loss of choice.

---

### Post by Skelator on 2011-05-24
> Right now, we as Ubuntu users need to decide whether Ubuntu is still for  us. Most people on this thread have known about the changes for  Choice is being restricted and Unity development is not keeping up  with that loss of choice.     Give it a rest... We're all aware of the situation.  Most people on this thread have known about the changes for 6 months now and have already stuck it out.  The reason most of us are here is to help make things better. If anything Ocelot will bring even more choice because it will have Gnome3, Gnome-shell, KDE,XFCE, Unity 3d, Unity 2d, Gnome2 fallback and a bunch of other DE's in the repositores.

---

### Post by Starks on 2011-05-24
I'm well aware of the situation too, but when you're ballsy like me and accept the risk of running Oneiric on a primary computer, you expect things to be no more broken than previous dev cycles.

---

### Post by Skelator on 2011-05-24
Dapper Drake and Edgy Eft development phases were similar experiences. Dapper was so buggy the launch had to be delayed by a few weeks.  Sometimes things work for some people and not others. If you've never had any problems during a development phase before then you are very, very lucky. Even if you look back at the history of releases you'll find that alot of people have had major problems just upgrading to the 'final' version. If you enter a develeopment phase you should expect breakage.

---

### Post by ranch hand on 2011-05-24
> **Skelator said:**
> Give it a rest... We're all aware of the situation.  Most people on this thread have known about the changes for 6 months now and have already stuck it out.  The reason most of us are here is to help make things better. If anything Ocelot will bring even more choice because it will have Gnome3, Gnome-shell, KDE,XFCE, Unity 3d, Unity 2d, Gnome2 fallback and a bunch of other DE's in the repositores.
I have to say that when someone like starks is saying something like this a little respect is called for.

Starks has been a bastion of Ubuntu support for many testing cycles (certainly has jumped my butt a time or 2).

I realize that the trend is be a fanboy or get out but let's try not to be so blatant about it.

---

### Post by Skelator on 2011-05-24
Try and keep on topic folks. This thread is not about starks or whether or not people need to reconsider Ubuntu, it's about  gnome3 testing. Please read the OP and let's try and stay on topic. Thanks.

---

### Post by scradock on 2011-05-24
So the latest gnome-session-* updates leave me with no Unity launcher, no top panel, no desktop background, no icons, no alt-F2 launcher, no ctl-alt-T terminal....

Only one start-up program starts up and shows its window on a black screen, minus window decorations.

Ctl-alt-F1 switches to a tty, in which I can login and do stuff; but what do I need to do to recover at this stage?

Any ideas?

---

### Post by Quackers on 2011-05-24
Have you run the latest updates? (A pixbuf update and 2 x librsvg).

---

### Post by Squonk07 on 2011-05-24
Today's minor breakage sorted itself out about an hour ago for me. Until then, I discovered that installing gnome-session-fallback let me log in and reach the desktop, as long as I selected the Gnome Classic desktop at login.

---

### Post by scradock on 2011-05-25
Thanks, guys. I had auto logon enabled, which meant I didn't get the session choice, just the blank screen, until I hit ctl-alt-del (which now gives me log-out rather than shutdown). Then I could choose Recovery Console, install gnome-session-fallback, and log back in with Gnome Classic.

Then the latest updates gave me the desktop background and window decorations again. One more logout and I was able to select Ubuntu (Unity) on logging in, and everything is back to normal.......

---

### Post by kansasnoob on 2011-05-25
This seems pretty good. I can get unity (ubuntu), classic and classic w/o effects.

Running "top" and fiddling a bit tells me they're each running as expected, both unity and classic on compiz, but classic w/o effects on metacity.

No way that I've found to run gnome-shell, so I'd bet once unity-2d gets added to the defaults, and the classic modes go away, things will be remarkably different.

---

### Post by kansasnoob on 2011-05-25
That last post is what's shown with 'gnome-session-fallback' installed. I just tried removing it and then I have only Ubuntu, recovery console and user defined session.

No sign of being able to use unity-2d yet and I wonder if it will be possible to switch to the standard gnome3 DE w/o a ppa :confused:

In Natty with the UGR/gnome3 ppa's installed, I prefer the actual "forced-fallback" which doesn't yet work with the GUI switch. But it allows the use of the gnome-tweak-tool which helps a bit.

---

### Post by scradock on 2011-05-25
> **kansasnoob said:**
> That last post is what's shown with 'gnome-session-fallback' installed. I just tried removing it and then I have only Ubuntu, recovery console and user defined session.

No sign of being able to use unity-2d yet and I wonder if it will be possible to switch to the standard gnome3 DE w/o a ppa :confused:

In Natty with the UGR/gnome3 ppa's installed, I prefer the actual "forced-fallback" which doesn't yet work with the GUI switch. But it allows the use of the gnome-tweak-tool which helps a bit.
Try installing unity-2d. It's there in the repos, and installs without a hitch here. Now I have not one but TWO new options at log-in - Unity-2d and Ubuntu-2d.

Typing this from ubuntu-2d at the moment - it seems to be using Unity-2d, but the launcher has only the apps and folders buttons initially. Launching an app adds its button to the launcher, and I can set it to stay. Don't know if it comes back after log-out/log-in yet.

EDIT: Yes, apps added to the launcher bar persist between sessions, so I can add my favorite set instead of using soemone else's idea.

BUT the Unity-2d session fails to start from log-in with a message "2d-ubuntu fails to start". As I say above, Ubuntu-2d works fine.

---

### Post by Harry33 on 2011-05-26
Here is changelog form the newest gnome-session.
Will we get the gnome-panel GTK+3 into repos soon?

gnome-session (3.0.2-0ubuntu3) oneiric; urgency=low

>   * debian/control:
    - gnome-session temporary recommends gnome-session-fallback until we can
      get a new gnome-panel recommending gnome-session-fallback for update
      migration

---

### Post by kansasnoob on 2011-05-26
> **scradock said:**
> Try installing unity-2d. It's there in the repos, and installs without a hitch here. Now I have not one but TWO new options at log-in - Unity-2d and Ubuntu-2d.

Typing this from ubuntu-2d at the moment - it seems to be using Unity-2d, but the launcher has only the apps and folders buttons initially. Launching an app adds its button to the launcher, and I can set it to stay. Don't know if it comes back after log-out/log-in yet.

EDIT: Yes, apps added to the launcher bar persist between sessions, so I can add my favorite set instead of using soemone else's idea.

BUT the Unity-2d session fails to start from log-in with a message "2d-ubuntu fails to start". As I say above, Ubuntu-2d works fine.

I've been holding back a bit on installing packages ATM just to get a feel of what the new defaults will be. After Alpha1 I'll start playing more :)

Ultimately I think I'll be wanting to find the easiest way to get the default gnome-shell DE and customize from there, but things could change, maybe they'll add the ability to tweak unity so it'll be more user friendly.

---

### Post by kansasnoob on 2011-05-27
Now I have unity-2d (called Ubuntu 2d in the menu), and it actually looks pretty good.

If I could remove the top panel altogether and replace it with a dock (docky or awn) at the bottom I think I could actually work with that ............ no need to be impatient though :D

As someone who really hasn't liked Unity very much I must say I'm a bit more impressed all the time.

One thing I've noticed with all gnome3 variants is that gthumb is no longer supported though, I sort of miss that :(

---

### Post by bmbaker on 2011-05-28
[https://launchpad.net/~webupd8team/+archive/gthumb](https://launchpad.net/~webupd8team/+archive/gthumb)

---

### Post by kansasnoob on 2011-05-28
> **bmbaker said:**
> [https://launchpad.net/~webupd8team/+archive/gthumb](https://launchpad.net/~webupd8team/+archive/gthumb)

Far out, thank you very much :D

---

### Post by ranch hand on 2011-05-28
Gthumb conflicts with a "sugests" of Shotwell which is a dependency of the gnome meta package.  I installed ghumb on one of my Debian installs with aptitude.

This thread was started by another feller and I started reading it to see if I could find a way to get gthumb installed.  Sure did.
post 12 tells how that worked.

[http://www.linuxquestions.org/questions/debian-26/why-on-earth-i-cant-install-gthumb-880355/](http://www.linuxquestions.org/questions/debian-26/why-on-earth-i-cant-install-gthumb-880355/)

Post 7 gives the link that had the clues needed.  I think there may be another solution under Ubuntu in that same link.

---


---
title: "Is gnome-shell working yet?"
date: 2011-07-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ojdon on 2011-07-13
Hi there, I've just tried Alpha 2 and the most recent Daily Build since I'm wanting to use Gnome-Shell in Ubuntu 11.10. But when I install Gnome-Shell and log into the "Gnome" session and wait a couple of seconds it will repeatedly crash.

Is there any work arounds I'd need to do first before using Gnome-Shell in Oneiric?

---

### Post by MonolithImmortal on 2011-07-13
EDIT: Removed, wrong advice.

---

### Post by sgage on 2011-07-14
Can't install the gnome-shell from the repos - still missing a dependency. I installed it from ricotz, and it's completely unusable. 

It is missing all the apps, crashes and sometimes restarts itself. You can't even launch an app via Alt-F2 - it simply can't find the program even when you type in the command.

Oh well.

[edit: does anyone know when a new GS will be built against the new libedataserverui?]

---

### Post by Bowmore on 2011-07-14
It's on its way now and seems to work.

[ubuntu/oneiric] gnome-shell 3.0.2-1ubuntu1 (Accepted)
[https://lists.ubuntu.com/archives/oneiric-changes/2011-July/004933.html](https://lists.ubuntu.com/archives/oneiric-changes/2011-July/004933.html)

The build (i386 or amd64) can be downloaded from here for those who can't wait ;)
[https://launchpad.net/ubuntu/oneiric/+source/gnome-shell/3.0.2-1ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/gnome-shell/3.0.2-1ubuntu1)

---

### Post by sgage on 2011-07-14
> **Bowmore said:**
> It's on its way now and seems to work.

[ubuntu/oneiric] gnome-shell 3.0.2-1ubuntu1 (Accepted)
[https://lists.ubuntu.com/archives/oneiric-changes/2011-July/004933.html](https://lists.ubuntu.com/archives/oneiric-changes/2011-July/004933.html)

The build (i386 or amd64) can be downloaded from here for those who can't wait ;)
[https://launchpad.net/ubuntu/oneiric/+source/gnome-shell/3.0.2-1ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/gnome-shell/3.0.2-1ubuntu1)

It's in the repos now, and installs without issue, but behaves just like the ricotz version. No icons, very crashy, etc.

---

### Post by Quackers on 2011-07-14
I'm getting no crashes here. I've been using it for some months and it has had some problems and some things are hidden now but it doesn't crash and Alt+F2 works ok here.

---

### Post by sgage on 2011-07-14
> **Quackers said:**
> I'm getting no crashes here. I've been using it for some months and it has had some problems and some things are hidden now but it doesn't crash and Alt+F2 works ok here.

It's an unusable mess here. Nothing in Applications. The top panel just disappears, and sometimes reloads. I was finally able to load Firefox via Alt-F2, but the panel went away, and the hot-corner stopped working.

I had just begun this reply, but when I typed in the box, nothing. Then it just crashed.

This is gnome-shell from the Oneiric repos, all up to date, 32-bit. The gnome-shell from ricotz behaves the same way.

Does anyone have a clue as to what might be going on?

---

### Post by MonolithImmortal on 2011-07-14
> **sgage said:**
> It's an unusable mess here. Nothing in Applications. The top panel just disappears, and sometimes reloads. I was finally able to load Firefox via Alt-F2, but the panel went away, and the hot-corner stopped working.

I had just begun this reply, but when I typed in the box, nothing. Then it just crashed.

This is gnome-shell from the Oneiric repos, all up to date, 32-bit. The gnome-shell from ricotz behaves the same way.

Does anyone have a clue as to what might be going on?
I had a similar problem when I first installed Gnome Shell. I fixed it a while back and I'm pretty sure it was from the advice I posted up there in my first post. Try that and tell me if it works.

---

### Post by ranch hand on 2011-07-14
> **Quackers said:**
> I'm getting no crashes here. I've been using it for some months and it has had some problems and some things are hidden now but it doesn't crash and Alt+F2 works ok here.
Are you using GS under GTK3 and Gnome3 with the 3.0.0 kernel?

---

### Post by Quackers on 2011-07-14
> **ranch hand said:**
> Are you using GS under GTK3 and Gnome3 with the 3.0.0 kernel?

I'm using GS with the 3.0.0-5 kernel and I have lots of GTK3 packages installed, if that helps :-)

---

### Post by mc4man on 2011-07-14
> **sgage said:**
> It's an unusable mess here. Nothing in Applications. The top panel just disappears, and sometimes reloads. I was finally able to load Firefox via Alt-F2, but the panel went away, and the hot-corner stopped working.

I had just begun this reply, but when I typed in the box, nothing. Then it just crashed.

This is gnome-shell from the Oneiric repos, all up to date, 32-bit. The gnome-shell from ricotz behaves the same way.

Does anyone have a clue as to what might be going on?

Have you created a /etc/xdg/menus/applications.menu or linked gnome-applications.menu like - 

 ```
sudo ln -s /etc/xdg/menus/gnome-applications.menu /etc/xdg/menus/applications.menu

```
(gs doesn't work right till you do so

Otherwise maybe try a fresh A2 install - there are considerable differences between an older > updated and a new (A2) > updated, some things are never made right thru updates

Ex. - on a slightly older install many apps don't show in gs's app's lenses without editing .desktops
On a new install the other day everything shows up (even some things that shouldn't like a few readme's and FAQ's.

There are several other diff's, and no apparent way to correct in the older install

---

### Post by cariboo on 2011-07-14
+1 to what mc4man says, I'm at the point right now where I need to do a re-install, as both GDM and Lightdm crash, and the only way to get to a working desktop for me is to start in recovery mode and use startx.

---

### Post by MonolithImmortal on 2011-07-14
> **mc4man said:**
> 
 ```
sudo ln -s /etc/xdg/menus/gnome-applications.menu /etc/xdg/menus/applications.menu

```(gs doesn't work right till you do so

Sorry, thats what I was trying to remember. That's how I fixed my issues.

---

### Post by sgage on 2011-07-14
> **mc4man said:**
> Have you created a /etc/xdg/menus/applications.menu or linked gnome-applications.menu like - 

 ```
sudo ln -s /etc/xdg/menus/gnome-applications.menu /etc/xdg/menus/applications.menu

```
(gs doesn't work right till you do so

Otherwise maybe try a fresh A2 install - there are considerable differences between an older > updated and a new (A2) > updated, some things are never made right thru updates

Ex. - on a slightly older install many apps don't show in gs's app's lenses without editing .desktops
On a new install the other day everything shows up (even some things that shouldn't like a few readme's and FAQ's.

There are several other diff's, and no apparent way to correct in the older install

Of course! Why didn't I think of that! The ol' sudo ln -s /etc/xdg/menus/gnome-applications.menu /etc/xdg/menus/applications.menu gambit! What could be more obvious?

GS works now :KS

---

### Post by Quackers on 2011-07-14
Aha! A happy ending! That's good :-)

---

### Post by sgage on 2011-07-14
> **Quackers said:**
> Aha! A happy ending! That's good :-)

Yes indeed.

I knew there was some incantation involved, and though I searched the forum fairly thoroughly, that particular spell eluded me.

I wonder if their should maybe be a Gnome Shell sticky thread up top?

---

### Post by Quackers on 2011-07-14
This thread is a source of much info for me, but it's a bit long :-)

[http://ubuntuforums.org/showthread.php?t=1722627&highlight=gnome-shell](http://ubuntuforums.org/showthread.php?t=1722627&highlight=gnome-shell)

---

### Post by cariboo on 2011-07-14
I use zim, it's in the repositories, to keep track of hints and tips like that.

---

### Post by ranch hand on 2011-07-14
> **Quackers said:**
> I'm using GS with the 3.0.0-5 kernel and I have lots of GTK3 packages installed, if that helps :-)
Thank you.   I was just curious.  Had tried GS in both 10.10 and 11.04 and am sure that there are still many doing so.

I never had much luck with it there.   It worked but was pretty crippled.

I am still on 3.0.0 from Debian experimental.  That is far as they have gotten, I think, could be I am not doing something quite right.  Actually I am sure I am not doing things just right.  It seems to be working right now so I will continue to do it the way I have been until it breaks.

---

### Post by rburkartjo on 2011-07-14
naultilus is still crashing frequently on my end. okay i cheated and am using dolphin and i can still access all my fiies. however using alt-f2 to run a command causes nautilus to instantly crash

---

### Post by Quackers on 2011-07-14
> **ranch hand said:**
> Thank you.   I was just curious.  Had tried GS in both 10.10 and 11.04 and am sure that there are still many doing so.

I never had much luck with it there.   It worked but was pretty crippled.

I am still on 3.0.0 from Debian experimental.  That is far as they have gotten, I think, could be I am not doing something quite right.  Actually I am sure I am not doing things just right.  It seems to be working right now so I will continue to do it the way I have been until it breaks.

And it will :-) - probably.
No problem. I re-install and play about so often that I'm never sure what state anything's in :confused:
Did you see mc4man's post a little earlier with the xdg command? I tried that but it says the link was already in existence so it obviously wasn't needed here, but others have needed that to get things working.
I have no idea why that would be - which isn't an unusual thing for me.

---

### Post by rbrick49 on 2011-07-14
> **Quackers said:**
> And it will :-) - probably.
No problem. I re-install and play about so often that I'm never sure what state anything's in :confused:
Did you see mc4man's post a little earlier with the xdg command? I tried that but it says the link was already in existence so it obviously wasn't needed here, but others have needed that to get things working.
I have no idea why that would be - which isn't an unusual thing for me.
I did MC4Man,s fix toQuackers and I didnt need it either

---


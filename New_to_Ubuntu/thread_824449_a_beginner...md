---
title: "a beginner.."
date: 2008-06-10
forum: New to Ubuntu
---

### Post by deathbunny on 2008-06-10
Hello,

     I've got the following problem, first I can't find a proper guide to install Moblock, anyone have one?  And second, how do I have programs running on login? AWN in particular does not start, even when setup to.  Thanks for any assistance on a first time Ubuntu user, first week to be exact.


DB

Setup: Ubuntu Hardy Heron/Vista on a Gateway P-6831

---

### Post by billgoldberg on 2008-06-10
> **deathbunny said:**
> Hello,

     I've got the following problem, first I can't find a proper guide to install Moblock, anyone have one?  And second, how do I have programs running on login? AWN in particular does not start, even when setup to.  Thanks for any assistance on a first time Ubuntu user, first week to be exact.


DB

Setup: Ubuntu Hardy Heron/Vista on a Gateway P-6831

Don't know about MoBlock, have no need for it.

To answer you second question, add the name of the program to "system -> preferences -> sessions"

You'll have to enter 3 lines, the first and last don't really matter. In the second, you'll have to name the programs name.

For awn that's "avant-window-navigator". [I](you can look these up in synaptic)
[/I]
But I find awn pretty useless compared to [cairo dock]("http://linuxowns.wordpress.com/2008/05/08/the-best-and-worst-docks-for-ubuntu/") (not in repo).

---

### Post by hyper_ch on 2008-06-10
it is advice to use a descriptive thread title that reflects the problem inside than a generic one like "noob here" or "help needed".

You want help from people? Then you should also help them to help you.

---

### Post by billgoldberg on 2008-06-10
*double post*

---

### Post by bumanie on 2008-06-10
Many have trouble with moblock, although some get it to work. There is another program, similar to peerguardian called ip block. Check it out [here]("http://www.ubuntugeek.com/ipblock-graphical-ip-blocker.html")

---

### Post by nothingspecial on 2008-06-10
To get awn to start at login -

system > preferences > sessions
 This will give a list of your start up programs. Call it awn. The command is
```
avant-window-navigator
```
You can put anything you like in the comments - "dock" or something like that.
 Same process for anything else you want at start up.

---

### Post by forger on 2008-06-10
for avant-window-navigator, try to enable compiz, system > preferences > appearance > visual effects > choose normal.

if awn still doesn't work, try run it from the gnome terminal, system > accessories > terminal, type **[COLOR="Red"]avant-window-navigator[/COLOR]** and post the output

to run programs on login, you go to system > preferences > sessions, you have to create a new item in that list

---

### Post by deathbunny on 2008-06-10
Many thanks for the reply and advice.  I'll give the suggestions a go.

---

### Post by jre on 2008-06-11
MoBlock wiki: [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)

If you have problems just start a new thread with a descriptive topic.

Have fun
jre

---


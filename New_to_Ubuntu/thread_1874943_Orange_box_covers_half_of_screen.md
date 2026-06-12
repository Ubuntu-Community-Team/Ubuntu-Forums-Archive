---
title: "Orange box covers half of screen"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by rlogan on 2011-11-04
This is a rather annoying issue which is also intermittent and it seems to occur mostly when I move the mouse pointer over to uncover the Unity dock. 

The problem is that there is an orange transparent box covering the left hand side of the screen and it covers half the screen. It will start with no apparent frequency and can stop as easily. One way that rids the screen of the box is to use the Unity desktop switcher app to switch to Desktop 4/4 and then switch back to Desktop 1 or 3 but this does not always work either.

I am hoping someone else has come across this issue and solved it already.

Thanks

---

### Post by illgetit on 2011-11-04
When did the issue first begin to occur? 
Does it follow or react to mouse movement?

---

### Post by rlogan on 2011-11-04
It doesn't appear to be related to the mouse,more that when the Unity dock appears it also appears and stays well after the dock auto-hides.

---

### Post by rlogan on 2011-11-04
I have only noticed since the upgrade to Ocelot, but in all fairness I did not use Unity on Natty.

---

### Post by Garland Fox on 2011-11-04
I also have this orange box after I upgraded from 10.04 in 3 steps to 11.10. Similar to yours except sometimes it does seem like the mouse "sizes" the box. Acer laptop vista/11.10 intel core duo (old)

It does not appear on my dell which is a clean install of 11.10
No idea here nor solution

---

### Post by rlogan on 2011-11-04
AT least I am not alone.

This is occurring on a clean install of Ocelot for me, but not on 3 other machines upgraded from Natty to Ocelot.

---

### Post by Lars Noodén on 2011-11-04
I get this too, but am not able to figure out exactly what causes it beyond that it is related to mouse activity.

---

### Post by 3rdalbum on 2011-11-04
It's the Grid plugin of Compiz; the feature that lets you move two windows to get a side-by-side comparison view.

Turning off the plugin in ccsm and then turning it back on should fix this issue if it occurs, but I've only seen it once.

---

### Post by rlogan on 2011-11-04
Thanks for the tip

I have turned the plug-in on and off, so lets see if I get the issue again.

Hopefully that has banished the bug for good

---

### Post by rlogan on 2011-11-04
The grid plug-in doesn't seem to be the issue, so will have to keep on looking

---

### Post by mc4man on 2011-11-04
You can also try disabling the Unity Mt Grab Handles plugin
(unless you're using - don't see much reason for that plugin in most installs

---

### Post by ixtok on 2011-11-05
It just started happening to me. I did a new install only an hour ago. The orange box started after I dragged an open firefox window into a new desktop. Would another fresh install be in order?

---

### Post by 3rdalbum on 2011-11-05
> **rlogan said:**
> Thanks for the tip

I have turned the plug-in on and off, so lets see if I get the issue again.

Hopefully that has banished the bug for good

Sorry, I wasn't clear enough in my post.

Turning off Grid and turning it on again is not a permanent fix, it merely removes an existing orange box that's on the screen.

It's a bug somewhere in the chain; either in Grid or Compiz or in Unity itself.

If you are seeing it regularly, please send in a bug report onto the Launchpad service. I've only seen it once uncommanded and I can't reproduce the problem, which is why I haven't reported it myself.

---

### Post by jm-leddy on 2011-11-09
> **3rdalbum said:**
> Sorry, I wasn't clear enough in my post.

Turning off Grid and turning it on again is not a permanent fix, it merely removes an existing orange box that's on the screen.

It's a bug somewhere in the chain; either in Grid or Compiz or in Unity itself.

If you are seeing it regularly, please send in a bug report onto the Launchpad service. I've only seen it once uncommanded and I can't reproduce the problem, which is why I haven't reported it myself.

 I keep seeing the problem but it is not reproducible as far as I can tell. I'm trying with the mt plugin off at the moment, we'll see if that alters anything, though I don't think it's the cause.  If I get it to happen again I'll screencast and open a bug.

---

### Post by jm-leddy on 2011-11-09
> **jm-leddy said:**
> I keep seeing the problem but it is not reproducible as far as I can tell. I'm trying with the mt plugin off at the moment, we'll see if that alters anything, though I don't think it's the cause.  If I get it to happen again I'll screencast and open a bug.

 I've found a reliable way to reproduce. It looks like the same bug as :  [https://bugs.launchpad.net/compiz-plugins-main/+bug/875557](https://bugs.launchpad.net/compiz-plugins-main/+bug/875557)

---

### Post by jedson3 on 2011-11-22
Did anything ever get figured out about that orange box? I get it a lot. It is rather distracting. 

jedson

---

### Post by mikegior on 2011-11-22
I saw a thread  where someone wanted to rid of the Aero Snap feature since it was bothersome to them. I myself experienced this issue and after realizing I couldn't find a reason why I'd use the Aero Snap feature ever, I installed the Compiz manager (as the thread instructs) and disabled the grid altogether. Not a permanent solution (given this will completely disable the snap feature) but if you don't mind not having the Aero Snap feature, this is a good work around until the Compiz bug is fixed.

THREAD: [Disable Aero Snap feature]("http://ubuntuforums.org/showthread.php?t=1824673&highlight=aero+snap")

---

### Post by r_mano on 2011-11-23
It's tracked: [https://bugs.launchpad.net/unity/+bug/875557](https://bugs.launchpad.net/unity/+bug/875557)

For what I can understand, there is a fix which is going through the steps to arrive in "updates".

---

### Post by bobman321123 on 2011-11-24
Ack, I have the same problem. It pops up every time I trigger that combination of actions. 
I've found that clicking the desktop switcher and waiting for a second will make it go away. If you've got compiz installed, putting the "desktop switcher" hot corner in the bottom left (haven't tried it anywhere else) and using it to go to the desktop switcher fixes the issue immediately. 

Are there any fixes for this? (permanent ones)

---

### Post by grahammechanical on 2011-11-24
I get it as well and I make it go away by grabbing an application window and dragging the window. The orange apparition then fads away.

---

### Post by oxman on 2012-01-07
Thanks for the heads up regarding the screen grab. Helpful!

---


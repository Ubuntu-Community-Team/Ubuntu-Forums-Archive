---
title: "closing programs in KDE plasma desktop"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by gregorio on 2013-04-08
I feel like an idiot. Ok, maybe I am an idiot. I installed KDE plasma active desktop kubuntu on my ubuntu system as an alternative desktop. I cannot find how to close a program.  Example, I start up Chromium, of which I am using as I write this, and cannot see it in the task bar at the bottom.  I cannot see any "X" on the window to close, or any symbols that may indicate to minimize or maximize.  Am I missing something?  Obviously. Ok, I just accidently pushed the print screen button and the copy screen interface came up.  It is lacking the same buttons. Did something not install right?

Thanks

---

### Post by 0151n on 2013-04-08
There should be 3 buttons to close,maximise and minimise in the top left of the windows.
If you can't see any then there is obviously something wrong.
It would be a helpful if you could post a screenshot so we can see what happening

---

### Post by gregorio on 2013-04-08
I hope I uploaded these two screenshots ok.  In the one shot, it shows what happens with Chromium running and I click the icon in the bottom right (don't know what you call it in KDE, in windows it's the start button) and it comes up under the Chromium window.  I also cannot resize the windows by clicking on corners or sides.

---

### Post by tartalo on 2013-04-08
> **gregorio said:**
> I hope I uploaded these two screenshots ok.  In the one shot, it shows what happens with Chromium running and I click the icon in the bottom right (don't know what you call it in KDE, in windows it's the start button) and it comes up under the Chromium window.  I also cannot resize the windows by clicking on corners or sides.

It looks like Kwin is not running, apparently that can happen when you install KDE on Ubuntu, instead of installing directly Kubuntu. Check this thread:
[http://forum.kde.org/viewtopic.php?f=66&t=90354](http://forum.kde.org/viewtopic.php?f=66&t=90354)

By the way you didn't install Plasma Active, Plasma Active is for tablets and it looks like this: [http://plasma-active.org/](http://plasma-active.org/)

---

### Post by 0151n on 2013-04-08
[SIZE=3][SIZE=2]I installed kde on default ubuntu using a command like this :
[/SIZE][COLOR=#000103][FONT=Arial][SIZE=2]*sudo apt-get install kubuntu-desktop*
and I have had **no **problems with it.you
[/SIZE]
[SIZE=2]How did you install it?[/SIZE]


[/FONT][/COLOR][/SIZE]

---

### Post by gregorio on 2013-04-08
> **tartalo said:**
> It looks like Kwin is not running, apparently that can happen when you install KDE on Ubuntu, instead of installing directly Kubuntu. Check this thread:
[http://forum.kde.org/viewtopic.php?f=66&t=90354](http://forum.kde.org/viewtopic.php?f=66&t=90354)

By the way you didn't install Plasma Active, Plasma Active is for tablets and it looks like this: [http://plasma-active.org/](http://plasma-active.org/)

Thanks.  That made me think of just uninstalling the whole kubuntu thing, which I managed to do (I hope).  And, yes, I did not install Plasma Active.  I actually knew that.  Surprisingly.  And I look so much forward to Plasma Active and Ubuntu for tablets taking off.

---

### Post by gregorio on 2013-04-09
Pretty well the same way.
[I]
sudo add-apt-repository ppa:kubuntu-ppa/backports
sudo apt-get update
sudo apt-get install kubuntu-desktop[/I]

Not sure what went wrong.  I was just looking for an alternative desktop.  No big deal tho.  Getting use to unity.

Thanks

---


---
title: "Non-maximized windows do not have a close button."
date: 2011-11-12
forum: New to Ubuntu
---

### Post by chemphill on 2011-11-12
Hello all,
I am a new user. I have Ubuntu 11.10. I have been experiencing a problem for a while now. Windows that are not maximized do not have the little bar on top of them where you can minimize, maximize, or close the window. It is not a huge problem since I use the keyboard shortcuts, but it would be nice if they were their. On maximized windows it is there, but not minimized windows. Any Ideas Why?
Thanks to all!

P.S. I forgot to mention: I cannot drag the windows anywhere because it is missing that little bar at top. Therefore, as stated above, I cannot close, minimize or maximize the window either. I have to use keyboard short cuts.

---

### Post by donaldt on 2011-11-12
I have the same problem.  I am at 11.04 and something I did (compiz perhaps?) caused the windows to lose their max/min/close symbols and although I can grab firefox and move the window around, I cannot grab thunderbird and move or re-size it.

Everything was working fine while I was going through the system options.  I must have accidentally clicked on something that caused it, but I can't figure out what it was and am stuck.

Thanks if you can help...

donaldt

---

### Post by abnordude on 2011-11-13
in compiz ccsm, there are options under window management..i think there is an option for moving and resizing windows......check those boxes.....

also check whether the windows decoration under effects is on.

try that.

---

### Post by beew on 2011-11-13
This is by design, known as the global menu. If the windows are not maximized the buttons would be stuck on the top panel instead of on the windows.

I hate it, so the first thing I install Ubuntu is to get rid of the global menu to restore things to normal. To do this simply remove the package indicator-appmenu

```
sudo apt-get remove indicator-appmenu
```You can also remove it easily from the synaptic package manager.

Oh wait, synaptic is not installed by default in 11.10 since they want new users to use only that Canonical designed crap the Ububtu Software Center, which is bloated, slow and lack options so you may want to install Synaptic too. 
```
sudo apt-get install synaptic 
```

---

### Post by abnordude on 2011-11-13
> **beew said:**
> This is by design, known as the global menu. If the windows are not maximized the buttons would be stuck on the top panel instead of on the windows.

I hate it, so the first thing I install Ubuntu is to get rid of the global menu to restore things to normal. To do this simply remove the package indicator-appmenu

```
sudo apt-get remove indicator-appmenu
```You can also remove it easily from the synaptic package manager.

Oh wait, synaptic is not installed by default in 11.10 since they want new users to use only that Canonical designed crap the Ububtu Software Center, which is bloated, slow and lack options so you may want to install Synaptic too. 
```
sudo apt-get install synaptic 
```


I dont think that he is talking about global menus......i believe that he has lost that bar which contain maximize, minimize and close buttons....
Am I right?

---

### Post by GWBouge on 2011-11-13
I don't have an answer for the issue (if it is by design, apparently I'm experiencing a bug where my Close/Min/Max buttons are showing up in the corner of my title bar ...), but to move windows you can hold Alt+Click and drag anywhere on the window, and to resize you can Alt+Middle Click and drag.

---

### Post by KBurns5040 on 2011-11-13
Is it possible it's a theme?  Try checking your system settings>personal>appearance. 


KBurns
[http://www.burnscomputers.com]("http://www.burnscomputers.com/")

---

### Post by cotcot on 2011-11-13
You will find the maximize option in a menu that appears when you right click in the window bar with the close icon.

I am now using gnome shell. There I found a way to get these icons back. I do not remember exact how I did but it is easy to find with google.

---

### Post by rpa.adak on 2012-08-17
I have the same problem of no close,max,min button. I solve it just adding the maximuze option in compiz ccsm. Just go to dash home write compiz, select compiz ccsm. in the windows management area just make the maximuze on. thats gone.:guitar:

---


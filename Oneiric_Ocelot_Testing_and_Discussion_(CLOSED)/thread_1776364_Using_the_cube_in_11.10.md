---
title: "Using the cube in 11.10"
date: 2011-06-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by wildmanne39 on 2011-06-06
Hi, I have personalized 11.10 with my conky and I was wondering if it would be a disaster to activate the cube and effects, I have then working great in natty, any thoughts on the matter is greatly appreciated.

---

### Post by mc4man on 2011-06-06
Should be no different than you see in natty - atm basically the same unity/compiz/nux
(handful of  small bug fixes, some in natty-proposed

---

### Post by sparker256 on 2011-06-06
> **wildmanne39 said:**
> Hi, I have personalized 11.10 with my conky and I was wondering if it would be a disaster to activate the cube and effects, I have then working great in natty, any thoughts on the matter is greatly appreciated.
This is what I saw when I tried in natty and oneiric so not sure how you got it working in natty.

Bill

---

### Post by mc4man on 2011-06-06
> **sparker256 said:**
> This is what I saw when I tried in natty and oneiric so not sure how you got it working in natty.

Bill
There are several ways to do without unsetting all the plugins (or you can just set all of them back

The easiest here is to just use gconf-editor - good for disabling plugins and limited enabling, will take about 30 sec's to do
Not worth repeating - the gconf way here (you can also edit workspaces - hsize, vsize. while in gconf or do back in ccsm
[http://ubuntuforums.org/showthread.php?p=10734118#post10734118](http://ubuntuforums.org/showthread.php?p=10734118#post10734118)

---

### Post by sparker256 on 2011-06-06
> **mc4man said:**
> There are several ways to do without unsetting all the plugins (or you can just set all of them back

The easiest here is to just use gconf-editor - good for disabling plugins and limited enabling, will take about 30 sec's to do
Not worth repeating - the gconf way here (you can also edit workspaces - hsize, vsize. while in gconf or do back in ccsm
[http://ubuntuforums.org/showthread.php?p=10734118#post10734118](http://ubuntuforums.org/showthread.php?p=10734118#post10734118)
I will look at that and see what I come up with.

PS. Once I got the number of desktops set all is great again.

Thanks Bill

---

### Post by wildmanne39 on 2011-06-06
> **sparker256 said:**
> This is what I saw when I tried in natty and oneiric so not sure how you got it working in natty.

BillHi, thanks for your reply, this is how I did it in natty.
[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)
if you change more effects after you are done with this guide it will mess up your windows but just log out and back in and they are fixed.Thanks to everyone the replied I will give it a try later in 11.10.

---

### Post by sparker256 on 2011-06-06
> **wildmanne39 said:**
> Hi, thanks for your reply, this is how I did it in natty.
[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)
if you change more effects after you are done with this guide it will mess up your windows but just log out and back in and they are fixed.Thanks to everyone the replied I will give it a try later in 11.10.
I tried to put a jpg image on the top and bottom of the cube and it wanted to enable some plugin about jpg but that seems to have broken my unity 3d. The launcher does not even show and ctrl+alt+t does not start the terminal. Reinstalled but still not working so will have to see what else I can try.

:(  Bill

---

### Post by mc4man on 2011-06-06
> **sparker256 said:**
> I tried to put a jpg image on the top and bottom of the cube and it wanted to enable some plugin about jpg but that seems to have broken my unity 3d. The launcher does not even show and ctrl+alt+t does not start the terminal. Reinstalled but still not working so will have to see what else I can try.

:(  Bill
Some plugins continue to unset all the plugins when enabled or disabled, it a good bet that enabling the JPEG plugin did just that.

Just get to ccsm any which way and re-enable the plugins you need/want, do the unity one last.
If you don't know then either run 
unity --replace
 when done log out/in and start over or ask for the basic list

---

### Post by wildmanne39 on 2011-06-06
> **sparker256 said:**
> I tried to put a jpg image on the top and bottom of the cube and it wanted to enable some plugin about jpg but that seems to have broken my unity 3d. The launcher does not even show and ctrl+alt+t does not start the terminal. Reinstalled but still not working so will have to see what else I can try.

:(  BillHi, that is one plugin that I did not try to activate, you can look in my signature if you need to reset unity or compiz the instructions are there. I am sorry to hear that you had a problem with it.

---

### Post by sparker256 on 2011-06-06
> **mc4man said:**
> Some plugins continue to unset all the plugins when enabled or disabled, it a good bet that enabling the JPEG plugin did just that.

Just get to ccsm any which way and re-enable the plugins you need/want, do the unity one last.
If you don't know then either run 
unity --replace
 when done log out/in and start over or ask for the basic list
A complete install with a new / and /home did the trick but not the easiest path. I used a daily live 053011 and now have to re tweak but will remember unity --replace.

Thanks Bill

---

### Post by mc4man on 2011-06-06
If you don't know the min plugins needed and ones you wish/have enabled then after you get it set up as you like  grab the list in case things get unset.. Several ways - while compiz is still using gconf you could simply go

```
gconftool-2 --get /apps/compiz-1/general/screen0/options/active_plugins
```
You could save the list to a file for reference
It's possible to also reset using the list though a bit awkward due to length - Ex. here - 
```
gconftool-2 --get /apps/compiz-1/general/screen0/options/active_plugins
[core,composite,opengl,decor,vpswitch,resize,place,cube,gnomecompat,move,text,regex,rotate,scale,scaleaddon,animation,expo,unityshell]


```

```
gconftool-2 -s --type=list --list-type=string /apps/compiz-1/general/screen0/options/active_plugins  [core,composite,opengl,decor,vpswitch,resize,place,cube,gnomecompat,move,regex,rotate,scale,scaleaddon,animation,expo,unityshell]

```

---


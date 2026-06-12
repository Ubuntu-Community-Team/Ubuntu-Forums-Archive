---
title: "Dual Screen Problem"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by mps69 on 2012-04-30
Just done a clean install of 12.04, from 10.10, everything is running ok, apart from the fact I've got two screens.
First problem seems to be having two panels, only way to decribe them these days, at top of each screen. Is there anyway to remove the notifications, or at least remove the panel completely.
Second problem is the location of the launcher bar, away to move it to the left screen 2?
I've played with the driver settings, without any success, the only one that seems to work it TwinView. The other setting is seperate X Screen, but this gives me a crash report, because I need to enable the Xinerama, and after a bit of searching around the forum, it's recomend that this is not selected.
I've also ensured that I'm using the correct drivers, or the one's recomended

I think a picture speaks a thousand words, these should explain my problem a bit better.

Can anyone recomend a solution?

Cheers


Display [IMG]http://i46.tinypic.com/w98iag.png[/IMG]

Graphic Card [IMG]http://i45.tinypic.com/2m3pr2u.png[/IMG]

Desktop [IMG]http://i45.tinypic.com/5kli1f.png[/IMG]

---

### Post by audiomick on 2012-04-30
Ok, it seems you have an nvidia graphics card. This is ok. I have one, and it works fine.

This means you should only use the utility called nVidia-settings to set up your screen, and not the standard Ubuntu one. In fact, I believe that when you open the standard Ubuntu one, you should be asked if you want to use the nVidia one. I haven't got 12.04 on any of my machines yet, but that has been the case since about 9.10 or so, so I can't see it having changed. One way to get to the nVidia tool should be to type "nvidia-settings" in the search box of the dash. As I said, can't check it right now, but I think that is right. Anyway, you have posted a picture of that utility, the second one, so you can open it somehow. ;)

So, 
You are right that you should not use Xinerama when using the nVidia drivers. Twin View does effectively the same thing as Xinerama, but is the nVidia proprierary solution. If you are using nVidia drivers, use Twin View.

As far as having the panel at the top on both screens goes, I don't think you can change that at the moment. I have 11.10 on my desktop, and this is the same there. To be honest, I didn't spend a long time trying to change it, but I couldn't find any way to change it. Annoying, but I expect that this will change at some time in the future. Maybe... ;)


To get the launcher over to the left of the left hand screen, you have to designate it as the primary screen. That is a checkbox in the nVidia settings utility. It is visible in your second picture. In fact, that picture shows exactly where you have to be to change that: the external screen is selected, as can be seen by the orange border. You only have to check the box labelled "make this the primary display for the x-screen".

Use the "apply" button when you have done your changes, and "save to x-org configuration file" to make them permanent.

One thing you need to bear in mind: you have 2 monitors of two different sizes. The way twin view (and Xinerama, incidentally) works is to make a virtual screen that goes around both monitors. You can see the total size in the "resolution" box in your first picture. 2880 is the width of both screens together, 1024 the height of the higher of the two. If they were one above the other, it would be 1600 x 1824, for instance. You can see the boundary of this virual screen in the shot of the nVidia utiliy. The dotted line below the AOC 2036 screen is the continuation of the virtual screen outside of where it is visible on the monitor. This area is there, but you can't see it on your monitor. This is generally not a problem. You just need to remember that it is there. You can "lose" your mouse in there, and if you are really unlucky, you can move a window such that the "close, minimise, maximise" buttons are in there and you have to use keyboard shortcuts to close the window.

I now have two monitors the same size, but I used a set-up with two different sized monitors for several years without a problem.

---

### Post by mps69 on 2012-04-30
Thanks, got the launcher bar on the far left, didn't even occure to me that changing the primary monitor would move the bar, do I feel right clutz now. 

Fingers crossed now sometime in the future we can change the Unity Panel if you have a second monitor.

---

### Post by audiomick on 2012-04-30
> **mps69 said:**
> 
Fingers crossed now sometime in the future we can change the Unity Panel if you have a second monitor.

I fully expect more configuration options in Unity as time goes by. Just have to wait and see if I'm right or not...

---


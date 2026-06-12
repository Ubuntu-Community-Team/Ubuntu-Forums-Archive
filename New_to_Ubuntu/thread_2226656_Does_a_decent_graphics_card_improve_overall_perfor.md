---
title: "Does a decent graphics card improve overall performance?"
date: 2014-05-28
forum: New to Ubuntu
---

### Post by wpurcell on 2014-05-28
Would adding a decent Graphics card (Nvidia) reduce the load on the CPU and improve the performance of Ubuntu overall? 
I'm looking at an Asus EN210 Silent with 1GB RAM. My Dell Optiplex 745's psu will not allow a card with a power connector.
I'm running a Core 2 Duo 2.13GHz with 4GB RAM.
I am using Ubuntu-gnome-14.04-amd64.
Just trying to gain overall performance. Not concerned with gaming, but with programs such as Google Earth, Sweet Home 3D, perhaps Blender, etc.
Thanks for your time!

---

### Post by mcduck on 2014-05-28
THat really depends on the task. Basically anything that causes CPU load will run on CPU regardless of what graphics card you have.

Of course applications that actually use graphics card for something more than basic desktop window management can benefit from better graphics card. (For Google Earth you do of course get improvemetns with better GPU, but there's a limit on how muc improvements actually make any difference after you get a reasonable framerate. Blender on the other hand can use GPU for rendering, as long as you have an nVidia card with Cuda support, so that's one place where a decent graphics card might easily be used instead of CPU for better performance).

However the card you are looking at is low-end card so depending on what you have now it might not make much of a difference, if any, and I probably wouldn't even bother switching GPU rendering on in Blender with that card as your CPU might quite well outperform it...

---

### Post by wpurcell on 2014-05-28
Hello mcduck! Thanks for the reply.
At the moment I have no card. The other two options I have (without driving 3/4 hour) are a Zotac GT610(2GB RAM) and a Zotac GT630 Synergy(2GB RAM).
What is your opinion of those?
I'm also considering upgrading the CPU to either a Core 2 Duo E6700(2.6GHz) or a Pentium Dual Core E6700(3.2GHz). A less expensive option to a GPU upgrade.
I can also upgrade the RAM from 4GB to 8GB.

---

### Post by sandyd on 2014-05-28
> **wpurcell said:**
> Would adding a decent Graphics card (Nvidia) reduce the load on the CPU and improve the performance of Ubuntu overall? 
I'm looking at an Asus EN210 Silent with 1GB RAM. My Dell Optiplex 745's psu will not allow a card with a power connector.
I'm running a Core 2 Duo 2.13GHz with 4GB RAM.
I am using Ubuntu-gnome-14.04-amd64.
Just trying to gain overall performance. Not concerned with gaming, but with programs such as Google Earth, Sweet Home 3D, perhaps Blender, etc.
Thanks for your time!

The en210 is not a very good card, depending on the resolution of your monitor.

Heres a performance comparison (passmark)

EN210: [http://www.videocardbenchmark.net/video_lookup.php?gpu=GeForce+210](http://www.videocardbenchmark.net/video_lookup.php?gpu=GeForce+210)
GT 610: [http://www.videocardbenchmark.net/gpu.php?gpu=GeForce+GT+610](http://www.videocardbenchmark.net/gpu.php?gpu=GeForce+GT+610)
GT 630: [http://www.videocardbenchmark.net/gpu.php?gpu=GeForce+GT+630](http://www.videocardbenchmark.net/gpu.php?gpu=GeForce+GT+630)

---

### Post by QIII on 2014-05-28
Please remember that anyone's opinion is just that -- an opinion.  Be careful of making purchase decisions based on recommendations here.  Those who provide their opinions risk nothing.  But it's your money being spent.

sandyd has pointed you towards some unbiased resources with actual measured results.  That sort of thing should be used to inform your decisions.  

Not to say that opinions are without merit, though.  mcduck's info was spot on and not just "opinion".  Letting you know that the card you were considering was not a powerful one and might not improve your performance was valuable information.

---

### Post by wpurcell on 2014-05-28
Well, that's not very good! My screen resolution is 1680x1050.
I might be better off getting a GeForce 8800gts and a new power supply.
Perhaps I'll just upgrade the CPU for the moment.

---

### Post by wpurcell on 2014-05-28
Thanks QIII.
Any and all advice is welcomed. I do realize the ultimate decision is mine, and the responsibility of that decision is mine also. If I make a bad one it's entirely my fault!
All is good!

---

### Post by mcduck on 2014-05-28
8800gts should definitely give you a noticeable improvement, especially with Blender (you'll be amazed at the speed a good GPU can give you with Cycles rendering!), and luckily decent quality power supplies aren't really that expensive so that sounds like a good plan.

I can't say much about CPU upgrade, although from what I recall about those CPU models the difference wouldn't be huge so it really depends on how cheap the upgrade would be. But what comes to RAM that's an easy decision to figure out; if you are maxing out on memory usage now then adding more makes sense, and if you aren't even using all 4GB you have then adding more wouldn't make any difference at all. (And if you go for the graphics card and GPU rendering with Blender, then it's the video RAM that's sets the limit anyway, and system RAM only comes to play with CPU rendering, physics simulations and Freestyle renders).

---

### Post by pqwoerituytrueiwoq on 2014-05-28
i don't know what your PSU wattage is but you probably could get a GT 630 and not upgrade your PSU, a quality 300W unit should be plenty for you
these new cards are very energy efficient
i know a optiplex 780 has a 300w unit that is rated for 90% efficiency
we are getting a gt 630 (2gb evga referb from newegg) for one of those where i am volunteering so the system can run 2 high res screens
i know a GT430 can run dual screens but it has to run full speed to pull that off
edit: that card runs unity beautifully

---


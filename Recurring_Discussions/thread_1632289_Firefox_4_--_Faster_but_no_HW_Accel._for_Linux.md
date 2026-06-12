---
title: "Firefox 4 -- Faster but no HW Accel. for Linux"
date: 2010-11-27
forum: Recurring Discussions
---

### Post by bwhite82 on 2010-11-27
Just installed it and was reading various articles about it. Found out Mozilla brought Hardware Acceleration to the table but omitted support for OpenGL. Your thoughts?

---

### Post by juancarlospaco on 2010-11-27
firefox--->Chromium
gwibber--->Hotot
Tomboy--->CherryTree

---

### Post by NCLI on 2010-11-27
> **Soldierboy said:**
> Just installed it and was reading various articles about it. Found out Mozilla brought Hardware Acceleration to the table but omitted support for OpenGL. Your thoughts?

That's FUD, it has support for HW acceleration in Linux, it's just not enabled by default yet.

---

### Post by bwhite82 on 2010-11-27
> **NCLI said:**
> That's FUD, it has support for HW acceleration in Linux, it's just not enabled by default yet.

Are you sure about that? I did indeed enable an option in 'about:config', called *layers.accelerate-all* but it had no change when I ran the mozilla hack where it shows your FPS.

Is this what you speak of?

Edit: The mozilla hack I speak of is here:
[http://demos.hacks.mozilla.org/openweb/HWACCEL/](http://demos.hacks.mozilla.org/openweb/HWACCEL/)

---

### Post by leef on 2010-11-27
That's a shame, I would have thought that the mozilla foundation would have used cross platform acceleration... either way it doesn't matter to me I'm using chromium.

---

### Post by Decatf on 2010-11-27
So that "Use hardware acceleration when available" check  box is just ornamental? :(

---

### Post by bwhite82 on 2010-11-27
> **Decatf said:**
> So that "Use hardware acceleration when available" check  box is just ornamental? :(

According to this developer (assuming from the comments), yes:

[http://blog.mozilla.com/joe/2010/11/10/fx4b7-hwaccel/](http://blog.mozilla.com/joe/2010/11/10/fx4b7-hwaccel/)

Read the comments of that blog post.

---

### Post by bwhite82 on 2010-11-27
Looks like you can help by building FF yourself and enabling the option there (high chance of failure though):

[http://blog.mozilla.com/joe/2010/09/15/so-you-want-to-help-us-with-hardware-acceleration/](http://blog.mozilla.com/joe/2010/09/15/so-you-want-to-help-us-with-hardware-acceleration/)

---

### Post by beew on 2010-11-28
Is it true that even FF discriminates against Linux? Now that really sucks!

---

### Post by unknownPoster on 2010-11-28
Quit twisting the facts to make it sound like Mozilla/FF is against Linux.
From the links posted above:

> 
**Right now we don&#8217;t plan on turning hardware acceleration on for  Linux, mostly due to driver problems.** We will gratefully accept help;  I&#8217;ve written up a blog post on [how to help us debug hardware acceleration problems]("http://blog.mozilla.com/joe/2010/09/15/so-you-want-to-help-us-with-hardware-acceleration/").  It might need to be a whitelist of drivers, rather than a blacklist (as  on Windows); helping us figure out what drivers work, and which don&#8217;t,  will also help *a lot*.
Emphasis is mine. It's not that Linux has been abandoned, it's that they are struggling with problems with Linux.

From Joe's (a FF dev) blog:

> 
However, enabling our implementation of accelerated composition using  OpenGL on Linux currently causes a lot of test failures, and we&#8217;d be *ecstatic* if you would try to help us fix them.

People that spread FUD are the bane of the internet.

---

### Post by Oxwivi on 2010-11-28
> **unknownPoster said:**
> Quit twisting the facts to make it sound like Mozilla/FF is against Linux.
My thoughts exactly after reading those posts.

---

### Post by Spice Weasel on 2010-11-28
Why do people have to post news stories then completely twist the article to make it sound sensational?

Example: "Ubuntu is going to be rolling release"... :-x

---

### Post by Oxwivi on 2010-11-28
If we didn't do that, we wouldn't be humans. ;-)

---

### Post by juancarlospaco on 2010-11-28
Any LiGNUx can be rolling release, if you want to...

---

### Post by Giant Speck on 2010-11-28
> **unknownPoster said:**
> words

Mozilla Corporation shill!

---

### Post by czr114 on 2010-11-28
Firefox devs need our help:

[http://jagriffin.wordpress.com/2010/08/30/introducting-grafx-bot/](http://jagriffin.wordpress.com/2010/08/30/introducting-grafx-bot/)

---

### Post by Decatf on 2010-11-28
I tested enabling  acceleration with the **layers.accelerate-all** option** (**[http://forums.mozillazine.org/viewtopic.php?f=23&t=1984355](http://forums.mozillazine.org/viewtopic.php?f=23&t=1984355))**.** On my system it ran slower than with it disabled. I guess the results may vary widely on Linux due to the various states of OpenGL with all the different drivers and hardware but bottom line they did not omit OpenGL from the Linux builds of Firefox 4 at all.

---

### Post by czr114 on 2010-11-28
> **Decatf said:**
> I tested enabling  acceleration with the **layers.accelerate-all** option** (**[http://forums.mozillazine.org/viewtopic.php?f=23&t=1984355](http://forums.mozillazine.org/viewtopic.php?f=23&t=1984355))**.** On my system it ran slower than with it disabled. I guess the results may vary widely on Linux due to the various states of OpenGL with all the different drivers and hardware but bottom line they did not omit OpenGL from the Linux builds of Firefox 4 at all.

Have you submitted a bug or system profile?

Try the test I posted above.

The devs are trying to flush out problematic drivers and setups and are in need of additional datapoints.

---

### Post by Helkaluin on 2010-11-28
Ye all be misunderstanding.

Hardware acceleration for RENDERING in Linux has long been here before the upcoming Firefox 4. They are using Cairo/XRender to do this even in Firefox 3.6. (I'm not sure about things earlier.)

The caveat of using XRender being that quite a lot of things influence its performance. For me, for example, running Nvidia 8400M GS with the blob driver, the performance at [http://demos.hacks.mozilla.org/openweb/HWACCEL/](http://demos.hacks.mozilla.org/openweb/HWACCEL/) fluctuates greatly depending on my WM. It's 30+ for Openbox, whether with or without xcompmgr, and a bare 2-3 FPS if I'm running Compiz. YMMV.

Hardware acceleration for COMPOSITING layers, however, is still experimental on Linux. As said previously in this thread, the option for turning on compositing with OpenGL is there. (So stop saying it isn't.) It's just that at many a times it actually slows down other parts of the performance that the net change is negative. Again, YMMV.

---

### Post by m4tic on 2010-11-29
People made the kinect work first on Linux, surprising how this is a big hill to go over.

---

### Post by chmmr on 2010-12-22
Possibly useful info on this:

[http://forums.mozillazine.org/viewtopic.php?f=23&t=2043851](http://forums.mozillazine.org/viewtopic.php?f=23&t=2043851)

[https://bugzilla.mozilla.org/show_bug.cgi?id=594319](https://bugzilla.mozilla.org/show_bug.cgi?id=594319)

Seems like there might be a performance regression specifically for hardware acceleration with FF4 betas and some Nvidia cards?  X server and cairo might be involved.

---

### Post by screaminj3sus on 2010-12-23
enabled this on my machine (minefield beta9pre, hd2600, fglrx 10.12) massive artifacts when scrolling, there is a reason why this isn't enabled in linux yet. Scrolling seemed smoother though.

---

### Post by zer010 on 2010-12-23
> **czr114 said:**
> Firefox devs need our help:

[http://jagriffin.wordpress.com/2010/08/30/introducting-grafx-bot/](http://jagriffin.wordpress.com/2010/08/30/introducting-grafx-bot/)
Awesome! I'm gonna have to get the latest FFbeta and run that. Since I use older hardware, I wanna make sure they have a dataset for my HW. I love it when I can help out my favorite projects! 
Thanks, czr114!
*I just ran the test and submitted the results. Not sure if it's because of my hardware, but that test took forever and with a lot of lag when I got to the interactive comparison section.

---

### Post by bikeboy on 2010-12-23
Works beautifully here at the moment, except Flash flickers badly. Better than the massive memory leak (growing 100mb/second) Flash caused with H/W accelerated layers on until recently :)

---

### Post by rajeev1204 on 2010-12-24
I am getting 11 fps with my ATI 4800 card and fglrx drivers.

---


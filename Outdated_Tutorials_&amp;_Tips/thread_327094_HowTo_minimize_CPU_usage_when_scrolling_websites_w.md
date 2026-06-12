---
title: "HowTo: minimize CPU usage when scrolling websites with Beryl"
date: 2006-12-28
forum: Outdated Tutorials &amp; Tips
---

### Post by franestepona on 2006-12-28
As the title says, I was looking for a solution to minimize the CPU usage since I surf the web quite a lot and it was a little bit annoying. I´m using Swiftfox, but it should work in firefox as well. The problem was the sooth scrolling, to inactivate it go to Edit-Preferences-Advanced and uncheck smooth scrolling.

Scroolling still requires lot of CPU usage, but much better now, hope this help some of you.

---

### Post by ffi on 2006-12-28
I found disabling the "disable gl yield setting" in the advanced beryl options in beryl-manager greatly improved scrolling.

---

### Post by franestepona on 2006-12-28
Where is that option? Cant find it

---

### Post by ffi on 2006-12-28
In the right click menu of beryl-manager (the thing in the system tray)-> "Advanced Beryl Options"-> "Disable GL Yield Setting Use this to fix some redraw bugs" and untick the option.

---

### Post by franestepona on 2006-12-28
Well looks like iI dont have that option, I'm using beryl-manager 0.1.4. Thanks for the advice anyway. I'll try to find that option in the next updates.

---

### Post by ffi on 2006-12-28
> **franestepona said:**
> Well looks like iI dont have that option, I'm using beryl-manager 0.1.4. Thanks for the advice anyway. I'll try to find that option in the next updates.
Same version I am using :???:

You right clicked the beryl icon in the system tray?

---

### Post by AgenT on 2006-12-28
> **ffi said:**
> Same version I am using :???:

You right clicked the beryl icon in the system tray?
This option is not available in 0.1.4 and I do not remember it ever being available in 0.1.3 CVS.
```
 $ dpkg-query -s beryl-core
Package: beryl-core
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 1312
Maintainer: Trevi <trevi55@gmail.com>
Architecture: i386
Version: 0.1.5+svn20061227-r2089+3v1ubuntu0
```

---

### Post by ffi on 2006-12-29
Wrong package, it's beryl-manager ;) 

sudo apt-get install beryl-manager
beryl-manager
->change setting

---

### Post by franestepona on 2006-12-29
Here you have a screenshot.

---

### Post by ffi on 2006-12-29
Strange :???:

maybe it's graphics card specific?? I have an nvidia 6600GT

---

### Post by franestepona on 2006-12-29
Yeah that could be a reason, I have an ATI mobility Radeon. I'll check that out to see if i can find that option somewhere. But maybe it's just that my graphic card dont support it. Thanks for the advice anyway.

---

### Post by AgenT on 2006-12-29
Confirmed a no-go on a ATI Mobility (using the radeon freedom drivers).

---

### Post by ffi on 2006-12-29
Too bad, the option isn't there because disabling it fixed the exact problems you described....which I think might have appeared since Beryl 0.14, but I am not sure, I could have been playing around with settings too ](*,) 

and to think my obssion with xgl/compiz started hoping it could fix the smooth scrolling problems of Opera, which turned out to be a very very long standing bug of Opera Linux/Mac/BSd and Solaris and which was finally fixed this month (for Linux at least not Mac :p )

Anyway it still might be useful for other nVidia users....

---

### Post by AgenT on 2006-12-29
Using todays SVN with the [/etc/drirc "hack"]("http://bugs.beryl-project.org/trac/ticket/37") not only fixed the maximized window problem but also boosted overall performance. Maximized browser (Firefox) shows a 100-130% FPS boost. Scrolling is still jittery but not as much as before. This is using radeon driver. Note: using the ati xorg driver should also work since ati is just a wrapper to three different drivers, including radeon.

---

### Post by d3v1ant_0n3 on 2006-12-29
> **franestepona said:**
> Here you have a screenshot.

Off topic, but what gtk theme is that? I like it.

I don't have the option here on Beryl SVN 0.1.5

---

### Post by franestepona on 2006-12-30
The gtk theme is BlueHeart combined with "fadeout" emerald theme. By the way AgenT How did you did that trick?

---

### Post by franestepona on 2006-12-30
Uh sorry I just realized you posted the link, thanks I'm gonna try that out.

---

### Post by AgenT on 2006-12-30
The drirc information in now in the [Beryl Forums FAQ]("http://forum.beryl-project.org/viewtopic.php?f=35&t=1500").

---


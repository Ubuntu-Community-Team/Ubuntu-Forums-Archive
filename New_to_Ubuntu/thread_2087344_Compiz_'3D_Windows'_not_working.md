---
title: "Compiz '3D Windows' not working"
date: 2012-11-23
forum: New to Ubuntu
---

### Post by Mars1996 on 2012-11-23
The 3D windows of my compiz manager is not working.

Whenver I rotate the desktop cube, the cube does not show up and the windows do not display properly.

---

### Post by stinkeye on 2012-11-23
The 3d windows plugin no longer works. Disable.(The cube still works just not with the 3d windows plugin)
You will see some plugins fail as Canonical focuses compiz functionality just for unity.
See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=12369441&postcount=4") if you need to reset compiz/unity.

---

### Post by monkeybrain2012 on 2012-11-23
It has been broken since 11.10 and is still broken in 12.04. But it works in 12.10, so either wait for a Unity upgrade in 12.04 (most likely in 12.04.2 in late jan) or upgrade to 12.10. 

If you are already using 12.10 then it may be your hardware or your configurations.

---

### Post by Mars1996 on 2012-11-23
> **monkeybrain2012 said:**
> It has been broken since 11.10 and is still broken in 12.04. But it works in 12.10, so either wait for a Unity upgrade in 12.04 (most likely in 12.04.2 in late jan) or upgrade to 12.10. 

If you are already using 12.10 then it may be your hardware or your configurations.

I am currently using 12.10. What do you mean by the configurations ?

---

### Post by monkeybrain2012 on 2012-11-23
> **Mars1996 said:**
> I am currently using 12.10. What do you mean by the configurations ?

I have attached a screenshot of my cube. The window appears to be a bit odd (it forms 4 walls outside the cube instead of surrounding the cube) but the cube is definitely there. 

By configuration I mean settings in ccsm.

---

### Post by stinkeye on 2012-11-23
I am using 12.10 and the 3d windows plugin does not render correctly
using the nvidia or nouveau drivers.
In my 12.04 install 3d windows plugin renders fine.
Your experience may vary depending on your GFX card and the way
proprietary drivers implement OpenGL.

For some explanation see a compiz developers blog.
[**_[COLOR="DarkRed"]On the future of Graphics Drivers[/COLOR]_**]("http://smspillaz.wordpress.com/2012/06/08/on-the-future-of-graphics-drivers/")

[**_[COLOR="darkred"]Maintainers for the unsupported plugins[/COLOR]_**]("http://smspillaz.wordpress.com/2012/09/07/maintainers-for-the-unsupported-plugins/")

---

### Post by monkeybrain2012 on 2012-11-23
> **stinkeye said:**
> I am using 12.10 and the 3d windows plugin does not render correctly
using the nvidia or nouveau drivers.
In my 12.04 install 3d windows plugin renders fine.
Your experience may vary depending on your GFX card and drivers.

For some explanation see a compiz developers blog.
[**_[COLOR=DarkRed]On the future of Graphics Drivers[/COLOR]_**]("http://smspillaz.wordpress.com/2012/06/08/on-the-future-of-graphics-drivers/")
[**_[COLOR=darkred]Maintainers for the unsupported plugins[/COLOR]_**]("http://smspillaz.wordpress.com/2012/09/07/maintainers-for-the-unsupported-plugins/")

Never tried 3d windows on 12.04 because the cube itself is not working (flashing while rotating and windows don't carry over with cube while rotate. I stick to the default in 12.04)  I use Nouveau because of this bug [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/729979](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/729979)

---

### Post by johnnydas on 2013-04-27
> **monkeybrain2012 said:**
> I have attached a screenshot of my cube. The window appears to be a bit odd (it forms 4 walls outside the cube instead of surrounding the cube) but the cube is definitely there. 

By configuration I mean settings in ccsm.

Hi there. 
Did you manage to solve the issue with the 3d windows showing outside the cube, and if yes in what way?

---

### Post by Frogs Hair on 2013-04-27
3D windows are  included with the compiz plugins in 13.04   and are working .I disabled mouse rotate in order to test and the windows are distanced from the cube until mouse rotate is enabled. I am not familiar with the plugin though.

---

### Post by monkeybrain2012 on 2013-06-01
> **Frogs Hair said:**
> 3D windows are  included with the compiz plugins in 13.04   and are working .I disabled mouse rotate in order to test and the windows are distanced from the cube until mouse rotate is enabled. I am not familiar with the plugin though.

What do you mean by "mouse rotate"?  If you are referring to the binding options in the rotating cube they are disabled by default, see attached screenshot.

---

### Post by bbaaxx on 2013-07-06
I'm getting the exact same behavior as the pics on Mars post using 13.04, I think it has something to do with the ATI propertary driver for my 7700 AGP because on my other laptop (INTEL AGP) 3D windows won't work at all.

---


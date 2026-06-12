---
title: "Drag &amp; Drop"
date: 2011-09-22
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by EgoGratis on 2011-09-22
I have one question:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/756614](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/756614)

It says that it is "fixed" for Unity 2D and Unity 3D BUT if i test it only Unity 2D successfully enables me to Drag & Drop launcher to the desktop and Unity 3D doesn't allow me to do that! I was wondering if this is a bug in Unity 3D or there are just two different opinions if Drag & Drop for this user action should be available to the user or not?

It would be great if Unity 2D and Unity 3D would allow user to do that now because Gnome 3 does not have GUI option to create custom desktop launcher? But not just because of that, Drag & Drop is just cool and more things Ubuntu user can do with Drag & Drop more it will like Unity! There will not be 100% hardware compatibility and Compiz and WiFi will give troubles to some Ubuntu users and so on... but good Drag & Drop capabilities could make it up at least a bit for them and in general for all Ubuntu users too?

---

### Post by mc4man on 2011-09-22
Never seen that working in unity 3d, fix released or not. 

At this point can't really check on a 13" laptop (1200X800) which uses the 'Desktop' dash because there is only a 1/2 ' or less of the desktop exposed when the dash is open 
Previously, before  the unity 3d dash got even bigger when the icons where enlarged, attempting would produce the typical error message

Reopen the bug if you're getting that error..
(Myself don't care about D&D to Desktop, they can be dragged to launcher or just copied to the desktop or created on if one wanted a launcher there

Ot - The size of the dash in unity 3d, from an appearance standpoint is terrible, though from a using it perspective size doesn't really matter, unity-2d looks better with about the same 'usability'

---

### Post by EgoGratis on 2011-09-22
> Reopen the bug if you're getting that error..That error is "fixed" BUT in two different ways. I was reading some time back what would be preferred behavior  but i don't know where i was reading that and what the final  decision was.

In Unity 2D it is "fixed" in the way that you can Drag & Drop launcher from Dash on the desktop. It works fine and i like what i can achieve with mouse or i imagine with finger on touchscreen device to?

In Unity 3D it is "fixed" in a way that you don't get that message any more but at least based on my test it does not allow you to Drag & Drop launcher to the desktop. You just don't get that massage any more?

"The problem" is that a lot of different profiles of users do use Ubuntu and having a lot of Drag & Drop actions supported instead of using terminal or copying files from different location and editing it in Gedit... to achieve the same goal i imagine does help a lot of users. Just like great "keyboard shortcuts" does help a lot of Ubuntu users.

And we must keep in mind that there is no GUI way right now that works in default install for user to create custom launcher on the desktop. There are just some workarounds:

[http://ubuntuforums.org/showthread.php?t=1837224](http://ubuntuforums.org/showthread.php?t=1837224)

I do agree that on small devices Dash covers the whole screen but still on most of devices you do get some space left on the desktop to Drag & Drop the content of the Dash to it.

---

### Post by mc4man on 2011-09-27
There is some 'oddity' possibly going on with the D&D from dash to Desktop.
In a fully updated beta 2 about 10 hrs. ago it would not work. After a cold boot this morning (no add. updates) it is was working fine

Now with another fresh cold boot it's not working again. Very odd...

Edit: it seems it may depend where it's grabbed from, if taking from 'frequently used' won't work, from 'installed' it will.

---

### Post by EgoGratis on 2011-09-27
> Edit: it seems it may depend where it's grabbed from, if taking from 'frequently used' won't work, from 'installed' it will.

Yes! Just few minutes back i tried it and i was getting the same result as you mention! Before it did not work for  'frequently used' or 'installed'. Now it does work for 'installed' and i get the "error" mentioned in bug report for the 'frequently used'. I hope this is indicator that user will be able to drag & drop application launcher from Dash to the desktop in Unity 3D after all!

---

### Post by EgoGratis on 2011-09-27
OK i made some tests.

User can drag & drop any application launcher from Dash to desktop (installed section right now) and it can customize it too it's needs. Than it can drag it to Unity launcher and it can remove it from Unity launcher.

Maybe in the future there will be more logic behind it, for example if user drags custom launcher to Unity launcher it automatically creates copy in .local/share/applications/ and user then can remove it from location it was added from and it won't be removed from Unity launcher automatically! This way user can find it in the Dash too, but that is more advanced capabilities and developers will decide that.

Users have (one) simple and default GUI option in Unity 3D now to create custom launcher and i am fine with that! Thanks developers!

---

### Post by EgoGratis on 2011-10-10
I tested this today again and now it works in Unity 3D for 'Most Frequently' too! I see there was new bug opened and it was fixed! Great!

I noticed back then something else and i tested it today again. If i use Unity 2D it worked fine before it was fixes in Unity 3D but now it does not work anymore! Some kind of "permission error" happens and instead of application launcher .desktop file owned by root is created on the desktop.

---

### Post by mc4man on 2011-10-10
yep - fixed in 3d, now broken in 2d

---

### Post by t1497f35 on 2011-10-10
> **EgoGratis said:**
> OK i made some tests.
Maybe in the future there will be more logic behind it, for example if user drags custom launcher to Unity launcher it automatically creates copy in .local/share/applications/ and user then can remove it from location it was added from and it won't be removed from Unity launcher automatically! This way user can find it in the Dash too, but **that is more advanced capabilities** and developers will decide that.

No, **advanced capabilities** is when you're doing some (extremely) sophisticated stuff, but what you're suggesting is common sense and should be implemented (hopefully by 12.04).
It would be lame to expect the user to keep the dragged file (not deleting it nor moving it anywhere after dragging) so that it doesn't disappear from the launcher/dash when removed, but for now the lack of such functionality is ok since Unity is young.

---


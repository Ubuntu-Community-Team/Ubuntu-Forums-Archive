---
title: "Oneiric &lt;-&gt; Compiz Config Settings Manager Issues"
date: 2012-04-04
forum: New to Ubuntu
---

### Post by sknth on 2012-04-04
Hi All,

I have just finished installing Ironhide for my Dell XPS L502X, and it seems to work great. A test with glxspheres gives me a nice smooth animation.

11.10 has Unity by default, and I have installed compizconfig settings manager. Now that I have installed all the necessary graphics drivers, desktop cube etc etc should work right?

It's not working! The moment I disable Desktop Wall and plugins, and Desktop Cube is chosen, the Unity taskbar disappears, the notification bar disappears, and all I am left with is the Desktop wallpaper. After this, I have to navigate to tty1 and reset unity.

Why is this happening? I did not install any of the recommended Nvidia drivers as I know they cause problems. Hence, Ironhide.

---

### Post by Gone fishing on 2012-04-04
I did that too - just wondered if Unity would work with the cube I learned it didn't.

To fix it I opened a terminal alt control F1 and installed fluxbox (I wanted to do this anyway) sudo apt-get install fluxbox then restarted logged into fluxbox and opened ccsm and un-ticked the the cube and rotate cube and  re-ticked the wall and all was well again.

I expect there is an easier way like deleting /home/user/.config/compiz-1 or /home/user/.compiz-1 but I'm not sure.

---

### Post by sknth on 2012-04-04
> **Gone fishing said:**
> I did that too - just wondered if Unity would work with the cube I learned it didn't.

To fix it I opened a terminal alt control F1 and installed fluxbox (I wanted to do this anyway) sudo apt-get install fluxbox then restarted logged into fluxbox and opened ccsm and un-ticked the the cube and rotate cube and  re-ticked the wall and all was well again.

I expect there is an easier way like deleting /home/user/.config/compiz-1 or /home/user/.compiz-1 but I'm not sure.
Ok. The unity --reset worked for me, but wobbly and fading window settings also disappeared.. So now my question is, what do I do to get the cube?

---

### Post by Gone fishing on 2012-04-04
Feeling brave?

[http://www.tuxgarage.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://www.tuxgarage.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

[http://reformedmusings.wordpress.com/2011/05/05/howto-get-the-compiz-desktop-cube-in-ubuntu-11-04-natty-and-unity/](http://reformedmusings.wordpress.com/2011/05/05/howto-get-the-compiz-desktop-cube-in-ubuntu-11-04-natty-and-unity/)

Post back if it works maybe I'll try too ;)

---

### Post by kazztan0325 on 2012-04-04
> **sknth said:**
> Ok. The unity --reset worked for me, but wobbly and fading window settings also disappeared.. So now my question is, what do I do to get the cube?

Hi sknth,

It seems there is a way to enable cube here:

**"How to correctly enable Desktop Cube in Unity 3D"**
[http://askubuntu.com/questions/86977/how-to-correctly-enable-desktop-cube-in-unity-3d]("http://askubuntu.com/questions/86977/how-to-correctly-enable-desktop-cube-in-unity-3d")

However I myself have not tried it yet...

---

### Post by sknth on 2012-04-04
> **kazztan0325 said:**
> Hi sknth,

It seems there is a way to enable cube here:

**"How to correctly enable Desktop Cube in Unity 3D"**
[http://askubuntu.com/questions/86977/how-to-correctly-enable-desktop-cube-in-unity-3d]("http://askubuntu.com/questions/86977/how-to-correctly-enable-desktop-cube-in-unity-3d")

However I myself have not tried it yet...
I tried it, but it didn't work. I'm not sure why. I will try rebooting to see if that makes a difference.

---

### Post by kazztan0325 on 2012-04-04
> **sknth said:**
> I tried it, but it didn't work. I'm not sure why. I will try rebooting to see if that makes a difference.

I guess maybe it would work after rebooting.
Could you get Cube?

---

### Post by wildmanne39 on 2012-04-04
Hi, actually the cube is easy to setup in 11.10 use the second link in my signature to the wiki, just make sure you use the one for 11.10 and it will miss up your desktop until you are done but if you keep going everything will come back and I know I wrote the guide and spent a month testing it.

With your video card it may never work right though.
Thanks

---


---
title: "Compiz"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by sameer.india on 2008-07-14
How do I use compiz to make the effects in this video

[http://www.youtube.com/watch?v=x4fTh0x3xLE&feature=related](http://www.youtube.com/watch?v=x4fTh0x3xLE&feature=related)

---

### Post by talsemgeest on 2008-07-14
Have you installed the compiz config settings manager?

---

### Post by kpkeerthi on 2008-07-14
... and the instructions from here  [http://wiki.compiz-fusion.org/CompizFusionPlugins](http://wiki.compiz-fusion.org/CompizFusionPlugins)

---

### Post by sameer.india on 2008-07-16
I have done the above.
But when I have a video playing when i use desktop cube or expo the video doesn't stick to the desktop it was on.
It stays where it was and is the same size.

---

### Post by talsemgeest on 2008-07-16
I'm afraid that is a problem with your graphics, not compiz. What graphics are you using?

---

### Post by Canis familiaris on 2008-07-16
Do you use an ATi card? I had the same problem and I fixed it by this post:
[http://ubuntuforums.org/showpost.php?p=5222068&postcount=6](http://ubuntuforums.org/showpost.php?p=5222068&postcount=6)

---

### Post by sameer.india on 2008-07-16
thanks!!
what's a skydome by the way.

---

### Post by talsemgeest on 2008-07-16
A skydome is to do with the desktop cube. When you start up the cube, the image that you set as the skydome is like a 3d wallpaper behind your cube.

As seen in this image: [http://www.opendesktop.org/CONTENT/content-pre2/64319-2.jpg](http://www.opendesktop.org/CONTENT/content-pre2/64319-2.jpg)

---

### Post by sameer.india on 2008-07-17
I use the intel graphics card

---

### Post by sameer.india on 2008-07-17
And the video doesn't flicker but instead it just doesn't move with the cube.

---

### Post by talsemgeest on 2008-07-17
Well the way you have it set up makes it impossible to make the video move with the cube.

There is one way you can get it working though. I know you can do it in vlc, you have to go into the preferences and change the video output to something other that xvideo.

---

### Post by sameer.india on 2008-07-17
what is wrong with the way i set it up.

---

### Post by talsemgeest on 2008-07-17
It is the way the video is being displayed.

---

### Post by phelixnyc on 2008-07-17
Hate to hijack a thread but how do you make thumbnails of minimized windows?

---

### Post by Canis familiaris on 2008-07-17
> **phelixnyc said:**
> Hate to hijack a thread but how do you make thumbnails of minimized windows?

Not possible yet. it is a bug in xorg which is yet to be resolved.
There was a hacky way in Beryl which showed non-live thumbnail but I am not finding that for Compiz.
If you find a way kindly tell me also.

---

### Post by phelixnyc on 2008-07-17
I did not mean make them thumbnails but view them as thumbnails when I hover the cursor over them?

---

### Post by Canis familiaris on 2008-07-17
> **phelixnyc said:**
> I did not mean make them thumbnails but view them as thumbnails when I hover the cursor over them?
Not impossible but someone has to code such a plugin which would take screenshot for last minimized state.
At least I don't know any plugin which does that yet.
As for 'live' thumbnails Compiz cannot do it yet.

I discussed this in the following thread. You may bump it and see if anyone else have better answers.

[http://ubuntuforums.org/showthread.php?t=845303](http://ubuntuforums.org/showthread.php?t=845303)

---

### Post by sameer.india on 2008-07-18
I am still not getting the video to move with the cube.

---

### Post by phelixnyc on 2008-07-18
It is possible.  As you can see from screen shot thumbnail previews work in 8.04.

---

### Post by Canis familiaris on 2008-07-18
No it will work when the Window is unminimized.
However it will not work when Window is minimized.

Minimize the Window and try again.

---

### Post by phelixnyc on 2008-07-18
I understand that.  Maybe I did not express exactly what I wanted.  I am satisfied with it.

---

### Post by sameer.india on 2008-07-21
Well what about my problem?????

---

### Post by talsemgeest on 2008-07-21
Ok first you install VLC media player.

---

### Post by sameer.india on 2008-07-21
right I have the vlc media player

---

### Post by sameer.india on 2008-07-22
now what????????

---

### Post by jordanmthomas on 2008-07-22
Basically what you need to do, sameer is to set the video output to x11.
To do this in vlc, go to Settings --> Preferences

Then, at the bottom right, be sure "Advanced Options" is enabled.
On the left panel, go to Video --> Output Modules.
You will see in the right pane a dropdown box labeled "Video Output Module"
Choose "X11 video output" from this dropdown box.

Then, at the bottom of the settings window click save.

You may need to restart vlc for the settings to take effect.
I'm sorry if your computer doesn't use English, as you'll obviously have to translate my instructions.  

VLC is not the only player that you can do this with.  For example, mplayer has the commandline option -vo to select a video output.
```
mplayer -vo x11 file
```  will give you the desired effect, and the gui version of mplayer has an option somewhere in its preferences to select an output.

Hope this helps.

---

### Post by sameer.india on 2008-07-22
thanks i'll try that out!!!!!

---


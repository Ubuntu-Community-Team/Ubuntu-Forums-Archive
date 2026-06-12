---
title: "Webcam working with cheese"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by pankirk on 2008-08-30
I have my web cam and I used this tutorial to set it all up and everything: [http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/](http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/)

It works well (not great, Firefox always freezes after a while) on websites like stickam.com and it works on meebo.com (aim-type website) and I just want to know why every time I open up cheese I get this screen:
[img]http://i33.tinypic.com/2bedsi.jpg[/img]

How can i fix this error? I know I should be seeing a picture of whatever my web cam is pointing at, not that screen I see... Also, I should point out that my web cam works fine in camorama web cam viewer as well as "gstreamer-properties" or whatever it is... I just don;t know why cheese is broken. Thanks in advance.

Maybe this has something to do with it? When I start up "gstreamer-properties" from terminal, I get these errors:
> 
Gtk-WARNING **: Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'



---

### Post by Tzimisce on 2008-08-30
Are you sure that's an error? That looks more like a video test, or lack-of-feed problem.

---

### Post by gmxgeek on 2008-08-30
Yeah, that looks more intentional, either as a video test for color etc, or as a singal that something isn't plugged in.

---

### Post by pankirk on 2008-08-30
Really? It did that even before I got my we bcam tho so... I don't know what the problem is. Also, My web cam works on basiacally everything else BUT cheese. It's a bit odd :mad:

---

### Post by gmxgeek on 2008-08-30
> **pankirk said:**
> Really? It did that even before I got my we bcam tho so... I don't know what the problem is. Also, My web cam works on basiacally everything else BUT cheese. It's a bit odd :mad:

Well, if it did this before you got the webcam, then it is most likely a connection error somewhere between cheese and the cam. Doublecheck all of your connections and see if there are some configuration settings with cheese that might be causing it. I am unfamiliar with cheese so my help here is limited.

---

### Post by Tzimisce on 2008-08-30
I am also unfamiliar with cheese, I had issues with webcams (locking my pc up) aswell so I ditched them for stability.

---

### Post by pankirk on 2008-08-30
Hmm, how do I check the connections? I have the USB camera connected nicely right into the back of my computer?

---

### Post by gmxgeek on 2008-08-30
> **pankirk said:**
> Hmm, how do I check the connections? I have the USB camera connected nicely right into the back of my computer?

Yeah, just double check all the wires are hooked up right. If not that, then there might be some kind of input selector in the software, so double check that it is USB or whatever. Like I said, i can't really be too much help here.

---

### Post by pankirk on 2008-08-30
Well, i double checked and still no luck... I don't think its because it's plugged in wrong. Maybe because I dont have some sort of driver to work it?

---

### Post by Crafty Kisses on 2008-09-05
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

---


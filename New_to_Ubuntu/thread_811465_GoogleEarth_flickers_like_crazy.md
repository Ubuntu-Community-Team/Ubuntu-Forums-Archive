---
title: "GoogleEarth flickers like crazy"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by carloslosgrande on 2008-05-29
[FONT="Comic Sans MS"]I got googleearth running just fine except it flickers. If I was epileptic I'd be in big trouble. Its really quite bad. 
So I guess its not running just fine
I have compiz running no trouble at all, 3d stuff. Nothing else seems to be having any difficulties with the video.[/FONT]

---

### Post by tubbygweilo on 2008-05-29
I had this problem when using the left click on the mouse or iirc even moving the mouse would cause the googleearth image to craze over and things would slow almost to a halt. 

I solved the problem by System > Preferences > Appearance > Visual Effects > None, this worked for my ThinkPad R61e T8100 4GB Ubuntu 8.04 Intel GMA X3100

Hope this helps.

---

### Post by netztier on 2008-05-29
> **carloslosgrande said:**
> 
I have compiz running no trouble at all, 3d stuff. Nothing else seems to be having any difficulties with the video.[/FONT]

ATI Chip? Using restricted drivers? And have desktop effects enabled?

Same Problem here, not only with Google Earth, but also with Blender (3D Software) or screensavers that use OpenGL.

Workaround: disable desktop effects when using these apps. Solution? no clue...

regards

Marc

---

### Post by denham2010 on 2008-05-29
Heya all,

I had the same problem in pre Hardy distros. Google Earth would not play nice with composited screens.

One solution is to turn off compositing when running Google Earth. Not the ideal of course.

The other solution you may try is to open Compiz settings (Advanced Desktop Effects Settings) and make sure you have the Video Playback and Workarounds plugins activated. It's these plugins that try to stop the mis-behaviour of some apps.

Again, if you are using Gutsy, it may not solve the issue (it didn't for me), but in Hardy, I have not had a problem with Google Earth at all.

Hope this might help!

---

### Post by carloslosgrande on 2008-05-29
[FONT="Comic Sans MS"]Yeah ATI card, already got *video playback* and *workarounds* selected. Turning off compiz seems the only solution. bummer.
Well thanks anyway guys.
wanted to check this out you see [http://www.ecogeek.org/content/view/1659/](http://www.ecogeek.org/content/view/1659/)[/FONT]

---


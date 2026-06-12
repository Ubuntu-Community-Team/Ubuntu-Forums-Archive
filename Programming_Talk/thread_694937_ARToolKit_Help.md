---
title: "ARToolKit Help"
date: 2008-02-12
forum: Programming Talk
---

### Post by chrislesueur on 2008-02-12
Hey im a newbie to ARToolKit and i really need some help!..

Ive just set up ArtToolKit and got an example working with a box appearing on the 2D pattern.

My problem is...

I cant get my head round tutorials, does anyone know where i can find a 'new user' tutorial (all i can seem to find are for more advanced users) or can tell me how i go about setting up my own 3D image?

Can i just replace a current file from one of the examples or do i have to edit code? Ive think ive got as far as exporting the right file type from Cinema 4D but I then dont know what to do with this file...

Please can anyone give me a hand.

Many Thanks

Chris

---

### Post by geraldm on 2008-02-13
The sourceforge site for the project has a place for links to tutorials.
Have you found a place where the visual hardware is described/forSale or at least the components are made available, so that a hobbiest could at least build the hardware?  The information on the site seems to be all software related.  Perhaps the hardware is only for the research lab or else made available from class course materials?

Gerald

---

### Post by skullmunky on 2008-02-14
Did you try the tutorials on the HITLab site?

[http://www.hitl.washington.edu/artoolkit](http://www.hitl.washington.edu/artoolkit)

For the hardware - you don't need anything special to get started with, just a webcam.  If you want the HMD for AR overlay, it sounds like you can just get any HMD visor device and mount the camera on it.  

[http://www.hitl.washington.edu/artoolkit/documentation/hardware.htm](http://www.hitl.washington.edu/artoolkit/documentation/hardware.htm)

They recommend using a regular NTSC or PAL cam and a capture card, so just make sure you get a capture card with good Video4Linux drivers.  

For HMD's, products appear and disappear really quickly, but you can use an off-the-shelf product, you don't need anything specially made at HIT.  Try stereo3d.com for product reviews & discussions of headmounts and other VR/AR gear.  

I'd be interested to hear your experiences with it, what works, what's difficult, etc - haven't had time to hack on that for a while but it's definitely on my list.  Along with OpenCV, OpenSG, Panda, and python-ogre.

If you can make a compiz plugin for the wiimote, I wonder if you can make one for ARToolkit... think about that, your XGL desktop overlayed on your actual desktop.   :)

---


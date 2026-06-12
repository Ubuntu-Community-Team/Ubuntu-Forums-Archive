---
title: "Gimp won't open a Canon .cr2 file"
date: 2014-06-29
forum: New to Ubuntu
---

### Post by J Tinsby on 2014-06-29
Hello,

I just installed Gimp and along with it a program or plug-in called 'dcraw' supposedly to allow me to edit my .cr2 Canon raw image files. The install of Gimp was done using Synaptic. I don't see any option to use the "dcraw" in the options of Gimp. Maybe it will appear after I'm done posting this message :D

But when I drop a .cr2 file into Gimp I get all sorts of error messages. Refer to screenshot below.

What didn't I put in when I installed Gimp that I should have? Seems to be a recurrent theme, IE: you install a program and then find out you didn't install enough of it <sighs>

Looking more closely at Synaptic, I see that it's indicating that I have ufraw-batch installed, that's not the standalone one. But if it's there where is it, and why isn't it working, yet?

Thanks in advance!

J T

---

### Post by vanessax on 2014-06-29
Did you try the UFRaw GIMP plugin?  It works on *some* Canon CR2 raw image files.

[http://ppa.launchpad.net/crass/ufraw/ubuntu](http://ppa.launchpad.net/crass/ufraw/ubuntu)

---

### Post by J Tinsby on 2014-06-30
> **vanessax said:**
> Did you try the UFRaw GIMP plugin?  It works on *some* Canon CR2 raw image files.

[http://ppa.launchpad.net/crass/ufraw/ubuntu](http://ppa.launchpad.net/crass/ufraw/ubuntu)

Yes I have it loaded now and it works, but not the way I was hoping it would.

I can drop a .cr2 file into Gimp, that causes UFD to open in it's own window, not in the Gimp editing area. I have to then click on "OK" in UFD, that makes it import into Gimp, where I can work on it.

I was hoping that the RAW file reader would integrate in to Gimp, elminating a lot of steps just to get an image open to work on it. There doesn't seem to be any reference in the Gimp toolbar that points to any sort of plug-in or add-on program.

Is this the way Gimp behaves with a RAW file? I am used to using other graphic programs so what I am getting seems a bit odd. :/  There is a bit of correlation to the way PSP does using the "Bridge" feature maybe this is what the developers were trying to do with Gimp? 

Or did I install UFDraw in the wrong place? It's the standalone version for single files, not batch file editing. As it is now, UFD only opens the .cr2 file but you can't do any much editing with it, at least I couldn't find a way to do that.

Would be nicer if UFD was integrated into Gimp, maybe it is and I'm unable to find out how to do it.

Thanks,
J T

---

### Post by slonk on 2014-06-30
The raw file really doesn't have a ready-to-edit picture.  At the very least you need to do one raw->jpeg conversion using one profile (which might or might not be automatically adjusted based on the picture).  Don't be mislead by what the camera is doing, the jpeg making inside the camera is actually a very complex process doing a lot of "photoshopping".

Why are you trying to use the cr2? Is the jpeg from the camera not available?

---

### Post by J Tinsby on 2014-06-30
> **slonk said:**
> The raw file really doesn't have a ready-to-edit picture.  At the very least you need to do one raw->jpeg conversion using one profile (which might or might not be automatically adjusted based on the picture).  Don't be mislead by what the camera is doing, the jpeg making inside the camera is actually a very complex process doing a lot of "photoshopping".

Why are you trying to use the cr2? Is the jpeg from the camera not available?

hi slonk,

As I'm sure you know the RAW file has no or very minimal correction of any type applied, jpgs are compressed and every time you open one to edit it you lose more and more quality. I like to have the control of doing my Photoshopping to a RAW file and making a .jpg, whilst keeping the original unmodified. Yes the .jpg is available, I use them all the time, a times I will shoot both simulaeously.

So what I am describing as to the behaior of Gimp is the way it's supposed to work?

J T

---

### Post by slonk on 2014-07-01
> **J Tinsby said:**
> hi slonk,

As I'm sure you know the RAW file has no or very minimal correction of any type applied, jpgs are compressed and every time you open one to edit it you lose more and more quality. I like to have the control of doing my Photoshopping to a RAW file and making a .jpg, whilst keeping the original unmodified. Yes the .jpg is available, I use them all the time, a times I will shoot both simulaeously.

So what I am describing as to the behaior of Gimp is the way it's supposed to work?

J T

It has been a long time since I used GIMP with a raw plugin, but yes it sounds about right.  There is no "reading" the raw file, you need to have a specialized software doing an initial conversion and GIMP doesn't know how to do it.  There generally is no saving to a raw file, but the GIMP xcf format isn't lossy either.

I use rawtherapee to first convert the cr2 to a tiff (no losses), then go GIMP.  Rawtherapee has a very good default profile and generally does a better job than the in-camera jpeg making even if you don't mess with the parameters.  Rawtherapee has batch processing, so you can just convert the whole directory with the same profile.

---

### Post by J Tinsby on 2014-07-01
Thanks slonk,

I will look into Rawtherapee and see how it goes.

Wish there was a way to dock the toolbox and brush windows of Gimp instead of having them floating beside the edit window.

Regards,

J T

---

### Post by oldrocker99 on 2014-07-01
Since 2.8, GIMP has had a single-window mode, under the Windows menu.

---

### Post by J Tinsby on 2014-07-01
> **oldrocker99 said:**
> Since 2.8, GIMP has had a single-window mode, under the Windows menu.

Beautiful! Dunno how I missed it but thanks! :D

J T

---


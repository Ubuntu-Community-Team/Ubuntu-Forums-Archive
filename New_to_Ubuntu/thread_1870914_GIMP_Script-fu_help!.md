---
title: "GIMP Script-fu help!"
date: 2011-10-28
forum: New to Ubuntu
---

### Post by Markjeffries86 on 2011-10-28
Hi All,
 
I am an absolute novice when it comes to this stuff, all I know about linux is that it isn't windows, and that it has a penguin as it's logo.
 
However, as part of my job I have had something dumped on my desk that I know nothing about... Script-fu for GIMP.
 
Basically we have a script for GIMP that crops a photo to passport size etc, our customers want to have a 2nd script that does the same, but different dimensions, for another kind of badge.
 
However, when I try to duplicate the script, change the pixel dimensions and re-import it, GIMP only shows one of the scrips.
 
I think the issue is down to the script-fu register portion, it doesn't like having two scripts registered to "script-fu-image-scale" however, I can't find a way of changing this on one of the scripts without it being incorrect syntax.
 
Here is the menu register portion of the script:
 
**(script-fu-register "script-fu-image-scale"**
**_"<Image>/Script-Fu/Crop"**
**"Scales an image (and eventualy crop it before scaling it if necessary) to the given size keeping in mind the aspect ratio.\**
**Works on the selection (if any) or on the whole image.\n \**
**Ratio: choose aspect ratio\n \**
**Bigger/Smaller side limits: maximal size of sides, one of them might be recalculated to keep the Ratio (if not set to Specified by sides)\**
**e.g. Ratio=7:4, Sides=800x600 => smaller side will change to 457\n \**
**Cropping area alignment: the image might be eventually cropped to the meet the Ratio, so the cropping area can be aligned to hold the important parts of the picture\n \**
**Work on copy: selfexplaining\n \**
**Enable UNDO...: when working on the original picture it's sometime usefull to keep the backdoor open :-)"**
**"08/20/2003 - v.0.2.0"**
**"RGB GRAY RGBA GRAYA"**
**SF-IMAGE "Image" 0**
**SF-DRAWABLE "Drawable" 0)**
**; SF-VALUE _"Bigger side limit\n0 = bigger side of the original" "354"**
**; SF-VALUE _"Smaller side limit\n0 = smaller side of the original" "274"**
**; SF-ADJUSTMENT _"Cropping area alignment\nLeft 0 - 100 Right" '(50 0 100 0 10 0 0)**
**; SF-ADJUSTMENT _"Cropping area alignment\nTop 0 - 100 Bottom" '(50 0 100 0 10 0 0))**
 
 
on the other script I have tried changing the <image>Script-Fu/ part to Crop2 but it doesn't work
 
any ideas guys? is this just a limitation of Script-Fu? :confused::confused::confused:
 
Thanks in advance guys and gals.
 
Mark

---

### Post by gsmanners on 2011-10-28
I'm thinking this might be the way to go:

[http://docs.gimp.org/2.6/en/gimp-using-script-fu-tutorial.html](http://docs.gimp.org/2.6/en/gimp-using-script-fu-tutorial.html)

---

### Post by Markjeffries86 on 2011-10-28
> **gsmanners said:**
> I'm thinking this might be the way to go:
 
[http://docs.gimp.org/2.6/en/gimp-using-script-fu-tutorial.html](http://docs.gimp.org/2.6/en/gimp-using-script-fu-tutorial.html)
 
 
I looked through that but it didn't make much sense to me, but it doesn't matter now as I fixed it.
 
I had been focusing so hard on changing the script-fu register call portion of the script that I had completely neglected the portion of the script that actually defines the procedure I'm calling.
 
So all I had to do in the end was change the defined procedure to something like crop1 then change it again further down in the script in the script-fu procedure call.
 
Hope this helps someone lol.
 
Mark

---

### Post by gsmanners on 2011-10-28
Okay. Well, good job I guess. :D

And welcome to the forums.

---

### Post by ofnuts on 2011-10-28
> **Markjeffries86 said:**
> Hi All,
 
I am an absolute novice when it comes to this stuff, all I know about linux is that it isn't windows, and that it has a penguin as it's logo.
 
However, as part of my job I have had something dumped on my desk that I know nothing about... Script-fu for GIMP.
 
Basically we have a script for GIMP that crops a photo to passport size etc, our customers want to have a 2nd script that does the same, but different dimensions, for another kind of badge.
 
However, when I try to duplicate the script, change the pixel dimensions and re-import it, GIMP only shows one of the scrips.
 
I think the issue is down to the script-fu register portion, it doesn't like having two scripts registered to "script-fu-image-scale" however, I can't find a way of changing this on one of the scripts without it being incorrect syntax.
 
<cut>

on the other script I have tried changing the <image>Script-Fu/ part to Crop2 but it doesn't work
 
any ideas guys? is this just a limitation of Script-Fu? :confused::confused::confused:
 
Thanks in advance guys and gals.
 
Mark
I do my Gimp scripting in Python, but AFAIK 
```

**(script-fu-register "script-fu-image-scale"**
**_"<Image>/Script-Fu/Crop"**

```
[LIST]
[*]The first line should give a unique name to the procedure (used as an identifier in the "procedure database", aka "PDB")
[*]The second line in the location in the menus, so obviously they must be different if you want to access both of them.
[*]If you use gimp-console (in Windows) or start Gimp from a terminal (Linux) and use the --verbose parameter, you'll be told if there are registration conflicts.
[*]You can also got to Filters/Script-fu/Console/ and hit the "Browse" button to access the PDB browser and see if your script got registered properly.
[/LIST]
PS: The "Script-fu" menu entry has disappeared from recent Gimp versions, you can give the scripts a more user-friendly menu location, such as "Photos" (ie "<Image>/Photos").

---


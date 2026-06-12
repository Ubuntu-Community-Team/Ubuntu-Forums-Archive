---
title: "HOWTO: Make an MPEG Picture Slideshow with digiKam"
date: 2009-03-01
forum: Outdated Tutorials &amp; Tips
---

### Post by futileissue on 2009-03-01
This is a short howto, but since I found no solution on the forums, or on google, I decided to post the solution here.  If you only install digiKam, you will not be able to encode and render the mpeg slideshow.  If you have digiKam and are frustrated, this is why it hasn't worked.

1. Install the packages:
```
sudo apt-get install imagemagick mjpegtools music123 ffmpeg digikam
```

Or, if you prefer, install the packages in Synaptic.

2. Open digiKam, select Tools -> Create MPEG Slideshow

3. From here on out, just select the file you want to save as (output file), add the pictures you want in the slideshow using the giant 'Add' button, and include an audio track if you're so inclined.

A Side Note: If you just install digikam, it will not install mjpegtools or music123 which it needs to do the encoding.  Also, this installs the full imagenagick, as opposed to the compact libraries.

---

### Post by CiaoCiao on 2009-06-30
Which version of Digikam are you using?  I have 0.10.0 and I have followed your instructions, but I don't have this menu option available.  It was available in a previous version, but is not available since I updated digikam.  I've installed the packages mentioned from repos but no go....

---

### Post by Rodnox on 2010-02-05
Same here, under "Tools" is no such thing as an "create mpeg" option. 

I struggle as well. Want to create a video with pics and sound .... can't find out how that works with the current version.

---

### Post by CiaoCiao on 2010-02-05
I posted on the Digikam forums some time ago, this feature was removed from 0.10.  I forget the exact reason, it didn't matter anyway since I couldn't use it...

---


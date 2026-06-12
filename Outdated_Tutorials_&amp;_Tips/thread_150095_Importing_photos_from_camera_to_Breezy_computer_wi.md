---
title: "Importing photos from camera to Breezy computer with gThumb."
date: 2006-03-25
forum: Outdated Tutorials &amp; Tips
---

### Post by David Haas on 2006-03-25
I see that many folks have had trouble uploading photos to their Ubuntu computers. I had no trouble with Hoary (5.04)/Gnome, but initially did with Breezy (5.10)/Gnome. Here is what works for me in Breezy/Gnome with a Nikon Coolpix 3700 camera. 

1.One plugs the off camera via USB cable to computer.
2.Power on camera.
3.Up pops dialog box stating “Import photos from camera.”
4.If I choose the “Import photos” option, I get this error message and can't import: “An error occurred in the io-library (Bad Parameters): could not find USB device (vendor ox4b0, product ox11d). Make sure this device is connected to the computer.”
5.So, one should choose “Cancel”. Of course, this is counter-intuitive for one with photos in the camera. 
6.When the dialog box closes after clicking on “Cancel”, open gThumb Image Viewer (Applications > Graphics > gThumb Image Viewer).
7.In gThumb, select “file” > “import photos”.
8.Select your camera by clicking on the camera icon, scrolling down the long list of cameras, and highlighting your model. The icon then changes to your model name. And the program distinguishes between PTP and mass storage formats. 
9.Upon this selection, thumbnails of all the photos in your camera appear on screen in gThumb.
10.Clicking on “Import” will upload all the photos to your computer (home is the default destination).   Or if one highlights one or more thumbnails, only these will upload when Import is clicked.

I hope this helps some folks.
David Haas

---


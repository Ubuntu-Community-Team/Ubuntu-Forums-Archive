---
title: "Convert dvd .iso to .avi?"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by westyonfire on 2008-05-26
Hi,
I've got a dvd which my pc won't play because of conflicting region codes. Not even VLC player will play this dvd, so I copied the dvd to my hard disc assuming I could watch it then...but now I realise I need to convert it to another format to be able to watch it. How can I convert this dvd .iso file into an avi file? All the threads I've found so far explain how to do it the other way around so I'm out of luck there...any help please? If there were any easy, simple way to do this with out installing software that would be preferable...

,thanks

---

### Post by PmDematagoda on 2008-05-26
The application dvd::rip aught to help, it can be installed with:-
```
sudo apt-get install dvdrip
```

After install it can be found in Applications>Sound & Video>dvd::rip.

---

### Post by kpkeerthi on 2008-05-26
You may also try acidrip or [acetoneiso]("http://getdeb.net/app/AcetoneISO").

---

### Post by westyonfire on 2008-05-26
Ok, so i installed dvdrip but whenever I try and open the .iso with dvdrip it just closes on me. any ideas?

---

### Post by shifty_powers on 2008-05-26
use dvdrip on the original dvd ;)

---

### Post by tom56 on 2008-05-26
If it helps you can use VLC to watch .iso files as though they were a DVD.
```
vlc dvd:///path/to/the/file.iso
```

---

### Post by westyonfire on 2008-05-26
Thank you! I finally got to watch it...I'm still working out how to convert it to avi though. Do I really have to stick the dvd back in and resave it to disc? Is there no way to just convert a dvd .iso to an .avi?

---

### Post by tjwoosta on 2008-05-26
a .iso is a disk image file (copy of the DVD), not a video file like .avi

theres two things you could do 

1. burn the .iso to a blank dvd then use dvdrip to copy it again

2. mount the .iso with a virtual drive and copy the movie that way
   (here is a guide to mount .iso with ubuntu)
[http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html]("http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html")

---

### Post by tom56 on 2008-05-27
Thoggen? I'm pretty sure it can rip from an iso. I don't think it can do avi but it can do Ogg Theora which gets you more or less the same result, ie. a compressed video file.

There's also k9copy. I've used that before for shrinking DVDs (from the larger capacity discs films come on to the small capacity blank ones you buy at 25 for £10) with great results. It can compress to MPEG4 instead of a disc too, though bear in mind that that's not really the function it was written for.

---

### Post by angeldodger on 2008-08-03
You've probably already sussed this by now, but I thought I'd post what I've done just in case it helps...

Rip the DVD to an ISO file.

Mount the imaage. Create an empty folder (mine is on the desktop and called DVDISO) and mount the ISO image to this folder:

> sudo mount -t udf /media/hda5/filename.iso /home/andrew/Desktop/DVDISO -o loop

A DVD icon appears on the desktop.

Open DVD::RIP, create new project and then select Choose DVD Image Directory

The mounted image should be shown down the left hand side. Now start playing with DVD::RIP! Rip the main title first, then transcode to the format you require.

Hope this helped a little!

---

### Post by TomB19 on 2008-12-11
Thanks, angeldodger!  :)

---

### Post by bikerider42 on 2008-12-11
acidrip will load an iso itself... i always change the name of the iso to say a.iso as acidrip does not like long names os spaces...etc. just put the path in the load box and away you go!:p

---

### Post by fooey on 2010-09-08
just going to make this simple for future onlookers:

**1.)**
Type "sudo apt-get install dvdrip" into the terminal to install DVD::Rip.

**2.)**
Start DVD::Rip from the Applications > Sound & Video menu, or from the terminal by typing "dvdrip." The Preferences window should open automatically; otherwise hit Ctrl+P.

**3.)**
Set your DVD-ROM device under "Default DVD Device," then open the "Miscellaneous Options" tab. Set the "Default Container Format" to "AVI," and click "OK" to close the Preferences window.

**4.)**
Under "Data Source Selection," click "Choose DVD Image Directory," and browse to the ISO image you wish to convert. If you wish to select extra options such as resizing the video or including subtitles, explore the other tabs in this main window. When you are finished, go to the "Transcode" tab.

**5.)**
Set final transcoding options in the "Transcode" tab. Though most of the defaults should be fine, you may want to set the target file size yourself. When you are ready, hit "Transcode," and come back in a few minutes for your completed AVI file.

---

### Post by biodiesel-bri on 2011-01-09
DVD:Rip wasn't able to load an .iso file for me using fooey's method.  It gave an error: 
"Selected directory is no DVD image directory. It has no VIDEO_TS folder."

I think if you want to use DVD:Rip you have to mount the .iso first.

WinFF was able to rip an .iso to .avi for me without any trouble, though.

---

### Post by imwithid on 2011-02-03
If you extract the contents of the ISO file into a given directory, you can then select the "Choose DVD Image Directory" option. I will proceed to explain in detail another time; it is late.

---


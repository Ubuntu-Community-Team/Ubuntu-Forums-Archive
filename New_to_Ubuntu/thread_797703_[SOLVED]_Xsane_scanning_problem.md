---
title: "[SOLVED] Xsane scanning problem"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-05-17
I have a Microtek 4800 scanner which I just got working.  I now have a problem with the scanned pictures.  All pictures I scan have a yellow tint to them that I can not get rid of.  I have tried adjusting gamma, brightness, and contrast with no change.  I have included a picture to show what I am talking about. Any help in getting rid of this problem would be appreciated.

---

### Post by alienexplorers on 2008-05-18
bump

---

### Post by nicedude on 2008-05-18
Not sure but you might try one of the following from the repositories and see if you can get a handle on this. Heres a list of relevant software I saw with a quick glance through the repos.


Gnome scan utility
Flegita intend to be a simple but powerful standalone utility based
on Gnome Scan Infrastructure. It allow to select scanner, select
document sources, preview, rotate and save to various format
(including PDF). Further functionalities are planned such as mass
acquisition, multipage PDF, etc.


scanner program for KDE 
Kooka is an open source GNU/Linux scan program based on SANE and
KScan library.

Kooka helps you to handle the most important scan parameters, find the
correct image file format to save and manage your scanned images. It
offers support for different OCR modules. Libkscan, a autonomous part
of Kooka, provides a scan service for easy and consistent use to all
KDE applications.


Hardware Color Profiler
.
 LPROF is a color profiler that creates ICC compliant profiles for devices
such as cameras, scanners, and monitors. These profiles provide color
consistency across devices. They can be used in color profile-aware software
such as The Gimp and Scribus. For an example of creating a profile that can
be used with Scribus see
[http://www.atlantictechsolutions.com/scribusdocs/lcms/moncal.html](http://www.atlantictechsolutions.com/scribusdocs/lcms/moncal.html).


A Qt based X11 frontend for SANE (Scanner Access Now Easy)
QuiteInsane is a graphical frontend for SANE (Scanner Access Now Easy). It
can save an image to a file in a variety of image formats, send an image to
a printer or do OCR (Optical Character Recognition) using gocr.


featureful graphical frontend for SANE (Scanner Access Now Easy) 
xsane can be run as a stand-alone program or through the GIMP image
manipulation program.  In stand-alone mode, xsane can save an image
to a file in a variety of image formats, serve as a frontend to a
fax program, or send an image to a printer.


Hope this helps you out, My scanner is just a brick in Ubuntu :-(

---

### Post by dansan on 2008-06-05
Thanks nicedude.

After endless trouble with the Xsane Image Scanner, I tried Kooka - just click and go. Worked perfectly with my Canon MP600 PIXMA.

Daniel

---

### Post by Reggie Manzer on 2008-06-26
I'm having the same problem only my pictures turned out purple and yours turned out yellow. How did you fix it. I used kooka and it gave me the same results. I'm really disappointed.

---

### Post by Alfred_McGee on 2008-09-16
When I had a color problem in xsane, I clicked on the button on the xsane control panel that had a big, funny-looking "R" on it, resetting everything I had tinkered with to default values. Installing GOCR had thrown everything WAY off...

---

### Post by shane19174 on 2008-11-05
> tried Kooka - just click and go. Worked perfectly with my Canon MP600 PIXMA.

What driver are you using? Is this under Hardy or Intrepid?

Thanks

---

### Post by alienexplorers on 2008-11-05
I am using driver 1.1.0 under 8.10 Ibex.  It's working fine now.

---

### Post by shane19174 on 2008-11-05
> **alienexplorers said:**
> I am using driver 1.1.0 under 8.10 Ibex.

Thanks, I'll try it.
Oh, by the way, has 1.1.0 been released, or is this CVS?

Thanks again

---

### Post by alienexplorers on 2008-11-05
Cvs

---


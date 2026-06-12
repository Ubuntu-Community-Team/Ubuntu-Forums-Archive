---
title: "USB audio/MIDI driver"
date: 2010-08-17
forum: Programming Talk
---

### Post by kurotenshi on 2010-08-17
Hi everybody (hi doctor nick...)

I'm a somewhat long time Ubuntu user and I'm an almost completely windows free person. One of the few things that keeps making me have a windows installation on my laptop is music production and recording.
Among other reasons, my main USB audio and MIDI interface has a proprietary windows driver and no linux one. It's a Behringer BCA2000.

I program in Matlab for a living and have basic knowledge of C but I have now idea of how device drivers or USB work. So my question is can I (in less than say...6 months) create (or reverse engineer) a driver for this device?

If so I would like some tips on what to read in order to do this. Of course some help on the way will be needed but that would be another Thread.
If not is someone here interested in doing this?

Thank you

---

### Post by Zugzwang on 2010-08-18
There are some links to very helpful web pages in another thread: [http://ubuntuforums.org/showthread.php?t=1486025&highlight=USB](http://ubuntuforums.org/showthread.php?t=1486025&highlight=USB)

Make sure to read all of the posts before following the links.

---

### Post by kurotenshi on 2010-08-22
Hi again, thanks for the link it helped to get me into the theme so now I have some other questions.

Since this is an interface for pro audio use I'll be using it with ALSA so I'll need to write only an ALSA driver or the USB driver is also needed?

I have another USB audio interface and a MIDI controller that already work, how can I find what drivers are they using in order to use them as reference for the new driver?

---


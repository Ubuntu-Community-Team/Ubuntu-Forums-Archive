---
title: "Rhythmbox error when attempting to extract a cd in MP3 format"
date: 2012-11-04
forum: New to Ubuntu
---

### Post by mmauldin3 on 2012-11-04
I receive this error: Python (v2.7) requires to install plugins to create media files of the following type: MPEG-1 Layer 3 (MP3) encoder.

I've already installed the ubuntu restricted extras package and still receive this error message. I'm using Rhythmbox v2.97 with ubuntu 12.10. If there is any help out there I'd be grateful.

---

### Post by CaptainFuzzyFace on 2012-11-15
I'm having exactly the same issue.

All was well before I upgraded to 12.10 from 12.04 and I know that it does uninstall restricted software, but I have the restricted extras installed already, but no joy.

---

### Post by Raphicerus on 2012-11-15
> **mmauldin3 said:**
> I receive this error: Python (v2.7) requires to install plugins to create media files of the following type: MPEG-1 Layer 3 (MP3) encoder.

I've already installed the ubuntu restricted extras package and still receive this error message. I'm using Rhythmbox v2.97 with ubuntu 12.10. If there is any help out there I'd be grateful.

I had problems using rhythmbox to rip CDs to mp3, and ended up trying the commandline ripping script "abcde". It did a good job, and is configurable.
It was in the standard 12.04 Ubuntu repository.

There's a lot more detail about configuring it here:
[http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)

---

### Post by andrew.46 on 2012-11-15
> **Raphicerus said:**
> There's a lot more detail about configuring it here:
[http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)

Nice page that one :). I am waiting for Ubuntu to move to 2.5.4 before adding in eyed3 for mp3 tagging, I see this has happened with Raring Ringtail already and although this page is not specifically aimed at Ubuntu / Debian users I like to keep this section of the Linux Community (an admittedly large section) happy!

---

### Post by cwsnyder on 2012-11-15
@andrew.46, sorry to break in, but is eyed3 better than easytag for ID3 tag manipulation?

---

### Post by mc4man on 2012-11-15
> **mmauldin3 said:**
> I receive this error: Python (v2.7) requires to install plugins to create media files of the following type: MPEG-1 Layer 3 (MP3) encoder.

I've already installed the ubuntu restricted extras package and still receive this error message. I'm using Rhythmbox v2.97 with ubuntu 12.10. If there is any help out there I'd be grateful.
If you've installed ubuntu restricted extras then mp3 encoding in gtreamer would be enabled. If still seeing the message then pick a Custom quaility setting, close RB. Next time it should be gone.

RB now use presets, either the total crap Gnome default, the ubuntu-default override or a custom one
(After picking you'll see the .psr created in ~/.gstreamer-0.10/presets

For mp3 presets have the disadvantage of having no way currently to use xingmux headers so gstreamer encoded mp3's will probably have wrong track times depending on player & position of the track.
Better to use something else for ripping or rip to flac then convert with lame or whatever

---

### Post by andrew.46 on 2012-11-15
> **cwsnyder said:**
> @andrew.46, sorry to break in, but is eyed3 better than easytag for ID3 tag manipulation?

The current developers of abcde hope that moving to eyed3 for tagging mp3s will get over some problems with abcde's utf-8 tagging:

[http://code.google.com/p/abcde/source/detail?r=360](http://code.google.com/p/abcde/source/detail?r=360)

But this is from within abcde, I personally still use the gui easytag for last minute adjustments *after* abcde3 has finished.

---

### Post by quentinl on 2012-11-15
have you tried installing a different music player that can play that type of file??

---

### Post by Merlins on 2012-12-02
I had same issue of error in both Rythmbox and Banshee when importing mp3 or ogg format from CD on 12.10.  As soon as I specified a "Custom" quality the import worked.

---

### Post by mike acker on 2012-12-02
:confused: CDs don't normally use MP3 do they -- this is a "lossy" compression . CDs are supposed to use a lossless format such as .flac

---

### Post by cwsnyder on 2012-12-03
Audio CDs are actually encoded in a format called CDA, but then can be converted to loss-less formats.  Of course, any digital format is inherently lossy in that it is PCM digitally encoded and only contains (theoretically) frequencies up to half of the sampling frequency (in the case of CDs, 22kHz).

---

### Post by galegUbu on 2013-01-11
There isn't anywhere in the GUI to modify the quality setting. Should this be done in the command-line somewhere?  There is a 'Settings' button that is greyed out next to the format.

There is no ~/.abcde.conf either.

I am using 64-bit (ran an upgrade from 10.04 LTS)

TIA ...

---

### Post by mc4man on 2013-01-11
> **galegUbu said:**
> There isn't anywhere in the GUI to modify the quality setting. Should this be done in the command-line somewhere?  There is a 'Settings' button that is greyed out next to the format.

There is no ~/.abcde.conf either.

I am using 64-bit (ran an upgrade from 10.04 LTS)

TIA ...
This thread is about rhythmbox in 12.10, likely you have a 12.04 install where the use of gstreamer presets is required to move RB from the ubuntu or gst default BUT no means is available
Somewhat explained here or open new thread of your own
[http://ubuntuforums.org/showthread.php?t=1965432](http://ubuntuforums.org/showthread.php?t=1965432)

~/.abcde.conf is something you'd create to use abcde
some guidance - or search forum
[http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)

---


---
title: "SiS SI7012 sound was working fine before upgrade now not"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by brokndodge on 2012-06-26
Okay, I've already solved this but it was an odd problem.  

Before triggering the upgrade to 11.10, my sound was working fine.  Never actually had a sound issue before with Ubuntu/Xubuntu.  Speakers were still working I checked them first.  Built-in sound card was still enabled in the bios.  From there I moved onto the standard tests to see where the problem was.  I followed [this doc]("https://help.ubuntu.com/community/SoundTroubleshooting").

No luck, everything checks out like it is supposed to.  Next I started wondering if I had the right module auto loaded.  [This page told me that I did.]("http://cateee.net/lkddb/web-lkddb/SND_INTEL8X0.html") So on to a possible problem with alsa.  I found my solution [on this page]("http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0"). Right at the end of the kernel module install section.
> Now adjust your soundcard's volume levels. All mixer channels are muted by default. You must use a native mixer program to unmute appropriate channels, for example alsamixer from the alsa-utils package. Note that some usb-audio devices do not have internal mixer controls. Run:
       ```
alsamixer
```


I went thru every control in that lil program.  Turned the volume up on every control.  Then I started going thru and unmuting everything that was muted.  By the way, left and right arrows move your selection, up and down arrows select the volume level and m mutes and unmutes. As I went thru the options on or about the third page I found something called 'Line Jack Sense'.  It was unmuted (turned on). I pressed m to mute 'Line Jack Sense' and was greeted with the most glorious ear piercing noise I had ever heard. Apparently, alsa was using 'Line Jack Sense' to try to detect which jack the speakers were hooked to unsuccessfully.  Turning it off (muting it) just sent the sound to the speaker jack.

So, while I knew that you can never really tell which volume control actually runs your main sound output, it had never occurred to me that such an odd (and not listed in xfce4-mixer) device might need to be turned off (muted).  

Anyway, if nothing else works the command line version of alsamixer has a whole lot more devices to turn up, on/off and mute/unmute.  Might give it a try.

---


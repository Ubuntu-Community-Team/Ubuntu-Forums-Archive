---
title: "Compaq Presario V6000 Sound Issues"
date: 2013-01-13
forum: New to Ubuntu
---

### Post by kcoffman1102 on 2013-01-13
I upgraded from Natty Narwahl to Precise Pangolin and I am having issues with my volume.

When the computer starts up the volume is muted (I'm fine with that), however, when I unmute it, it goes to 100% volume. Which is super loud. Like "blow my speakers loud", if I turn the volume down to about 80% or less it's totally silent. Not a sound comes out no matter what percent of volume you're on. 1%-79% is really 0%. 

The other problem I have is that when I upgraded, my little sound bar that is physically on the computer above the key board which is usually lit up blue doesn't work the sound any longer.

---

### Post by rajhanschinmay on 2013-01-14
Try this solution.

Kindly backup the file
/etc/modprobe.d/alsa-base.conf
 by copying it to some other location.

Adding the line:
options snd-hda-intel model=generic

to

/etc/modprobe.d/alsa-base.conf

and rebooting fixed it.

Let us know if this worked.
Thank you.

---


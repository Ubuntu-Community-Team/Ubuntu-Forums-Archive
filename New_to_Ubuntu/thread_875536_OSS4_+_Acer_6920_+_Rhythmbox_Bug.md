---
title: "OSS4 + Acer 6920 + Rhythmbox Bug"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by CJay554 on 2008-07-30
So i finally got almost everything to work perfectly on my acer 6920

my pad works, my camera, graphics, sound, etc.

although one problem is stopping me from fully enjoying my ubuntu experience with my acer.

As i switched to OSS4 from ALSA, i noticed my touch pad for media control and my FN shortcut keys would not work (For volume control)

so i found a patch online gstreamer-ossv4.

keep in mind everything worked fine before this.

now, when i applied this patch my rhythmbox started to play really badly, im talking bad fuzzy interference with horrible bass sound. Right now im using amarok which works fine (along with other media player),seems to be a rhythmbox side bug of some sort. So.. the FN keys and my pad dont work completely with it, like the play, stop, forward, back, etc, and i tried setting the fn keys (same key stroke ID used as the pad) but they cant be set on amarok. Anyone might know a way to find out this conflict (if any) or have any idea on what may be effecting rhythmbox? i tried re-installing (complete removal) but still have the same problem..

PS -  anyone have any idea on ubuntu's support for finger scanners?

---

### Post by CJay554 on 2008-07-31
bump? =[

---

### Post by CJay554 on 2008-08-04
I can definately verify that its the gstreamer-ossv4 patch that causing the fault.

without the patch but with OSS4 installed
i run rhythmbox, and it works fine, i leave it playing.
Then i apply the patch (which replaces libgstossaudio.so with a patched version.

If i keep rhythmbox running after the patch is installed, it works fine, and the volume applet works like a charm, but if i restart it, (logically) rhythmbox reads the altered libgstossaudio.so and causes the conflict of really ugly sound...

I can i guess try and examine the source code for the patch, but with my limited knowledge at what im dealing with, im looking at a needle in a very very large haystack.

Please help! i would LOVE for this to run perfectly! Even if theres some sort of workaround that i have to do..:(

---

### Post by abelardo_jara on 2009-04-10
Hi, the solution is go to inside Rhythmbox to Preferences->Network and set buffer size to maximum value, you will not have more choppy sound afterwards :)

---


---
title: "no flash sound"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Zopiac on 2008-04-26
i cant remember if this is correct, as i am on another computer, in another house right now, but i believe that with my ubuntu i can watch flash (or whatever youtube has) but there is o sound. any suggestions? specs can be offered if necessary.

---

### Post by PeterJS on 2008-04-26
This is a known bug with Flash 9.0 r124, adobe will fix it eventually (we hope). In the mean time if you're on 32 bit you can install **libflashsupport** to make flash work with Pulse Audio. If you're on 64 bit you can install the same package, but it is not stable by any stretch of the imagination.

EDIT:

Originally libflashsupport was a dependency of flashplugin-nonfree, but because of the 64 bit stability issues it was down graded to a recommends during the beta.

---

### Post by richbl on 2008-05-07
> **PeterJS said:**
> This is a known bug with Flash 9.0 r124, adobe will fix it eventually (we hope). In the mean time if you're on 32 bit you can install **libflashsupport** to make flash work with Pulse Audio. If you're on 64 bit you can install the same package, but it is not stable by any stretch of the imagination.

EDIT:

Originally libflashsupport was a dependency of flashplugin-nonfree, but because of the 64 bit stability issues it was down graded to a recommends during the beta.

Very strange, but I was running Firefox 3.0B5 **without** libflashsupport up until this morning. Then, after getting a bunch of updates installed from Update Manager, audio support for flash in Firefox began to fail.

An install of libflashsupport (as suggested here) appears to have solved the problem. Of course, it would've been better to know what the cause of the problem was in the first place ;).

Such is life.

In any case, kudos on the fix solution.

---

### Post by miwaypet on 2008-05-07
May I also suggest that you open the terminal and type:

sudo apt-get autoremove flashplugin-nonfree; sudo apt-get install flashplugin-nonfree.

This will install the latest version. Make sure to have libflshsupport installed as has been suggested. That should clear the problem up.

---

### Post by Zopiac on 2008-06-20
it was fixed, but recently it stopped working again! i tried all of the fixes but nothing happened.

---

### Post by RomeReactor on 2008-06-20
Hi. Does Flash work--besides the sound problem (meaning, can you watch a video in YouTube without sound)? If so, try going to 'System->Preferences->Sound' and on the Devices tab, change all output to PulseAudio, and try again.

---

### Post by Zopiac on 2008-07-24
well, my sound's still down...and when i try to switch to pulseaudio it gives me an error message. any further advice?

---

### Post by richbl on 2008-07-24
> **Zopiac said:**
> well, my sound's still down...and when i try to switch to pulseaudio it gives me an error message. any further advice?

After switching over to pulseaudio, try rebooting. Turns out there isn't an easy way to (re)start pulseaudio.

Annoying, but it works for me.

---

### Post by Zopiac on 2008-07-24
nope didnt work :/ i think pusleaudio's dead on my computer

---


---
title: "[SOLVED] No Sound"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by poscomp on 2008-10-30
Just loaded Kubuntu 8.10 to my notebook with 3 problems. 
  1. I can attach to network drives in XP and Vista but will not load shared printers. It does see my ethernet printer but not shared printers.

  2, No sound. I have a HP TX2000z tablet computer with realtek sound.

Can anyone help me with these problems? Thanks in advance.

---

### Post by jbrown96 on 2008-10-30
1. I don't have a lot of support with printers, especially network printers (if it's HP, I might be able to help). Could you post some specifics: how are the printers attached, what models are they. I seem to remember that CUPS doesn't support printers attached to windows computers, but that's from a year ago, so it may be supported. have you tried the HP toolbox app under system??
2. Go to a terminal and try ```
alsamixer
``` the channel might be muted (use m) or turned down (up). Mute all the channels you don't need; there may be buzzing from unnecessary channels.

---

### Post by poscomp on 2008-10-31
Found the problem. It seems that the sound starts at 81%. I push it to 100% but no sound. If I right click on the sound icon and loan the mixer, I see that the volum is 100% but speakers are at 0%. I turned the speakers up and magically, sound happens. What a wonderful world. This works in Kubuntu and Ubuntu 8.10

---

### Post by gali98 on 2008-11-01
Wow this helped me as well... on another note, the external mics also work now. You just have to mess with the mixer...
Sound recorder and stuff like that is not picking it up though since the mics are put on the playback side instead of the record side.

anyway if you feel this is solved, could you mark it as solved (thread tools -> Mark thread as solved)
Kory

---

### Post by jweaver28 on 2008-11-01
OK. I'm a beginner here and I can't figure out how to get to the mixer, much less individual speaker volumes. No sound even on startup. I'm running an EVGA pentium4 motherboard with onboard Realtek sound and onboard NVIDIA 6100 series graphics.

When I go into System/Preferences/sounds the window's mis-sized so I can't see the bottom and click on the buttons. I can only drag the entire window down, which does me no good, or hit Alt-left click and make the window even bigger! I've been jiggering with this most of the afternoon. I saw a piece of code which when pasted into terminal mode led to a graphic which showed my sounds at 81% and 100%, despite psyke83's guess that they were muted. I've downloaded the Alsa files issued on 10/29, but my cutting and pasting others' commands for installation has led only to a variety of error messages.

Last month I readily got sounds working in Hardy on a machine I scraped together. It had a separate sound card, but that's not here now. This machine has working onboard sound, except in Ubuntu. I'm trying to get Intrepid in shape on a clean install/new hard drive, so I can install the hard drive (with my music files) on the now-Hardy machine with the nearly full hard drive (and whose location has only intermittent internet connections).

Thanks for any (very basic) help you can offer.

Jane.

---

### Post by gali98 on 2008-11-01
These sites may be of some help to you....
[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)
Kory

---


---
title: "Headphones won't work on laptop"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by Tithis on 2008-05-21
Alright this probably belongs in the hardware help section but the forums say I don't have permission to make a thread there.

Alright so I'm using the Linux Mint Elyssa beta(based off your 8.04) on my A135-S4527 Toshiba satellite laptop. My problem is that my headphone port won't work and it did in the last version. I'm presuming this is a problem with the new PulseAudio sound. Is there something I can edit to make it work with my headphones?

---

### Post by jamieh on 2008-05-21
- Try plugging something else in. Maybe your headphones are broken
- Can sound come from your built-in speakers?

---

### Post by Tithis on 2008-05-21
I tried both my headphones and the ones to my TV. I know the TV one works because its hooked up to my desktop computer. Sounds works fine with my speakers.

On the last version Linux Mint 4 Darnya sound didnt work right away. I would have to create a text file with some stuff in it and move it to modprobe.d, then after restarting it would work. However with that version I can't mute the speakers and have the headphones work, which kinda eliminates their purpose. It looks like PulseAudio would let me mute the speakers so I really want to get the headphones working.

---

### Post by seetho on 2008-05-21
Open your volume control and check to see if your headphones are active (not mute).  The volume may be set to zero as well.

---

### Post by Tithis on 2008-05-22
They are set to full volume.

---

### Post by seetho on 2008-05-22
There's another thread here with more or less the same problem you have with Toshiba notebook.  Could be Hardy-Toshiba issue.

---

### Post by Tithis on 2008-05-22
Alright I found the thread
[http://ubuntuforums.org/showthread.php?t=767930](http://ubuntuforums.org/showthread.php?t=767930)
and it worked perfectly. Thank you for pointing me over.

---


---
title: "Leptop emits high-pitched whine when on battery power"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by sparo007 on 2008-05-25
Hey, I'm running 8.04 on a HP dv6000 laptop with a centrino duo processor.  Whenever I unplug the laptop, it starts to emit a high-pitched whine whenever the computer is idle or not doing anything too processor intensive (i.e. if I start a program, the noise will go away for a few seconds, then return once the programs started).  

It's not a fan or the hard-drive, I know this because I've heard the fan before, and when I put my ear up to the laptop, it comes from the side the processor is on, not the side the hard-drive is on.  It does make the noise a little bit when it's on AC power, but not nearly as bad.  Also, it never used to make the noise when I was running Vista.

I tried messing around with the laptop-mode.conf file, turning the minfreq when running on battery power up to fastest, but that didn't do anything (I don't know what that does (an explanation of that would be nice too :)), but I read on the forum somewhere that doing that might work).

I was wondering if anyone might also have the same problem and might be able to help.  The noise is extraordinarily annoying.

Thanks

---

### Post by sayakb on 2008-05-25
Try muting the laptop's microphone. Maybe that is causing the sound.

---

### Post by sparo007 on 2008-05-25
How would I mute the microphone?  Also, if it was the microphone wouldn't it make a noise when on AC power too?

---

### Post by sayakb on 2008-05-25
I had a similar problem. Open the volume control and change the device to a capture device and mute it from there. Mute all available capture devices.

---

### Post by sparo007 on 2008-05-25
Still there :(, just tried muting everything, and no change.

---

### Post by sayakb on 2008-05-25
I had vista that time when I had that problem. I just muted it and got rid of it. Sorry, couldn't help you any furthur, I guess. :(

---

### Post by sparo007 on 2008-05-25
It's ok,thanks for trying

---

### Post by sparo007 on 2008-05-25
Anybody else have any suggestions? Anything?

---

### Post by xenocide13 on 2008-05-25
are you running a dual boot?

---

### Post by sparo007 on 2008-05-25
Yes, I am

---

### Post by xenocide13 on 2008-05-25
There is no whine when you load up in windows?

---

### Post by sparo007 on 2008-05-25
Nope

---

### Post by sparo007 on 2008-05-25
Me again, I've found this link:

[http://ubuntuforums.org/showthread.php?t=21232](http://ubuntuforums.org/showthread.php?t=21232)

and that person seems to have the same problem I did.  Now I need to now where to put the "root=/dev/sda2 ro pci=bios idle=halt acpi_sleep=s3_bios quiet splash" part. My menu.lst looks like this "kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b51d3078-d456-4d9f-ac67-0ffa3d9dd755 ro quiet splash".  Should i just replace all the stuff including and after the UUID part?  Also, the posts are two years old, so will this still apply to my case?

---

### Post by xenocide13 on 2008-05-25
Just back up your files before you try it and be sure you know how to make it roll back to them if it doesnt work thats what i would recomend

---

### Post by sparo007 on 2008-05-25
Yea, so tried what they suggested in the other post and 15 minutes and a recovery mode later and I still have that annoying sound

---

### Post by xenocide13 on 2008-05-25
=/ i dont know what to tell you
computers whine if they have a stick of ram that is not in all the way you could try the ram check on start up i dont think that is your problem though

---

### Post by sparo007 on 2008-05-25
It's ok, thanks for trying

---


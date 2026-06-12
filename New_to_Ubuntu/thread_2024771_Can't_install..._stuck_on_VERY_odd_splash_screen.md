---
title: "Can't install... stuck on VERY odd splash screen"
date: 2012-07-14
forum: New to Ubuntu
---

### Post by ricardisimo on 2012-07-14
I was having a problem with an older install of Ubuntu - I had only upgraded since probably 10.04 or so - where I would get logged off mostly randomly (but I think there was a connection with network activity... but that's beside the point). So, I figured, why not try a fresh install of 12.04, just to clean things up, maybe get rid of some weird little conflict somewhere?

I tried installing first with a LiveCD, and all would seem to be OK, but after the initial restart, the login screen would flash on screen for a moment, then give way to the old splash screen, warty-final-ubuntu, with nothing on it. At some point I figured out that the login box and login options button were still there, just not visible, but entering my password would not get me past the empty splash screen.

So, I tried installing from a different source, namely the Ubuntu 12.04 DVD (the one with the language packs and some other stuff included). Same result, only this time I messed around a bit more with the space on-screen where the login/password box normally is, trying to manipulate the GNOME 2D, Unity, blahblahblah, and whatever other options are there.

And that's when I see them - depending on whether I up-arrow or down-arrow on those options - these two words appearing as sort of weird video noise/intereference. Please see attached. What the hell am I up against here? Is this some weird sort of virus that's spread beyond my system to my hardware? I'm at a loss.

---

### Post by Shadius on 2012-07-14
> **ricardisimo said:**
> I was having a problem with an older install of Ubuntu - I had only upgraded since probably 10.04 or so - where I would get logged off mostly randomly (but I think there was a connection with network activity... but that's beside the point). So, I figured, why not try a fresh install of 12.04, just to clean things up, maybe get rid of some weird little conflict somewhere?

I tried installing first with a LiveCD, and all would seem to be OK, but after the initial restart, the login screen would flash on screen for a moment, then give way to the old splash screen, warty-final-ubuntu, with nothing on it. At some point I figured out that the login box and login options button were still there, just not visible, but entering my password would not get me past the empty splash screen.

So, I tried installing from a different source, namely the Ubuntu 12.04 DVD (the one with the language packs and some other stuff included). Same result, only this time I messed around a bit more with the space on-screen where the login/password box normally is, trying to manipulate the GNOME 2D, Unity, blahblahblah, and whatever other options are there.

And that's when I see them - depending on whether I up-arrow or down-arrow on those options - these two words appearing as sort of weird video noise/intereference. Please see attached. What the hell am I up against here? Is this some weird sort of virus that's spread beyond my system to my hardware? I'm at a loss.

I'm thinking it's a graphics card issue. You can try using the *nomodeset* option. I think this [thread]("http://ubuntuforums.org/showthread.php?t=1613132") should help you.

---

### Post by ricardisimo on 2012-07-14
... and I just realized after posting that "sword" is not some Christian hacker's calling card, but the tail end of "password", and "jln" is actually "gin", the tail end of "login". So the scary paranoia is gone, and I'm remembering vaguely having to jump through some hoops installing on this machine, so thanks for the tip!

---

### Post by Shadius on 2012-07-14
> **ricardisimo said:**
> ... and I just realized after posting that "sword" is not some Christian hacker's calling card, but the tail end of "password", and "jln" is actually "gin", the tail end of "login". So the scary paranoia is gone, and I'm remembering vaguely having to jump through some hoops installing on this machine, so thanks for the tip!

Yes, I believe you're right as I got the same impression the first time I saw it. Good thing the paranoia is gone now. :) What troubles did you experience while trying to install Ubuntu on the machine? The more details you provide, the better!

---

### Post by sheg on 2012-07-15
> **Shadius said:**
> Yes, I believe you're right as I got the same impression the first time I saw it. Good thing the paranoia is gone now. :) What troubles did you experience while trying to install Ubuntu on the machine? The more details you provide, the better!

thanks.

[FONT=Arial][SIZE=2][EMAIL="Stew21451@aol.com"]Stew21451@aol.com[/EMAIL]
stew21451 at aol dot com
stew21451 @ aol . com
[/SIZE][/FONT]

---

### Post by ricardisimo on 2012-07-15
So, nomodeset did not immediately solve the problem, but at least it got me to a barely usable session. I could barely make out what was on screen, but fumbling around I managed to install the nvidia driver, and that did the trick. Thank you shadius!

As it turns out, I'm still having a problem with my system randomly logging me out, so I've solved nothing, but hopefully one day...

---

### Post by Shadius on 2012-07-15
> **ricardisimo said:**
> So, nomodeset did not immediately solve the problem, but at least it got me to a barely usable session. I could barely make out what was on screen, but fumbling around I managed to install the nvidia driver, and that did the trick. Thank you shadius!

As it turns out, I'm still having a problem with my system randomly logging me out, so I've solved nothing, but hopefully one day...

You're welcome! Seems like you had the wrong NVIDIA driver installed then. Glad you were able to fix it. As for the randomly logging out part, I have no idea. Maybe you should make another thread for that issue. 

Could you tell me the steps you used in installing the NVIDIA driver? I need to install the proper NVDIA drivers on my system as I have the buggy version and I don't know how to proceed.

---

### Post by ricardisimo on 2012-07-15
> **Shadius said:**
> You're welcome! Seems like you had the wrong NVIDIA driver installed then. Glad you were able to fix it. As for the randomly logging out part, I have no idea. Maybe you should make another thread for that issue. 

Could you tell me the steps you used in installing the NVIDIA driver? I need to install the proper NVDIA drivers on my system as I have the buggy version and I don't know how to proceed.

I fumbled around on screen until I found System Settings >> Additional Drivers and installed whatever proprietary driver was available. As it turns out it was the recommended current version, so all is well. It was not easy because, even though I had an actual session, it was still screwed up and highly pixelated.

---

### Post by Shadius on 2012-07-15
> **ricardisimo said:**
> I fumbled around on screen until I found System Settings >> Additional Drivers and installed whatever proprietary driver was available. As it turns out it was the recommended current version, so all is well. It was not easy because, even though I had an actual session, it was still screwed up and highly pixelated.

Oh okay. Is it working correctly now that you have the correct driver, no pixelation and such?

---

### Post by ricardisimo on 2012-07-15
> **Shadius said:**
> Oh okay. Is it working correctly now that you have the correct driver, no pixelation and such?

Yes. But like I said, my other problem still appears to be there, the shutting down part.

---

### Post by Shadius on 2012-07-15
> **ricardisimo said:**
> Yes. But like I said, my other problem still appears to be there, the shutting down part.

It seems to be a [bug]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/980519")

---

### Post by ricardisimo on 2012-10-26
I'm going to try a fresh install of 12.10. Is it highly probable I'm looking at the same problem and solution this time around?

---

### Post by squakie on 2012-10-26
Hard to say - but I'd make sure to do a completely clean install.  I usually delete the existing Ubuntu partitions, then create new ones but in reverse order (swap then /).  You'll still need to install the nvidia driver.

---

### Post by Bashing-om on 2012-10-26
@ Shadius -> graphics troubleshooting:

Have a long read at this sticky in : Threads in Forum : Installation & Upgrades.

[INDENT]hth <== BDQ

[/INDENT]

---


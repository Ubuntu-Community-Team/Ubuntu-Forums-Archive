---
title: "[SOLVED] Wine audio issues"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by Tom11235 on 2008-12-02
Hi,

When I first installed wine (version 1.1.9), everything was fine except for the audio. When I entered winecfg, I was able to reach the audio tab, and had ALSA, JACK, and OSS present. However, whenever I clicked 'test sound', a sound would play for only a few seconds, and then the entire window would freeze up. Within games, audio was distorted due to cracking. Therefore, I installed wine version 1.0.1 instead. Within games, the window no longer fits my screen (the resolution and screen placement is off), and there is absolutely no sound. In winecfg there is an audio tab; however, when I click it, it says that the ALSA drivers are not found. JACK and OSS are available, but neither produce sound when the sound is tested. I receive an error stating 'Audio test failed!' It does not crash or freeze however. I would appreciate any help in resolving this matter. I am not sure whether it is my ALSA drivers, my sound card's drivers, my wine installation, or something else. 

Thanks ahead of time.



P.S. By the way, how do I officially thank people. I've received much help from the forums, and have thanked others through posts, but have not tried to 'make it official'. The 'Thanks: 0' below my name makes me seem somewhat ungrateful. 
Thanks again.

---

### Post by PocketDog on 2008-12-02
Apologies for not being able to help with your main issue, but the thanks button is the gold medal on the right, next to the quote button.

---

### Post by jimreynold2nd on 2008-12-02
Uh.... have you tried switching to PulseAudio instead of ALSA in the Winecfg audio tab? Or if you're in Pulse, try to switch to ALSA. Or if both doesn't work, try to use OSS.

Umm... and remember to click apply and close winecfg before trying test sound again.

---

### Post by jimreynold2nd on 2008-12-02
Uh.... have you tried switching to PulseAudio instead of ALSA in the Winecfg audio tab? Or if you're in Pulse, try to switch to ALSA. Or if both doesn't work, try to use OSS.

Umm... and remember to click apply and close winecfg before trying test sound again.

---

### Post by Tom11235 on 2008-12-02
Thanks, it was a simple/foolish mistake. I always tested the sound immediately after applying changes. I was not aware that I had to exit and reenter winecfg after making changes. Thanks again.

---


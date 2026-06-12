---
title: "Audio Ports SoundCard and Feedback in some ports"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by jeepin on 2008-07-13
Hi all, 
 I have an Ensoniq AudioPCI (according to "aplay"
  I have my headphones plugged into 1 port, and my speakers plugged into another. In WIN it works fine, I can have both running, however in ubuntu, one port the audio is distorted, distant, and even sounds like feedback. (The one I use for speakers, but still have the issue regardless if headphones are plugged in or not).
  I also have an On board audio on the board which I never use and I believe is even disabled in bios, i'll check. I never used the onboard one.
  Any ideas? Thanks in advanced guys!

---

### Post by jbrown96 on 2008-07-14
Feedback can be caused by other channels. You should disable all the channels that are not necessary, especially input channels (provided you're not using them). In a terminal, ```
alsamixer
``` use the arrow keys to move between channels, up/down to adjust volume, and M to mute channels. Try muting everything that you can and still have output on the channels you need (speaker and headphone from your post).

---


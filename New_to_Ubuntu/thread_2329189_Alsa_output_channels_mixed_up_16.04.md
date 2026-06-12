---
title: "Alsa output channels mixed up 16.04"
date: 2016-06-28
forum: New to Ubuntu
---

### Post by seniormateo on 2016-06-28
Here's the problem:

When i want to play audio, alsamixer thinks that my speaker is my headset, and that my headset is my speaker.
Pulse audio works fine, telling me my output is the built in speaker and that my other option is "headphones (unplugged)"
Alsa still works switching between the plug and the speaker

I've tried to band-aid the problem by telling alsa to just keep my volume on the headphones (which comes out of my speaker) to max, then tried to "alsaconf store" it. problem is, the volume setting im changing wont stay stored. auto mute and other settings stay when i reboot but the volume reverts back to 0 for headphones and 100 again for the internal speaker channels. 

My question here is, how to i swap these channels in alsa? Or even try to perma change the volume settings outside of alsamixer?

ps. no it isnt a driver issue, ive tested with 14.04 and 15.10 and both run fine. Ive already tried to update them as well to see if that was the issue, so this is purely alsa wiggin out.

---


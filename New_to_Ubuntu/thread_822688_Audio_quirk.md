---
title: "Audio quirk"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by arijarot on 2008-06-08
Has anyone noticed -and solved- a sound quirk that I've noticed: when one program is using audio another can't until the other program is closed?

---

### Post by markbuntu on 2008-06-08
This is a common problem and has a lot to do with having your Sound preference set to automatic. When you do this, applications that use pulseaudio or oss or alsa will fight over sound card control and the first one there will shut out the others.

The solution is to have all your apps go through one sound server that controls the sound card and slave the rest to that with plugins and default settings. 

I have had my success by setting everything to alsa. Others have had similar success with pulseaudio. In any case you need to have the libasound2-plugins and the libesd-alsa0 Enlightened Sound Demon installed for multiple sound streaming.

There is a good tutorial about this in the Multimedia and Video forum and another in the tutorial and tips forum.

In any case, you may have problems with flash taking over audio playback.
 
good luck and get bakc to us if you still have problems.

---

### Post by arijarot on 2008-06-08
> **markbuntu said:**
> This is a common problem and has a lot to do with having your Sound preference set to automatic. When you do this, applications that use pulseaudio or oss or alsa will fight over sound card control and the first one there will shut out the others.

The solution is to have all your apps go through one sound server that controls the sound card and slave the rest to that with plugins and default settings. 

I have had my success by setting everything to alsa. Others have had similar success with pulseaudio. In any case you need to have the libasound2-plugins and the libesd-alsa0 Enlightened Sound Demon installed for multiple sound streaming.

There is a good tutorial about this in the Multimedia and Video forum and another in the tutorial and tips forum.

In any case, you may have problems with flash taking over audio playback.
 
good luck and get bakc to us if you still have problems.

Thank you. I installed the libesd-alsa0 as I already had the other. No change... could you specify a link to the pages to which you were referring, please?

---


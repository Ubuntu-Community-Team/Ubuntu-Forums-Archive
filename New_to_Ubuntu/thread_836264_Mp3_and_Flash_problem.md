---
title: "Mp3 and Flash problem"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by hoverX on 2008-06-21
Hello,

I seem to be having a strange problem with audio playback.  I'm running 8.04 and it has been fully patched.  When i start up my machine and play a flash video the audio works fine.  When i try to play an audio file after that the file will not play in either totem or rhythmbox.

When i do the opposite first, play audio with rhythmbox or totem, i cannot get audio from any flash videos.

---

### Post by Nepherte on 2008-06-21
This is a problem related to pulseaudio. It blocks the second access request to your sound card. You should be able to fix this by doing part A of the following guide: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) It is up to you if you do the rest, but they shouldn't be required to fix the problem.

To be sure that it is the specific problem, I recommend you do something else first. Run the following commands simultaneously, each command in a separate terminal:
```
gst-launch-0.10 audiotestsrc ! pulsesink
gst-launch-0.10 audiotestsrc ! alsasink
```

If you only get sound from one of them, you have the problem, which you can fix by following the earlier mentioned guide.

---

### Post by hoverX on 2008-06-21
Thanks!  That worked.  I had to do parts A and B to get the flash audio working.

---


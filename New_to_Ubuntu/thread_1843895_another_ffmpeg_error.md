---
title: "another ffmpeg error"
date: 2011-09-14
forum: New to Ubuntu
---

### Post by Old-un on 2011-09-14
Ok i have installed and updated ffmpeg but everytime i run: mytube-dl -t --audio-format=mp3 --extract-audio "url" the download completes but i keep getting the following error message:-
Warning: error running ffmpeg?

---

### Post by FakeOutdoorsman on 2011-09-14
I think I know what program you're referring to (avoiding some overzealousness, eh?).

You probably need to enable MP3 encoding support in ffmpeg. It's easy to enable because you just need to install one package to do that. See *option B* in:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---


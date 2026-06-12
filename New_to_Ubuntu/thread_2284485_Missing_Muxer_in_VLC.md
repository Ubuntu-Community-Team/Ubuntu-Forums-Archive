---
title: "Missing Muxer in VLC"
date: 2015-06-29
forum: New to Ubuntu
---

### Post by tristan16 on 2015-06-29
I use VLC for (among other things) converting recordings into smaller .mp4 files. It worked on 14.04, but I just now noticed that it has a problem in 15.04. For every format container except .ogg, it says "This muxer is missing, using this profile will fail." I can convert to .mp4, but there's no audio. Interestingly enough, OpenShot video editor is still able to create .mp4 files.

How would I go about finding this "missing muxer?" So far, all I've been able to find are various threads saying an older or newer version solved the problem for some people, and for other people it works even though the message appears.

---

### Post by tristan16 on 2015-06-29
I installed Ubuntu Restricted Extras, but it didn't help any. According to VLC's codec information, the converted file only contains a video stream, so there isn't any audio stream whatsoever. When running VLC in a terminal, the mux_mp4 says "unsupported format mp3 in mp4."

---

### Post by mc4man on 2015-06-29
In my 15.04 vlc there is no such message, in 14.04 i'm using vlc-3.0-dev & there is that message though I take it to mean whatever has an x, not the profile itself (usually chapters has the red x.
As far as the profile you mentioned, don't know why anyone named it "Video - H.264 + MP3 (MP4)"  The default audio for that profile is actually mp2 (MPEG-1 Audio Layer II ), listed as MPEG Audio in vlc, you can't use mp3 in .mp4 & it shouldn't even be an available  option. (- Default should be AAC
So with either vlc using mp2 or aac works, missing muxer message is not a factor.

---

### Post by tristan16 on 2015-06-29
> **mc4man said:**
> In my 15.04 vlc there is no such message, in 14.04 i'm using vlc-3.0-dev & there is that message though I take it to mean whatever has an x, not the profile itself (usually chapters has the red x.
As far as the profile you mentioned, don't know why anyone named it "Video - H.264 + MP3 (MP4)"  The default audio for that profile is actually mp2 (MPEG-1 Audio Layer II ), listed as MPEG Audio in vlc, you can't use mp3 in .mp4 & it shouldn't even be an available  option. (- Default should be AAC
So with either vlc using mp2 or aac works, missing muxer message is not a factor.

Hm, sounds like somebody really messed up when naming that profile. After switching the audio codec from MP3 to MPEG Audio, everything works fine. I'm actually a little confused why it works now, because I thought I had tried other formats earlier.

What you were talking about with the X next to features (like chapters), I think those are some sort of codec features. Anyway, the missing muxer message appears underneath those. Everything looks normal in the terminal and logs, so I have no idea why it still thinks the muxer is missing.

Once again, I missed the obvious. I thought purging and re-installing VLC would have reset the default profiles, unless MP3 was somehow the default option. Thanks for the help. :)

---

### Post by mc4man on 2015-06-29
If you get the occasional issue with vlc rather than re-installing you just  should remove ~/.config/vlc 
The 2 files inside will be redone at vlc install defaults next time vlc is run & can be at the root of many little problems, ect.

---


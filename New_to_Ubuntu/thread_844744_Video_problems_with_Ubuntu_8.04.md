---
title: "Video problems with Ubuntu 8.04"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by bprof on 2008-06-29
I'm trying to play avi, wmv videos, so far I'm only able to hear the voice but see no images.

I've tried VLC,mplayer,kmplayer 

No luck. Any help?

---

### Post by neurostu on 2008-06-29
have you installed the restricted codecs?

Try:
```

sudo apt-get install ubuntu-restricted-extras

```
that should make it so you can read the video files.

---

### Post by bprof on 2008-06-29
I just did, but still same. Play voice but does not display images.

---

### Post by kuja on 2008-06-29
Ubuntu-restricted-extras will have no effect on VLC or Mplayer or Kmplayer either for that matter. I recommend using the [medibuntu](https://help.ubuntu.com/community/Medibuntu) repository to get the "w32codecs" (or "w64codecs") package. For more detailed info look here: [RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by bprof on 2008-06-29
I just did kuja, no luck with that too.

---

### Post by kuja on 2008-06-29
Medibuntu also has packages of several media players, including mplayer, with extra support for "restricted" things compiled in. Mayhap that would be able to play it? If not, then I'm not sure what the problem is. Wait, come to think of it, in my experience Xine has handled WMV playback better than MPlayer. Try installing xine-ui and libxine-ffmpeg (if you don't already have them), and from there on you can use kmplayer with the xine engine selected (or xine-ui or kaffeine)

---

### Post by bprof on 2008-06-29
I've installed xine-ui but couldn't find libxine-ffmpeg.

When I tried to play the video with xine I got this error message:

video.wmv uses an unsupported codec:

Video Codec: Unavailable(MSS2)

---

### Post by bprof on 2008-06-29
I checked the SPM and found that I have libxine1-ffmpeg is installed, but still I cant see the images.

---

### Post by kuja on 2008-06-29
[http://nerdrage.org/?p=9](http://nerdrage.org/?p=9) maybe

---

### Post by RomeReactor on 2008-06-29
Hi bprof. Do you have Compiz enabled? If so, turn the effects off and see if the video displays correctly.

---

### Post by bprof on 2008-06-29
Unfortunatelly that didn't work.

This is the error I getting no matter what I did

Cannotfind codec matching selected -vo and video format 0x3253534d

---

### Post by bprof on 2008-06-29
I do have compiz enabled. I disabled it usin system->preferences->apperance->visual effects and then selected none.

But still cant get the video to play. I really don't know why its not working, I though it will be easy, I guess I was so wrong.

---

### Post by RomeReactor on 2008-06-29
In Mplayer, right-click on it and select 'Preferences', go to the 'Video' tab make sure **xv   X11/Xv** is highlighted.

---

### Post by bprof on 2008-06-29
I did and it is highlihted.

---

### Post by RomeReactor on 2008-06-29
The last post on [this thread]("http://ubuntuforums.org/showthread.php?t=356656") suggests changing the file extension from WMV to ASF.

---

### Post by bprof on 2008-06-29
I just changed it to asf but same result (No images)

---

### Post by RomeReactor on 2008-06-29
Are you using Ubuntu 64-bit? There's a possibility that the [w64codecs package differs enough from the w32]("http://ubuntuforums.org/showthread.php?t=768538") that it's unable to play the video. I'm running Ubuntu 64-bit, so I can't corroborate whether it does work in 32-bit.

In the meantime, a workaround is to use the windows version of mplayer:
```
wget ftp://ftp4.mplayerhq.hu/MPlayer/releases/win32/MPlayer-1.0rc2-gui.zip
```
```
unzip -x MPlayer-1.0rc2-gui.zip
```
You'll then have a folder named **MPlayer-1.0rc2-gui**; go inside that folder and double-click on the **gmplayer** executable. You'll need to have Wine installed.

---

### Post by bprof on 2008-06-29
I'm using 64bit. I've downloaded and installed w64 codecs but nothing changed.

---

### Post by kuja on 2008-06-29
This is another possibility, though it's currently unmaintained and I'ver never figured out how he managed to do it, or I'd have half the mind to do it myself. 

[http://ubuntuforums.org/showthread.php?t=188974](http://ubuntuforums.org/showthread.php?t=188974)

Try it, it may still work with the edgy package, hard to tell. If you want to try, do try, and the install fails, give me the full context of the error message and I'll do what I can to cook up a fix for you.

---

### Post by RomeReactor on 2008-06-29
> **bprof said:**
> I'm using 64bit. I've downloaded and installed w64 codecs but nothing changed.
If someone posting on this thread is running Ubuntu 32-bit and is able to play a MSS2 WMV video, then that would be a good indicator of the problem.

Just as a note: The windows version of Mplayer (through Wine) was able to play [this MSS2 video]("http://sw.nokia.com/id/105027dd-501a-4709-8c48-0da1d57bb0c0/VOIP_Webinar_27Nov06.wmv") ([referenced here]("http://ubuntuforums.org/archive/index.php/t-63502.html")) without problems.

---


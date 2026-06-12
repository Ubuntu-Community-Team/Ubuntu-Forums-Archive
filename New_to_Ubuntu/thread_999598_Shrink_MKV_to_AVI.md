---
title: "Shrink MKV to AVI"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by abhiroopb on 2008-12-02
I have a few VERY large MKV files (H.264, Blu-Ray Rip) and I would like to convert them to a lower quality AVI (Xvid) file. What is the best method to do this?

---

### Post by prshah on 2008-12-02
> **abhiroopb said:**
> I have a few VERY large MKV files (H.264, Blu-Ray Rip) and I would like to convert them to a lower quality AVI (Xvid) file. What is the best method to do this?

I always use Avidemux (it's in the repos) to shrink down files. They have a "template" based method which will allow you to select a suitable size-based format (Eg, SVCD, MPG4, etc). I don't know if it will handle MKV (container) files though.

---

### Post by expatCM on 2008-12-02
There is a program in the repositories called mkvmerge.  It does a number of things, one will allow you to select an mkv file and then convert it to an avi.  Very fast .....  just change the extension in the output window...

---

### Post by aeiah on 2008-12-02
this is kinda redundant but what the hell.

i think what expatCM is describing isnt actually reencoding, but rather just remuxing. mkv and avi are really just containers. the video and audio inside them can be quite different from eachother or could be identical (although mkv can have fancy things that avi cant normally have). anyway, what you want is reencoding, not remuxing, since you want to lower the quality. if you wanted to keep the subtitles and multiple audio tracks or whatever else your mkv has you could strip out the video, encode it at a lower bitrate / resolution and remux it back into an mkv container with all the other files intact (or indeed do the same with the audio track(s)). 

like i said this is kinda redundant since something like avidemux will do what you want but if you know the distinction between container, codec etc it may help in the future if you want to do more with your mkv files.

---


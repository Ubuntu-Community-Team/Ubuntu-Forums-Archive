---
title: "shell command for video resolution"
date: 2006-10-23
forum: Programming Talk
---

### Post by I_Failed_C++ on 2006-10-23
Hi all.  I need a shell command to output the resolution of a video file for use in a script but I'm at a loss.  Can anyone help me.
Thanks

---

### Post by duff on 2006-10-23
```
# xdpyinfo | grep '^  dimension' | awk '{print $2}'
```

---

### Post by I_Failed_C++ on 2006-10-23
I'm a relative noob but it look like this code will query a display server?  What I'm wanting to do is query a file.
Thanks.

---

### Post by toojays on 2006-10-24
I don't know of a tool which does this, but I know some programs use mplayer to create thumbnails of video files. If you could use mplayer to output a single frame at the resolution of the video, you could then use a tool like identify (from ImageMagick) to get the dimensions of the frame.

If all your videos are in a single format, you may be able to use another tool, but if you have to deal with videos in arbitrary formats, you will need to use a movie player somewhere.

---


---
title: "Resize qt window on widget resize"
date: 2010-08-05
forum: Programming Talk
---

### Post by simon303 on 2010-08-05
Hi,

I'm using the ogl widget to display video streams.

There are multilple streams being shown along a strip. When the user double clicks on a stream it becomes full size above the strip (replacing the one there if there is one). Double clicking on a full size stream puts it back in the strip.

The window resizes if it needs more space to do the above, but if it takes up less space in the window the window remains large with blank space.

Does anyone know how to auto resize the window so it gets smaller when needed?

Simon

---

### Post by simon303 on 2010-08-05
The picture shows what happens, showing
1) the original strip
2) video 2 full size
3) video 3 full size
4) the original strip

As can be seen the window resizes when it needs to get bigger (2, 3), but not when it needs to get smaller (4).
It also doesn't get smaller when the new full screen video is smaller than the previous video (i.e. when i go back to displaying video 2 from video 3)

It must also be noted each video is in a layout so i can display stats (eg resolution) under the video.

---

### Post by simon303 on 2010-08-10
bump

---

### Post by simon303 on 2010-08-19
bump

Is any more information needed? Or does no one really know what to do about it?

Simon

---


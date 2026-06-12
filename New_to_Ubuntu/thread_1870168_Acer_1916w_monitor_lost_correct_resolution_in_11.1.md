---
title: "Acer 1916w monitor lost correct resolution in 11.10"
date: 2011-10-26
forum: New to Ubuntu
---

### Post by egkeat on 2011-10-26
I don't know how this one happened, but I've got 1024 x 768 (4:3) showing on an "unknown" monitor. The same happens when logging onto Windows. I cannot get back the 1440 x 900 widescreen that I had just yesterday. The board's not fancy...it's an Intel integrated graphics i833? I think. I had one successful restart when going to Windows and downloading drivers from Intel and Acer and after getting in to set the Acer driver, it wasn't digitally signed. I didn't know whether or not that would be safe, so I didn't proceed but went back to Ubuntu and found Acer 19" Widescreen in the setting, but then I had to go foul things up again when hit "apply."

Any help would be appreciated.

---

### Post by egkeat on 2011-10-28
Well, today when coming out of the screensaver, this happened.:(


none of the selected modes were compatible with the possible modes:
Trying modes for CRTC 63
CRTC 63: trying mode 1024x768@60Hz with output at 1440x900@60Hz (pass 0)
CRTC 63: trying mode 800x600@60Hz with output at 1440x900@60Hz (pass 0)
CRTC 63: trying mode 800x600@56Hz with output at 1440x900@60Hz (pass 0)
CRTC 63: trying mode 848x480@60Hz with output at 1440x900@60Hz (pass 0)
CRTC 63: trying mode 640x480@60Hz with output at 1440x900@60Hz (pass 0)
CRTC 63: trying mode 1024x768@60Hz with output at 1440x900@60Hz (pass 1)
CRTC 63: trying mode 800x600@60Hz with output at 1440x900@60Hz (pass 1)
CRTC 63: trying mode 800x600@56Hz with output at 1440x900@60Hz (pass 1)
CRTC 63: trying mode 848x480@60Hz with output at 1440x900@60Hz (pass 1)
CRTC 63: trying mode 640x480@60Hz with output at 1440x900@60Hz (pass 1)
Trying modes for CRTC 64
CRTC 64: trying mode 1024x768@60Hz with output at 1440x900@60Hz (pass 0)
CRTC 64: trying mode 800x600@60Hz with output at 1440x900@60Hz (pass 0)
CRTC 64: trying mode 800x600@56Hz with output at 1440x900@60Hz (pass 0)
CRTC 64: trying mode 848x480@60Hz with output at 1440x900@60Hz (pass 0)
CRTC 64: trying mode 640x480@60Hz with output at 1440x900@60Hz (pass 0)
CRTC 64: trying mode 1024x768@60Hz with output at 1440x900@60Hz (pass 1)
CRTC 64: trying mode 800x600@60Hz with output at 1440x900@60Hz (pass 1)
CRTC 64: trying mode 800x600@56Hz with output at 1440x900@60Hz (pass 1)
CRTC 64: trying mode 848x480@60Hz with output at 1440x900@60Hz (pass 1)
CRTC 64: trying mode 640x480@60Hz with output at 1440x900@60Hz (pass 1)

---

### Post by khelben1979 on 2011-10-29
Hmm.. try ```
lspci
``` and share the output here. Because it's the video driver which is responsible for your screen resolution working correctly.

Have you recently upgraded to this Ubuntu 11.10 b.t.w?

---


---
title: "Still Xlib troubles"
date: 2008-08-24
forum: Programming Talk
---

### Post by techmarks on 2008-08-24
I finally was able to create a simple window with X-lib and start it from the command line, I just needed to specify the path to the executable program in .xinitrc, and start it up that way.

Well then that much works now, but when the program shuts down
it exits the X server  but not to the command line,
it just stays stuck there (all the stuff that was at the commnd line before is there, but not a new prompt, sometimes if I do CRTL ALT Backspace that will get it back)


At the end of displaying the window I shutdown X like this

XCloseDisplay(display);
exit(1);

where display is the string with my display name,

IS there something else I need to do so I just get back to
a commnd line?

Thanks for any help.

---


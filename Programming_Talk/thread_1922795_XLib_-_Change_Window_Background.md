---
title: "XLib - Change Window Background"
date: 2012-02-09
forum: Programming Talk
---

### Post by yank3s on 2012-02-09
Hello community,

I'm making a small project using XLib. I set up the window with the normal XCreateSimpleWindow() command, where I specify the background color, in this case RED (0xFF0000); I also applied the XShape extension, in order to create a Rounded Rectangle shape for the window.

But after this, I've been trying to change the color of the background of the window, when the mouse button is pressed. I tried XSetWindowBackground() command, specifying a different color and nothing. I also tried with :

```
        if (e.type == ButtonPress) {
            if( e.xbutton.button == 2 ) {
                XSetWindowAttributes o;
                o.background_pixel = YELLOW;
                XChangeWindowAttributes(d, w, CWBackPixel, &o);
                printf("VIV O BENFICA\n");
            }
        }
```The string that i ask to print is actually printed, but the background collor is never changed. YELLOW is a constant defined as 0xFFFF00.

Does anyone have an idea of why the background color is not changing ?

Thank you very much.

EDIT: Ok i solved the problem. Looks like i have to unmap the window, and map it once again.

---


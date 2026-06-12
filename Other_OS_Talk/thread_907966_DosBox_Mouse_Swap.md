---
title: "DosBox: Mouse Swap"
date: 2008-09-02
forum: Other OS Talk
---

### Post by rickyrockrat on 2008-09-02
So I've pulled my hair out searching how to swap the mouse buttons in DosBox. I finally got the source for 0.72 and added buttonswap to the options file.  

Here is the patch for DosBox if anyone is interested, but Is there some other way to do this??

Cheers

```

diff -ruN dosbox-0.72/src/gui/sdlmain.cpp dosbox-0.72-buttonswap/src/gui/sdlmain.cpp
--- dosbox-0.72/src/gui/sdlmain.cpp     2007-08-26 12:03:25.000000000 -0600
+++ dosbox-0.72-buttonswap/src/gui/sdlmain.cpp  2008-09-01 23:13:36.000000000 -0600
@@ -203,6 +203,7 @@
                bool autoenable;
                bool requestlock;
                bool locked;
+               bool buttonswap;
                Bitu sensitivity;
        } mouse;
        SDL_Rect updateRects[1024];
@@ -1058,6 +1059,7 @@
 #endif
        }
        sdl.mouse.autoenable=section->Get_bool("autolock");
+       sdl.mouse.buttonswap=section->Get_bool("buttonswap");
        if (!sdl.mouse.autoenable) SDL_ShowCursor(SDL_DISABLE);
        sdl.mouse.autolock=false;
        sdl.mouse.sensitivity=section->Get_int("sensitivity");
@@ -1171,10 +1173,16 @@
                }
                switch (button->button) {
                case SDL_BUTTON_LEFT:
-                       Mouse_ButtonPressed(0);
+                       if(sdl.mouse.buttonswap)
+                               Mouse_ButtonPressed(1);
+                       else
+                               Mouse_ButtonPressed(0);
                        break;
                case SDL_BUTTON_RIGHT:
-                       Mouse_ButtonPressed(1);
+                       if(sdl.mouse.buttonswap)
+                               Mouse_ButtonPressed(0);
+                       else
+                               Mouse_ButtonPressed(1);
                        break;
                case SDL_BUTTON_MIDDLE:
                        Mouse_ButtonPressed(2);
@@ -1480,6 +1488,7 @@
                        "            Second entry behind the comma is for when dosbox is not focused/minimized.\n"
                        "mapperfile -- File used to load/save the key/event mappings from.\n"
                        "usescancodes -- Avoid usage of symkeys, might not work on all operating systems.\n"
+                       "buttonswap -- Swaps left and right buttons on the mouse.\n"
                        );
                /* Init all the dosbox subsystems */
                DOSBOX_Init();


```

---


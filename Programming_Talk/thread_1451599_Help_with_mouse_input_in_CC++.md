---
title: "Help with mouse input in C/C++"
date: 2010-04-10
forum: Programming Talk
---

### Post by TehCodr on 2010-04-10
Hi, I'm developing a game in c++, and to do so, I need to capture the mouse input, but I'm having trouble writing a script for that. I need to know the coordinates of the mouse in system memory (0xXXXXXX), so I can get the mouse input. The script would look something like this:

```

#ifndef MOUSE_LEFT_CLICK
#define MOUSE_LEFT_CLICK 0xXXXXXX //System coordinates for mouse left click
#endif

#ifndef MOUSE_RIGHT_CLICK
#define MOUSE_RIGHT_CLICK 0xXXXXXX //System coordinates for mouse right click
#endif

#ifndef MOUSE_MIDDLE_CLICK
#define MOUSE_MIDDLE_CLICK 0xXXXXXX //System coordinates for mouse middle click
#endif

#ifndef MOUSE_MOVE_LEFTRIGHT
#define MOUSE_MOVE_LEFTRIGHT 0xXXXXXX //System coordinates for mouse moving left and right
#endif

#ifndef MOUSE_MOVE_UPDOWN
#define MOUSE_MOVE_UPDOWN 0xXXXXXX //System coordinates for mouse moving up and down
#endif


```

If you know where the mouse button coordinates are in the system memory, how to use them for input, or how to improve the script, It'd be really helpful.

I am NOT using Microsoft Visual C++

---

### Post by Zugzwang on 2010-04-11
What platform/toolkit are you developing for? Mouse input/output is not part of the C++ standard, so it is platform dependent how you do that, which leads to the fact that you will need to provide more data to get a usable answer.

Note that in Linux, you generally need to call functions for performing such operations. Memory access to system memory is forbidden by the design of the operating system. If you are using "text mode" in the terminal, probably the "ncurses" library might be of help. In case you are using graphics anyway, you might want to look into the SDL library.

---

### Post by TehCodr on 2010-04-11
> **Zugzwang said:**
> What platform/toolkit are you developing for? Mouse input/output is not part of the C++ standard, so it is platform dependent how you do that, which leads to the fact that you will need to provide more data to get a usable answer.

Note that in Linux, you generally need to call functions for performing such operations. Memory access to system memory is forbidden by the design of the operating system. If you are using "text mode" in the terminal, probably the "ncurses" library might be of help. In case you are using graphics anyway, you might want to look into the SDL library.

Thanks, it's graphics-based, but I don't want to use SDL as an engine, graphics, or device support, but OpenAL and OpenGL instead, and I'm developing under all Unix-based computers... Is it possible to access the mouse or other devices through GL or AL, or write something for device support without them?

---

### Post by heikaman on 2010-04-11
> **TehCodr said:**
>  Is it possible to access the mouse or other devices through GL or AL, or write something for device support without them?

No, openal is an audio api, and opengl is a graphics api and you can use glut or talk to XServer directly, but I wouldn't recommend that.

If you're writing your own engine the most difficult part, in my opinion,  is the **design** not the implementation, save sometime by not writing SDL, again, from scratch, and just use it for your windowing and input subsystems and **abstract** that behind **interfaces** until you yourself don't know what **specific** input implementation you're using ! 

This way if you ever need to port your engine you can do so easily.

---

### Post by Simian Man on 2010-04-11
> **heikaman said:**
> If you're writing your own engine the most difficult part, in my opinion,  is the **design** not the implementation, save sometime by not writing SDL, again, from scratch, and just use it for your windowing and input subsystems and **abstract** that behind **interfaces** until you yourself don't know what **specific** input implementation you're using ! 

This way if you ever need to port your engine you can do so easily.

This is absolutely the best advice you can get.

---

### Post by TehCodr on 2010-04-18
> **heikaman said:**
> No, openal is an audio api, and opengl is a graphics api and you can use glut or talk to XServer directly, but I wouldn't recommend that.

If you're writing your own engine the most difficult part, in my opinion,  is the **design** not the implementation, save sometime by not writing SDL, again, from scratch, and just use it for your windowing and input subsystems and **abstract** that behind **interfaces** until you yourself don't know what **specific** input implementation you're using ! 

This way if you ever need to port your engine you can do so easily.

Thanks for the advice :) I'll do that :D

---


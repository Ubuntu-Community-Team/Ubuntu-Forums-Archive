---
title: "KDevelop create a simple SDL program cannot link lib"
date: 2008-01-24
forum: Programming Talk
---

### Post by windxu on 2008-01-24
i using KDevelop create a simple SDL program. when i build this project, the compiler are output this tips:
/project/study/src/study.cpp:36: undefined reference to `SDL_Init'
/project/study/src/study.cpp:37: undefined reference to `SDL_GetError'
/project/study/src/study.cpp:38: undefined reference to `SDL_Quit'
/project/study/src/study.cpp:42: undefined reference to `SDL_CDNumDrives'
/project/study/src/study.cpp:44: undefined reference to `SDL_CDName'
/project/study/src/study.cpp:43: undefined reference to `SDL_CDNumDrives'
/project/study/src/study.cpp:47: undefined reference to `SDL_Quit'

i set the libraries and found two environment variables $(LIBSDL_RPATH) and $(LIBSDL_LIBS). what is correct value??

---

### Post by hod139 on 2008-02-08
You should use sdl-config to set the include and linking paths:
```

sdl-config --cflags --libs

```

---


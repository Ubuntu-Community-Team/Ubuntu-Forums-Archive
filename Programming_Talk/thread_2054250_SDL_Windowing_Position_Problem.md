---
title: "SDL Windowing Position Problem"
date: 2012-09-06
forum: Programming Talk
---

### Post by dosh on 2012-09-06
I am writing some simple code using SDL, positioning a number of windows, and came across a problem. In that if I place windows as in the code below (increasing the y position of each window)the first 5 windows seem to be in the same y position on the screen, however the y position of the windows have been increased. Is this a Unity,Gnome, Ubuntu or SDL problem? Is this the same with GTK+? Using SDL_GetWindowPosition it shows the y position has increased which is incorrect.

```

for(y=0,x=15;y<=50;y+=5,x+=100) {
  win[y/5]=SDL_CreateWindow("Test",x,y,90,40,SDL_WINDOW_SHOWN);  
  SDL_GetWindowPosition(win[y/5],&x1,&y1);
  printf("Window %d: x %d, y %d \n",[y/5],x1,y1);
}

```

---


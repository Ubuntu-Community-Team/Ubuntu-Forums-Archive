---
title: "[SOLVED] Reading keyboard in Linux?"
date: 2007-11-15
forum: Programming Talk
---

### Post by paukku92 on 2007-11-15
I'm making a simple GUI Library for OpenGL and I would like to know how do you read keypresses from keyboard in Linux? 

Windows had GetAsyncKeyPress or something like that. Is there a similiar function?

---

### Post by LaRoza on 2007-11-15
ncurses has such functions, but any functions like that will not be ansi standards, like the Windows function who mention.

[http://laroza.pbwiki.com/LinuxSpecific](http://laroza.pbwiki.com/LinuxSpecific)

---

### Post by paukku92 on 2007-11-15
Well, that was not actually something I was looking for. I need a function that can read keyboard without a terminal window. 

One possible way to solve the problem is that I could always let the library user to get the keyboard data to the library but I would not like it that way.

---

### Post by Kadrus on 2007-11-15
If you haven't installed the packages for ncurses
type in Terminal
```
 sud apt-get install ncurses-base
```

and then

```
sudo apt-get install ncurses-bin

```

---

### Post by LaRoza on 2007-11-15
Oh, I am not familiar with the Windows function, so went by description.

---

### Post by bunker on 2007-11-15
[SDL](http://www.libsdl.org/) sounds like what you need.  Also, since it is a cross platform thing there's a chance it might give some  functions that are more familiar to you than using xlib directly.  I don't program on windows so I can't be sure.

A quick example from their docs:
```

    SDL_Event event;

    SDL_WaitEvent(&event);

    switch (event.type) {
        case SDL_KEYDOWN:
            printf("The %s key was pressed!\n",
                   SDL_GetKeyName(event.key.keysym.sym));
            break;
        case SDL_QUIT:
            exit(0);
    }
}

```

---

### Post by paukku92 on 2007-11-16
Can you use SDL from the library so that it will not cause interference to the program that uses the library if it's using SDL?

But if it is really possible to just wait for keypresses with SDL it would be really easy.

---

### Post by bunker on 2007-11-16
If I understand you rightly, you're asking if a client program to YOUR library can also use SDL.  This is fine.  You will see many programs and libraries using the same libraries -- that's pretty much the idea :).

---


---
title: "what does this process really means..??"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by shredder12 on 2008-10-10
Hey my system was working quite slow..
so when i checked the processes running..using 
```
top -c
``` 
i found that these 2 processes were consuming most of the cpu..
could any body help by telling me wht do they really convey..
```
 6021 root      20   0 92036  50m  12m S   46  5.0  24:17.09 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7                        
23839 sahni     20   0 85408  52m  27m S   21  5.2   8:29.43 /usr/bin/compiz.real --ignore-desktop-hints --replace --loose-binding --replace core ccp        

```
I am a newbie..so please don't mind it it is a really straight forward question..
thankyou...

---

### Post by Orange_and_Green on 2008-10-10
Hello shredder12.

These processes are related to the graphical interface.

More specifically, X is a server process that provides interfaces for basic graphical functions (like showing windows, colouring pixels on the screen, drawing shapes, handling bitmaps, etc) while compiz is a desktop manager that provides animations, 3D desktop effects (like the "cube"), transparencies etc.

It's quite normal, I think, for these processes to have occasional peaks in resource consumption if you have lots of windows and/or graphical applications open. However, if they are always taking up that much, then maybe you could have "overdone" it with the cool desktop effects, or misconfigured something.

Hope this helps.

---

### Post by unutbu on 2008-10-10
```
 6021 root      20   0 92036  50m  12m S   46  5.0  24:17.09 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7 
``` 
This is the command which launches your X server. The X server is the underlying program which allows you to  have a graphical user interface, rather than a text terminal.
                      
```
23839 sahni     20   0 85408  52m  27m S   21  5.2   8:29.43 /usr/bin/compiz.real --ignore-desktop-hints --replace --loose-binding --replace core ccp
```
compiz.real is the OpenGL window and compositing manager. compiz is what allows you to have the rotating cube effect for example.

If you type 
```

man X
```

or ```


man compiz.real
man compiz

```
you can learn more about these processes. And in general, "man" is a pretty good tool for finding out about the processes running on your machine.

---

### Post by sam hassell on 2008-10-10
I'd add that 50meg for these processes is quite low.

---

### Post by shredder12 on 2008-10-10
Hey just wanna know..what does this 50meg really means..and how does its being low or high affects the process..??

---


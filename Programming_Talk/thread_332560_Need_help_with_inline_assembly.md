---
title: "Need help with inline assembly"
date: 2007-01-06
forum: Programming Talk
---

### Post by mavix on 2007-01-06
I need some help with inline assembly in GCC. I am trying to write my own "Operating system" and need help with my putpixel function. Before the function is called I switch into graphics mode. Heres my code(converted from Intel assembly, as best as I could): 

    __asm__ ("movb $12, %ah\n\t"
        "movw 1, %dx\n\t"
        "movw 1, %cx\n\t"
        "movb $0x07, %al\n\t"
        "movb 0, %bh\n\t"
        "int  $0x10\n\t");

(Converted from:
    mov ah, 12
    mov dx, 1
    mov cx, 1
    mov al, 0x07
    mov bh, 0
    int 0x10
)
Nothing happens when I call this function. Please help!

---

### Post by Wybiral on 2007-01-06
I'm a little rusty with my assembly graphics routines (haven't done much since I had DOS on my comp)... So, correct me if I'm wrong, but "int 0x10" doesn't work in linux.

There's a VGA example on this assembly page... [http://www.janw.dommel.be/eng.html](http://www.janw.dommel.be/eng.html)

But, once again, I may be wrong, it's just that I haven't seen that call in a long time.

BTW... If you're writing this in c/c++ and looking for an easier way to switch to a graphics mode, try libvga or sdl. SDL is a really nice graphics api that also offers some mouse/keyboard/sound functionality. And with SDL_image you can also easily load images of various formats (although SDL alone is able to load BMP's)

---


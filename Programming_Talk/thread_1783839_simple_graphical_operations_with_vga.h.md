---
title: "simple graphical operations with vga.h"
date: 2011-06-16
forum: Programming Talk
---

### Post by sensational on 2011-06-16
Hi,
Im looking for a simple way to perform graphical operations in c on ubuntu.

getpixel
drawpixel
move mouse.

I discovered vga.h and installed  "sudo apt-get install libsvga1-dev"

I then wrote a small test program

//get pix
#include <vga.h>
#include <stdio.h>
#include <stdlib.h>
main()
{
int value;
value=vga_getpixel(10,10);
printf("value=%d",value);
}


It compiled but when I ran it I got "Segmentation fault"

Can anybody advise me here.
Am I on the right track. Im looking for the easiest possible way to read from and write to the display in ubuntu.

Mark.

---

### Post by cgroza on 2011-06-16
Uhmmm, why do you use VGA? You can use openGL although I am not sure of what you are trying to do. Gdb may tell you where the segfault occurs.

---

### Post by cgroza on 2011-06-16
I checked some sample and it seems they set a video mode before doing anything.
This is a small sample:
[http://www.brackeen.com/vga/source/djgpp20/pixel.c.html](http://www.brackeen.com/vga/source/djgpp20/pixel.c.html)

---

### Post by sensational on 2011-06-16
Hi,

That code you sent sent me is for a windows/dos system.

I looked at vga.h because I want the simplest way possible to read and write pixels from the screen.

Would most people use openGL for this ?

If so how do I get started with it.

Mark.

---

### Post by Petrolea on 2011-06-17
> **sensational said:**
> Hi,
Im looking for a simple way to perform graphical operations in c on ubuntu.

getpixel
drawpixel
move mouse.

I discovered vga.h and installed  "sudo apt-get install libsvga1-dev"

I then wrote a small test program

//get pix
#include <vga.h>
#include <stdio.h>
#include <stdlib.h>
main()
{
int value;
value=vga_getpixel(10,10);
printf("value=%d",value);
}


It compiled but when I ran it I got "Segmentation fault"

Can anybody advise me here.
Am I on the right track. Im looking for the easiest possible way to read from and write to the display in ubuntu.

Mark.

Function probably returns incompatible type with int.

---

### Post by ziekfiguur on 2011-06-17
> **sensational said:**
> Hi,

That code you sent sent me is for a windows/dos system.

I looked at vga.h because I want the simplest way possible to read and write pixels from the screen.

Would most people use openGL for this ?

If so how do I get started with it.

Mark.

if you just need things like getpixel and drawpixel i would suggest using SDL without OpenGL. SDL (Simple Directmedia Layer) offers some basic graphics as well as keyboard/mouse input, it is also used a lot in combination with OpenGL, but unless you really need hardware accelleration just SDL will work fine for you.
You can find tutorials at the [SDL website]("http://www.libsdl.org/").

---

### Post by cgroza on 2011-06-17
> **Petrolea said:**
> Function probably returns incompatible type with int.
Wouldn't that generate a compile time error?

---


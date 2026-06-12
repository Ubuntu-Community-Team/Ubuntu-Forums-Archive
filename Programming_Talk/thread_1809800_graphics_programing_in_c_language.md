---
title: "graphics programing in c language"
date: 2011-07-22
forum: Programming Talk
---

### Post by aju1991 on 2011-07-22
I use ubuntu11.04.
In i installed svga packages to do graphics programing in c lang.
It is compiling in my computer. but i donot get the result.
it only display a black screen. 
My laptop's resoluuton is 16:9.
When the mode changes using
vga_setmode( )
its screen colour changes to blue.
then comuter become hang.
then i need ti restart my laptop.
please help me anyone to solve this problem

---

### Post by Tony Flury on 2011-07-22
Can you post your code please - right now the problem could be anything.

Use Code Tags (assuming the code is short) - and include the smallest code segment that demonstrates the problem.

---

### Post by aju1991 on 2011-07-22
#include<stdio.h>
#include<vga.h>
main()
{
vga_init();
vga_setmode(43);
vga_drawline(50,50.200,200);
vga_getch();
vga_setmode(0);
}

---

### Post by Tony Flury on 2011-07-22
Mode 43 suggests that your Laptop can handle G1152x864x16M32 - i.e. 1152 x 864 resolution with 16million colours - can your laptop handle that.

Try calling : vga_lastmodenumber to get the highest mode number your system supports, or call  vga_hasmode(43) to see if your system can support the mode you are requesting

---

### Post by aju1991 on 2011-07-22
> **Tony Flury said:**
> Mode 43 suggests that your Laptop can handle G1152x864x16M32 - i.e. 1152 x 864 resolution with 16million colours - can your laptop handle that.

Try calling : vga_lastmodenumber to get the highest mode number your system supports, or call  vga_hasmode(43) to see if your system can support the mode you are requesting

I tried with different mode.
When i gave this mode screen become black.
Small numbers give blue colour screen.
Very small numbers give blue cour screen with some small parallel lines

---

### Post by Tony Flury on 2011-07-26
Have you read the man pages or try any of the suggestions ?

setmode man page : [http://linux.die.net/man/3/vga_setmode](http://linux.die.net/man/3/vga_setmode)

hasmode man page : [http://linux.die.net/man/3/vga_hasmode](http://linux.die.net/man/3/vga_hasmode)

Which svga package did you install ?

What other mode numbers did you try - do they appear on the man pages above ?

It is possible that you have chosen an SVGA mode that your PC cannot support.

I will try later and see what my PC does.

---

### Post by clubsoda on 2011-11-19
aju1991, maybe [this thread](http://ubuntuforums.org/showthread.php?t=1883334) will help.

---


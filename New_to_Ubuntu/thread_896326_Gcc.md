---
title: "Gcc"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by e_pech on 2008-08-21
So, I'm totally new to Linux, as far as I understand, ubuntu comes with a C Compiler (gcc). If I open a Terminal i can type 'gcc' and it's recognized, however I made a small program in C (with the text editor) and when I type "gcc -c hola.c" it just doesn't work...

this is the program I wrote:

```
#include <math.h>

int main(int argc, char **argv)
{

	return 1;

}
```

IT tells me the following:

pech@PechLaptopWithUbuntu:~$ gcc -c hola.c
hola.c:1:18: error: math.h: No such file or directory

So.... what's wrong?? my guess is that I might not either have the files (but why would I have the compiler??) or that there is some kind of variable (like PATH in Windows) that I must modify... 

I just installed Ubuntu 7.04... Please help me.. I'm really interested in learning Linux....

Thanks in advance!!

---

### Post by enitink on 2008-08-21
check if libgcc is installed or not!!!
by going to synaptic package manager.....

---

### Post by tarps87 on 2008-08-21
The problem is it can not find the math.h libary, try installing libgcc
Edit: Just remembered, try:```

sudo apt-get install build-essential
```
The library should be in there

---

### Post by hvc123 on 2008-08-21
have you installed build essential

sudo apt-get install build-essential

---

### Post by mali2297 on 2008-08-21
Install the package **build-essential**.

You might also need to tell gcc to check for the math library, this is done by adding -lm as an argument:
```

gcc -lm hola.c

```

---

### Post by e_pech on 2008-08-21
I'll try it and hit back to you guys.... thank you sooo much for your quick reply... thanks...

---

### Post by e_pech on 2008-08-21
Thank you very much, now it compiles, how can I make an executable file (like in windows)?

---

### Post by Joeb454 on 2008-08-21
Run ```
gcc myprogram.c -o myprogram
```

You will then be left with an executable called "myprogram"

---

### Post by mali2297 on 2008-08-21
> **e_pech said:**
> Thank you very much, now it compiles, how can I make an executable file (like in windows)?

If you don't specify the name of the executable (with *-o exec_name*) then it will be called *a.out*. If it is in the current directory, you run it with
```

./a.out

```

---

### Post by e_pech on 2008-08-21
You guys are great.. Thank you very much for all the info, I now have a little 'Hello world program' (in spanish cuz I'm mexican heheh). Thank you, everything was really helpful. I have a new one for you guys, how can I start developing with OpenGL under Linux?? I tried adding 

```

#import <GL/gl.h>
#import <GL/glut.h>

```

It doesn't work... any ideas/suggestions?

---

### Post by mali2297 on 2008-08-21
Try installing **freeglut3-dev**.

You can search the contents of packages in Synaptic, and also on this site:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

For instance, a search for *glut.h* gives you the package above.

---

### Post by e_pech on 2008-08-21
> **mali2297 said:**
> Try installing **freeglut3-dev**.

You can search the contents of packages in Synaptic, and also on this site:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

For instance, a search for *glut.h* gives you the package above.

Thanks man, I installed that library already and it recognizes the GL/glut.h directive. However it does not recognizes the instructions (glutInit, etc...) "undefined reference".
Is it the way I'm compiling it??

---

### Post by mali2297 on 2008-08-21
Why do you use *#import* instead of *#include*?

---

### Post by elmoosecapitan on 2008-08-21
try:

#include "headername.h"

instead of:

#import <headername.h>


subtle, but very important differences.

---

### Post by e_pech on 2008-08-21
> **mali2297 said:**
> Why do you use *#import* instead of *#include*?


Hahhaa... yeah, that's the one I'm using... #include ...
It was just how I was compiling it... thank you!! I think I'm good to go now (I wasn't including the  -lglut ) on the gcc command line.... THanks!!!

---

### Post by e_pech on 2008-08-21
Another question, I ran a program which uses GLUT, I'd like to do something like what I do with MFC... Have menus, some kind of View Where I can draw in OpenGL... I mean, I just want a Window with menus, resizable and stuff liek that... how can I do that?? I'd really appreciate your help...

I realized something, I'm using the Desktop Effects in Ubuntu 7.04 and when the GLUT window is displayed, it won't show the Title bar with the Minimize, Maximize, Close buttons... If I disable Desktop Effects, everything works perfectly, strange.. does anyone have an explanation??

---


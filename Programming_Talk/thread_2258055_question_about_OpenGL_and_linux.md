---
title: "question about OpenGL and linux"
date: 2014-12-24
forum: Programming Talk
---

### Post by geno3 on 2014-12-24
Hello, Merry Christmas!

 I'm messing around with OpenGL development in Linux. This is my first time trying to develop any executable on Linux. I have Ubuntu 14.


I used the OpenGL library to create a very simple red window with some text. I compiled it, and created the ".out" file. I ran it from Ubuntu and it works perfectly.


I gave it to a friend to try on a different Linux machine, and its not working. I need to get more details on what isnt working about it.


First of all, and forgive me if this is utter nonsense, I am used to working with micro-controllers where I dont have an OS, and where the processor only executes a single program in its entire lifetime. I have worked with graphics before, but it was for an ARM micro-controller and I created my own graphics driver as well as higher level code to display images on the LCD. So when it comes to machines that run an OS, I may be asking stupid questions. Just warning.


If I create an executable ".out" file which was compiled from C with the OpenGL library, according to my understanding, the binary file is telling the OS to control the graphics driver directly. The OS should not need any library files to run my ".out" file. At least thats the way it works on a uC with no OS, haha. You can tell how new I am to machines with an OS.

Does my friend need freeglut3-dev to run my .out file?

Here is the file if anyone wants to try it out. 
[http://expirebox.com/download/722f8037168711e657058e4aef6eb61d.html](http://expirebox.com/download/722f8037168711e657058e4aef6eb61d.html)

---

### Post by sisco311 on 2014-12-24
Thread moved to **Programming Talk**.

It would be more helpful if you could post the source code and the options you used to compile it. 

I downloaded the binary. It's a 32bit executable and it uses shared libraries (it's dynamically linked). ;)
```
file   geno_opengl.out geno_opengl.out: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=b53394275072c09dd66f9a8fcc51598da44c4c5b, not stripped

```

You can use the ldd command to print the shared library dependencies, here is the output of ldd on my system:
```
ldd -d geno_opengl.out 	linux-gate.so.1 (0xf7771000)
	libGL.so.1 => not found
	libglut.so.3 => not found
	libc.so.6 => /usr/lib32/libc.so.6 (0xf7595000)
	/lib/ld-linux.so.2 (0xf7772000)

```

You either install the missing libs on your friends computer or create a statically linked app.

---

### Post by geno3 on 2014-12-25
Thank you, I'm going to go read about statically and dynamically linked apps.

---

### Post by schragge on 2014-12-26
Packages containing missing libraries:
```

[COLOR=green]$ [/COLOR]apt-file -x find 'lib(GL|glut)\.so\.\d$' | rev | sort -t/ -k1 | rev
[COLOR=green]nvidia-331: /usr/lib/nvidia-331/libGL.so.1
nvidia-304: /usr/lib/nvidia-304/libGL.so.1
libgl1-mesa-glx: /usr/lib/i386-linux-gnu/mesa/libGL.so.1
nvidia-331-updates: /usr/lib/nvidia-331-updates/libGL.so.1
nvidia-304-updates: /usr/lib/nvidia-304-updates/libGL.so.1
primus-libs: /usr/lib/i386-linux-gnu/primus/libGL.so.1
fglrx-updates: /usr/lib/fglrx/libGL.so.1
fglrx: /usr/lib/fglrx/libGL.so.1
freeglut3: /usr/lib/i386-linux-gnu/libglut.so.3[/COLOR]

```

---


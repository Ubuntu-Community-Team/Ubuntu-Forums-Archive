---
title: "Installing freeglut and OpenGl"
date: 2007-01-23
forum: Programming Talk
---

### Post by wideback on 2007-01-23
This is a simple tutorial to show a new linux user (such as myself) how to setup freeglut and OpenGl. 

System used IBM T22 ThinkPad: 
   mobile pentium 3 900mhz
   256mb ram 
   20GB hd 
   S3 Inc. 86C270-294 Savage/IX-MV    (rev 13) video card

OS: xubuntu 6.10

I have just recently become a linux user and wanted to install freeglut to do my graphics assignments on my laptop. Although the install did not turn out to be very difficult it took me a while to do. So I have written this tutorial in case another young linux user comes along and decides he/she wants to install freeglut and OpenGL.

**This tutorial assumes that you have your operating system installed and you have access to the internet** 

Steps:

From a terminal

1) sudo apt-get update 
 
-This will update your apt database to the most recent available packages.

2) sudo apt-get install build-essential

- This installs the necessary development tools for building source code.

3) sudo apt-get install freeglut3-dev

- This installs the development libraries and headers for freeglut.

Your done! Extremely simple! However you must remember that when compiling you must add a '-lglut' as a comand line argument to gcc. If you don't it cannot find the library's and you will get undefined reference errors.

example command line: gcc simple.c -lglut

At this point if your program compiles and runs then you are finished. However the first time I tried to run mine I received a 'libGL warning: 3D driver claims to not support visual 0x42'. This error means I cannot display the required colors to run the program. In my case I had the most recent drivers for my video card. So I did some research on my monitor and found out it can display a color depth of 24 instead of the 16 it was set at. To fix this problem you must edit the /etc/X11/xorg.conf file as root and set the 'DefaultDepth  24'. Reboot and the problem is solved.

This is my first post (and tutorial) on the ubuntuforums. If people feel that this tutorial is not needed they can feel free to remove it. If anyone wants to add anything related to freeglut or OpenGl please feel free.

:guitar:

---

### Post by luckstrikes on 2008-12-23
thank you, thank you, thank you!!!

---

### Post by l3ftm1n0r on 2009-02-26
Thanks!! Just what i was looking for. Btw has anyone tried to compile the freeglut package manually because i tried that before this apt-get method and it spewed out errors. Please help me out.

---

### Post by Ferrat on 2009-02-27
> **l3ftm1n0r said:**
> Thanks!! Just what i was looking for. Btw has anyone tried to compile the freeglut package manually because i tried that before this apt-get method and it spewed out errors. Please help me out.

What errors? according to apt-get the package is there

---

### Post by Dlambert on 2010-06-19
Thanks Man!:KS:KS:KS:KS:KS

---

### Post by durjoy on 2010-08-19
Previously I am using 9.04. It has installed a software called Autodoc. It requires freeglut. While upgrading to Ubuntu 10.04 LTS, all rpm files are disabled. I have again install freeglut. But while trying to run this software it  shows following error.
[FONT=Arial][SIZE=2]Try adjusting the vblank_mode configuration parameter.
freeglut  ERROR:  Function <glutSolidSphere> called without first calling 'glutInit'.
[/SIZE][/FONT]Can any one help to solve this?

---

### Post by joshig on 2010-10-03
Those steps are very quick and very helpful.  To go with that speed, it would be nice to have a simple.c to try compiling at the end instead of having to look around for examples that will work with the newly installed freeglut package.

---

### Post by lsteamer on 2010-10-14
Hey.

I want to start working with GL, I'm a newbie here on that. 
Apparently i got a "code-test" to check if the packages are installed.

Apparently all of them are! still, It gives me an error on the Terminal.

This one:
> g++ -Wall -o cube main.cpp imageloader.cpp -lglut
imageloader.cpp: In function ‘Image* loadBMP(const char*)’:
imageloader.cpp:141: warning: suggest parentheses around ‘&&’ within ‘||’
/tmp/ccenhiwc.o: In function `handleResize(int, int)':
main.cpp:(.text+0x183): undefined reference to `gluPerspective'
collect2: ld returned 1 exit status
make: *** [cube] Error 1


I'm probably overlooking something. Can you help me out?

---

### Post by Rayston on 2010-10-30
When I do the last step I get this error. 

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 freeglut3-dev : Depends: libglu1-mesa-dev but it is not going to be installed or
                          libglu-dev
E: Broken packages



if I try this command 

sudo apt-get install libglu1-mes

I get this. 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libglu1-mesa is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.


Any ideas?

---

### Post by EarthVsMe on 2010-11-08
_@_[lsteamer]("http://ubuntuforums.org/member.php?u=1148264") 


I'm getting the same errors. I worked with those video tutorial's on window's and they all compiled fine. I really want to fix that.

---

### Post by Dlambert on 2011-01-15
How do you get OpenGl 4.0 Libraries?

---

### Post by olgis on 2011-02-08
Thank you for tutorial.

---

### Post by hakura11 on 2011-04-24
When using code::blocks, I tried to start a new glut project but when it asks for a directory there isn't one for the glut stuff I just installed, am I doing this wrong? Should I just start a new openGL project instead? Bit confused about this, thanks if anyone can help.

---

### Post by Inder on 2011-07-10
I have a similar problem.

I'm trying to get an existing project to work in Codeblocks and I'm getting "undefined reference to ..." errors relating to functions like:
glEnableClientState
glTexCoordPointer
glVertexPointer
etc..

I assume I must add "-lglut" to the compiler options, but I am not using a makefile so I don't know how to do this.

Any clues?

---

### Post by Ramy89 on 2011-07-23
I have followed the guide, but when I try to compile including <gl/glu.h> , I get an error: "gl/glu.h : no such file or directory".
Do I have to add the -glut string somewhere in code:.blocks options?

---

### Post by mandddam on 2011-07-29
Hi is it necessary to have the packages downloaded to use sudo get apt-or is it required to have net connection,im having lot of problems with the sudo apt method,
and am downloading and installing all opengl packages from the net,[www.debian.org,i](www.debian.org,i) still have unmet dependencies for libx11,libglu1-mesa ,
what i require is that the gl.h and glut.h files are there in usr/include/GL,
as of now the files are gl.h,glext.h,gl_mangle.h and omesa.h,
i would like to get a basic opengl program running and then run a 2d game which i wrote on windows,thanks,
my configuration is ubuntu9.04,i486,(jaunty?) 
-And is it possible to have glaux.h there in the ../GL directory as well ?becouse that would be the best, as i have used that in the windows code,and am very lazy..(do not want to write more func)

---

### Post by KreshDev on 2011-09-14
Thanks a lot for this great tutorial. It helped me a lot to finally install that little piece of happiness that is OpenGL SDK. I have been looking for a way to install it on Windows 7 and haven't found any single working tutorial for me. Everything have installed well so far, so I guess it is all working fine.

---

### Post by umeju on 2011-09-28
> **Rayston said:**
> When I do the last step I get this error. 

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 freeglut3-dev : Depends: libglu1-mesa-dev but it is not going to be installed or
                          libglu-dev
E: Broken packages



if I try this command 

sudo apt-get install libglu1-mes

I get this. 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libglu1-mesa is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.


Any ideas?

hi!
i know it's about many time ago...but did u solve it? i have the same problem for a univ. project and it stopped me...

---

### Post by shubham1 on 2012-01-07
thanks

---

### Post by laserator on 2012-02-10
Thank You! so now what do include is it <glu> or <glux> or what?

---

### Post by laserator on 2012-04-09
Yup it doesn't work for me either. I dont understand.

---

### Post by laserator on 2012-04-09
Could you explain how to do this in code::blocks?

---

### Post by cirosantilli on 2012-08-10
I also had to put the compiler option -lGLU making

gcc -o prog prog.cpp  -lglut -lGLU 

or else I get:

undefined reference to `gluOrtho2D' if I try to use a gluOrtho2D.

Some day I'gonna understand why I will!

---

### Post by Proteasome on 2012-11-14
Total newbie question about the following statement in the first post:

"example command line: gcc simple.c -lglut"

Having not compiled before, I'm unsure why `gcc simple.c -lglut` fails to find the file "simple.c" 

Can anyone tell me where it's located, or am I on the completely wrong track?

Thanks!

---


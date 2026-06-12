---
title: "How to compile this program ..."
date: 2009-03-05
forum: Programming Talk
---

### Post by Bob John on 2009-03-05
I found this code from magazines . I think it's interesting . Its goal was to realise a flying flag with a windows logo and word "98". But it occurs lots of errors when I tried to compile it.

The source code as follows:
```
#include <graphics.h>
#include <math.h>
#include <conio.h>
#include <stdlib.h>
#define NUMBER 8
#define PI 3.14
#define STRING "1998"
#define MAXSIZE 24
#define DEFSIZE 16
struct FLY_H
{
	int x,y;
	int size;
	char font;
	int color;
	int rale;
};
void fly(struct FLY_H *f);
main()
{
	int drive=VGA,mode=VGAHI;
	int i;
	struct FLY_H f[NUMBER];
	initgraph(&drive,&mode,"c:\\tc");
	randomize();
	for(i=0;i<NUMBER;i++)
	{
		f[i].x=random(getmaxx()/3)+getmaxx()/3;
		f[i].y=random(getmaxy()/3)+getmaxy()/3;
		f[i].color=random(15)+1;
		f[i].font=random(4)+1;
		f[i].size=1;
		f[i].rale=random(360);
	}
while(bioskey(1)!=0x011b)
	for(i=0;i<NUMBER &&bioskey(1)!=0x11b;i++)
	{
		fly(&f[i]);
		if(bioskey(1))
		{
			if(bioskey(1)!=0x11b);
				getch();
		}
	}
	closegraph();
}
void fly(struct FLY_H *f)
{
	setcolor(getbkcolor());
	settextstyle(f->font,HORIZ_DIR,0);
	setusercharsize(f->site,DEFSIZE,f->size,DEFSIZE);
	outtextxy(f->x,f->y,STRING);
	if (f->size+1<=MAXSIZE)
		f->size++;
		f->x+=STEP*cos((float)f->rale/180.0*PI);
		f->y+=STEP*sin((float)f->rale/180.0*PI);
	if (f->x>getmaxx()||f->y>getmaxy()
	    ||f->x+f->size*strlen(STRING)<0
	    ||f->y+f->size*strlen(STRING)<0)
	{
		f->x=random(getmaxx()/3)+getmaxx()/3;
		f->y=random(getmaxy()/3)+getmaxy()/3;
		f->color=random(15)+1;
		f->font=random(4)+1;
		f->size=1;
		f->rale=random(360);
	}
	setcolor(f->color);
	settextstyle(f>font,HORIZ_DIR,0);
	setusercharsize(f->size,DEFSIZE,f->size,DEFSIZE);
	outtextxy(f->x,f->y,STRING);
}

```
The error message as follows:
```
bob@bob-laptop:~/c$ gcc flying98.c -o flying98 -Wall
flying98.c:1:22: error: graphics.h: No such file or directory
flying98.c:3:19: error: conio.h: No such file or directory
flying98.c:20: warning: return type defaults to &#8216;int&#8217;
flying98.c: In function &#8216;main&#8217;:
flying98.c:21: error: &#8216;VGA&#8217; undeclared (first use in this function)
flying98.c:21: error: (Each undeclared identifier is reported only once
flying98.c:21: error: for each function it appears in.)
flying98.c:21: error: &#8216;VGAHI&#8217; undeclared (first use in this function)
flying98.c:24: warning: implicit declaration of function &#8216;initgraph&#8217;
flying98.c:25: warning: implicit declaration of function &#8216;randomize&#8217;
flying98.c:28: warning: implicit declaration of function &#8216;getmaxx&#8217;
flying98.c:28: error: too many arguments to function &#8216;random&#8217;
flying98.c:29: warning: implicit declaration of function &#8216;getmaxy&#8217;
flying98.c:29: error: too many arguments to function &#8216;random&#8217;
flying98.c:30: error: too many arguments to function &#8216;random&#8217;
flying98.c:31: error: too many arguments to function &#8216;random&#8217;
flying98.c:33: error: too many arguments to function &#8216;random&#8217;
flying98.c:35: warning: implicit declaration of function &#8216;bioskey&#8217;
flying98.c:42: warning: implicit declaration of function &#8216;getch&#8217;
flying98.c:45: warning: implicit declaration of function &#8216;closegraph&#8217;
flying98.c:46: warning: control reaches end of non-void function
flying98.c: In function &#8216;fly&#8217;:
flying98.c:49: warning: implicit declaration of function &#8216;setcolor&#8217;
flying98.c:49: warning: implicit declaration of function &#8216;getbkcolor&#8217;
flying98.c:50: warning: implicit declaration of function &#8216;settextstyle&#8217;
flying98.c:50: error: &#8216;HORIZ_DIR&#8217; undeclared (first use in this function)
flying98.c:51: warning: implicit declaration of function &#8216;setusercharsize&#8217;
flying98.c:51: error: &#8216;struct FLY_H&#8217; has no member named &#8216;site&#8217;
flying98.c:52: warning: implicit declaration of function &#8216;outtextxy&#8217;
flying98.c:55: error: &#8216;STEP&#8217; undeclared (first use in this function)
flying98.c:58: warning: implicit declaration of function &#8216;strlen&#8217;
flying98.c:58: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
flying98.c:61: error: too many arguments to function &#8216;random&#8217;
flying98.c:62: error: too many arguments to function &#8216;random&#8217;
flying98.c:63: error: too many arguments to function &#8216;random&#8217;
flying98.c:64: error: too many arguments to function &#8216;random&#8217;
flying98.c:66: error: too many arguments to function &#8216;random&#8217;
flying98.c:69: error: &#8216;font&#8217; undeclared (first use in this function)
bob@bob-laptop:~/c$ 
```

So what to do with it to make it work ?
Thanks for your reply .

---

### Post by sujoy on 2009-03-05
hmm, as far as i can recall, graphics.h comes only with turboC (an outdated compiler/IDE).

there is an alternative for linux, called libgraph, although in my opinion you'd do better by using openGL or SDL for this. you should still be able to apply the same programming logic, only with different function calls

EDIT: functionalities from conio.h can be found in the ncurses libs

---

### Post by wmcbrine on 2009-03-05
Yes, this is not portable C; it's aimed very specifically at a very old compiler environment that you'd be hard-pressed to find nowadays. It's not even a Windows program (despite being a Windows ad), but rather a DOS program.

Now, if you do find Turbo C, you should be able to build and run this program under DOSBox or DOSEmu.

BTW, use [ code ] tags rather than [ quote ] (without spaces) to preserve the indentation.

P.S. Even in 1998, I think that choice of environment would've seemed quaint.

---

### Post by Firestom on 2009-03-05
Even though the code looks doubtful, it is possible to compile it under Ubuntu. Just type ```
apt-get build-essential
``` and the standard libraries for C will be downloaded. Then to compile, create a Makefile (don't ask me, I don't know how these work) and compile it using the make command.

---

### Post by wmcbrine on 2009-03-05
> **Firestom said:**
> Even though the code looks doubtful, it is possible to compile it under Ubuntu.No, really, it isn't.

> *Just type ```
apt-get build-essential
``` and the standard libraries for C will be downloaded.*Too bad the program requires nonstandard libraries.

---

### Post by namegame on 2009-03-05
> **Firestom said:**
>  Then to compile, create a Makefile (don't ask me, I don't know how these work) and compile it using the make command.

You don't even need a makefile. For a single source file, gcc is quite adequate. You could create a makefile, but I fail to see the utility in that...

---

### Post by Bob John on 2009-03-05
After reading your posts , I downloaded Turbo C 2.0 from Internet on Windows Platform .
So I tried to compile it by Turbo C 2.0 . It really successfully worked ! Also I found some typing mistakes in the source code . So I put the correct code here :
```
#include <graphics.h>
#include <math.h>
#include <conio.h>
#include <stdlib.h>
#define STEP 5
#define NUMBER 8
#define PI 3.14
#define STRING "1998"
#define MAXSIZE 24
#define DEFSIZE 16
struct FLY_H
{
	int x,y;
	int size;
	char font;
	int color;
	int rale;
};
void fly(struct FLY_H *f);
main()
{
	int drive=VGA,mode=VGAHI;
	int i;
	struct FLY_H f[NUMBER];
	initgraph(&drive,&mode,"c:\\tc");
	randomize();
	for(i=0;i<NUMBER;i++)
	{
		f[i].x=random(getmaxx()/3)+getmaxx()/3;
		f[i].y=random(getmaxy()/3)+getmaxy()/3;
		f[i].color=random(15)+1;
		f[i].font=random(4)+1;
		f[i].size=1;
		f[i].rale=random(360);
	}
while(bioskey(1)!=0x011b)
	for(i=0;i<NUMBER &&bioskey(1)!=0x11b;i++)
	{
		fly(&f[i]);
		if(bioskey(1))
		{
			if(bioskey(1)!=0x11b);
				getch();
		}
	}
	closegraph();
}
void fly(struct FLY_H *f)
{
	setcolor(getbkcolor());
	settextstyle(f->font,HORIZ_DIR,0);
	setusercharsize(f->size,DEFSIZE,f->size,DEFSIZE);
	outtextxy(f->x,f->y,STRING);
	if (f->size+1<=MAXSIZE)
		f->size++;
		f->x+=STEP*cos((float)f->rale/180.0*PI);
		f->y+=STEP*sin((float)f->rale/180.0*PI);
	if (f->x>getmaxx()||f->y>getmaxy()
	    ||f->x+f->size*strlen(STRING)<0
	    ||f->y+f->size*strlen(STRING)<0)
	{	f->x=random(getmaxx()/3)+getmaxx()/3;
		f->y=random(getmaxy()/3)+getmaxy()/3;
		f->color=random(15)+1;
		f->font=random(4)+1;
		f->size=1;
		f->rale=random(360);
	}
	setcolor(f->color);
	settextstyle(f->font,HORIZ_DIR,0);
	setusercharsize(f->size,DEFSIZE,f->size,DEFSIZE);
	outtextxy(f->x,f->y,STRING);
}

```

Besides I think since it is lack of some .h files to compile , how about copying these .h files to Linux and let GCC to use them ? Basically , I think it should work . What do you think , Friends ?

---

### Post by sujoy on 2009-03-05
no just copying the header files wont do. as already mentioned by wmcbrine, you can run it in a dos emulator in linux, but even then you'll need turbo C to compile them.

the codes and header files are specific to turbo C and DOS. you cannot just copy the header files.

---

### Post by Bob John on 2009-03-06
Maybe I should read something about how GCC works . :P

---

### Post by sujoy on 2009-03-06
hmm and the POSIX standard in general ...

---

### Post by Bob John on 2009-03-06
I will . :)

---

### Post by MGaddict2000 on 2009-03-29
I am new to linux programming. Ive pulled up a bunch of my old, old, programs from Comp. Sci. I took in HS. We used the 16bit Borland C++ compiler then. I also was taught that a lot of the headers we used were not standard while some at the time were soon to be standardized such as iostream. I'm glad to see that happened. But now, because of the world only teaching windows at the time, I'm used to using simple functions within conio, stdlib, math.h, constrea.h, and dos.h. Obviously a lot of these won't work in linux. I don't really care about dos.h as all it did was change the text color for me.  conio.h on the other hand contains some useful functions for clearing a terminal window and recording keystorkes (clrscr, getch, and kbhit) These are very useful functions when working with a terminal window as they allow you to work with a clean working space and a function can run until a key is hit as in....

char key;
do 
 {
  blah blah blah... //all the crap you want running
 }
while(!kbhit()); //keep going as long as a key is not pressed on the keyboard
key = getch(); // record whatever key was pressed
blah blah blah; //do something according to the key pressed.

there has to be an alternative way of accomplishing this same idea in linux. I use to use graphic.h but I'm also interested in learning opengl. graphic.h was outdated when I took the class but it was a very simple way to draw lines and place a pixel on the screen. If you have a reference to where I can learn about that, I would appreciate it.

Back to the conio.h issue, I see a lot of posts where people have asked about it and the only response they get is... "remove it, its not in the standard library." I got that, how about some help on finding an alternative.

---

### Post by Zugzwang on 2009-03-29
> **MGaddict2000 said:**
> Back to the conio.h issue, I see a lot of posts where people have asked about it and the only response they get is... "remove it, its not in the standard library." I got that, how about some help on finding an alternative.

There's "libconio", a replacement for it for Linux. However, its development has been abandoned, as it seems:

[http://sourceforge.net/projects/libconio](http://sourceforge.net/projects/libconio)

---

### Post by meganox on 2009-03-29
[http://en.wikipedia.org/wiki/Ncurses](http://en.wikipedia.org/wiki/Ncurses)

[http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/](http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/)

---

### Post by MGaddict2000 on 2009-03-29
Thank you so much to the last two folks. Giving a link to a page to help with a solution is far more helpful then just saying, "remove conio.h and its functions." I really appreciate that. I've gone through numerous questions about this stupid header and this is the first useful link I've found. Thanks again.

---


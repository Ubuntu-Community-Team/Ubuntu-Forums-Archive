---
title: "Noobie question: how to load a image file in C/C++"
date: 2009-01-22
forum: Programming Talk
---

### Post by InSaN3 GoDLiK3 on 2009-01-22
how could i load an image like .png .bmp etc on C or C++ i searched google all over and couldn't find anything

---

### Post by jimi_hendrix on 2009-01-22
are you making a game or some GUI app?

---

### Post by snova on 2009-01-22
> **InSaN3 GoDLiK3 said:**
> how could i load an image like .png .bmp etc on C or C++ i searched google all over and couldn't find anything

"Load" is pretty abstract, it can mean a lot of different things depending on what you're going to do with it afterwards.

What are you trying to accomplish here?

---

### Post by InSaN3 GoDLiK3 on 2009-01-22
psp app trying to load a background and cant find out how to

---

### Post by monkeyking on 2009-01-22
You can easily just load the file as a binary file,
but that will just give a memory glob.

It depends on what you are planing to do with the file.

This is a copy paste
[PHP]
// reading a complete binary file
#include <iostream>
#include <fstream>
using namespace std;

ifstream::pos_type size;
char * memblock;

int main () {
  ifstream file ("example.bin", ios::in|ios::binary|ios::ate);
  if (file.is_open())
  {
    size = file.tellg();
    memblock = new char [size];
    file.seekg (0, ios::beg);
    file.read (memblock, size);
    file.close();

    cout << "the complete file content is in memory";

    delete[] memblock;
  }
  else cout << "Unable to open file";
  return 0;
}
[/PHP] 
from here [http://www.cplusplus.com/doc/tutorial/files.html](http://www.cplusplus.com/doc/tutorial/files.html)

---

### Post by bgs100 on 2009-01-22
[http://www.vbforums.com/showthread.php?t=261522](http://www.vbforums.com/showthread.php?t=261522) ???

---

### Post by InSaN3 GoDLiK3 on 2009-01-22
well like i said im making a play station portable application aka homebrew and i would like to give this app a background like say halo.png as the background file how would i make the png file load into my C/C++ source. some example of psp C/C++ programming is 

```
//file name main.c
#include <pspkernel.h>
#include <pspdebug.h>
#include <pspdisplay.h>
```

---

### Post by CptPicard on 2009-01-22
Sorry, but I think you should just spend some more time learning programming in general, as that was the most clear example I've ever seen of someone being totally out of their depth.

You may want to consider starting with Python and working onwards from there...

---

### Post by Cracauer on 2009-01-22
> **InSaN3 GoDLiK3 said:**
> how could i load an image like .png .bmp etc on C or C++ i searched google all over and couldn't find anything

I use ImageMagick, but it is pretty slow. For some formats it's better to have a more direct loader such a libjpeg.

---

### Post by InSaN3 GoDLiK3 on 2009-01-22
i know programming like lua, some php, (hacking Xss) etc but C/C++ in psp is different from the regular C/C++ heres and example of hello world

```
#include <pspkernel.h>
#include <pspdebug.h> 
PSP_MODULE_INFO("Hello World", 0, 1, 1);
#define printf pspDebugScreenPrintf 

/* Exit callback */
int exit_callback(int arg1, int arg2, void *common) {
          sceKernelExitGame();
          return 0;
}

/* Callback thread */
int CallbackThread(SceSize args, void *argp) {
          int cbid;

          cbid = sceKernelCreateCallback("Exit Callback", exit_callback, NULL);
          sceKernelRegisterExitCallback(cbid);

          sceKernelSleepThreadCB();

          return 0;
}

/* Sets up the callback thread and returns its thread id */
int SetupCallbacks(void) {
          int thid = 0;

          thid = sceKernelCreateThread("update_thread", CallbackThread, 0x11, 0xFA0, 0, 0);
          if(thid >= 0) {
                    sceKernelStartThread(thid, 0, 0);
          }

          return thid;
}  
int main() 
{ 
pspDebugScreenInit();
SetupCallbacks(); 
printf("Hello World"); 
sceKernelSleepThread(); 
return 0;
}


***********************************
The Makefile for ubuntu 

TARGET = hello
OBJS = main.o

CFLAGS = -O2 -G0 -Wall
CXXFLAGS = $(CFLAGS) -fno-exceptions -fno-rtti
ASFLAGS = $(CFLAGS)

EXTRA_TARGETS = EBOOT.PBP
PSP_EBOOT_TITLE = Hello World

PSPSDK=$(shell psp-config --pspsdk-path)
include $(PSPSDK)/lib/build.mak

******************************************
```

---

### Post by CptPicard on 2009-01-22
Seems like perfectly valid, normal C. PSP appears to use some kind of callback model in its applications. Do you understand how that Hello World works?

---

### Post by InSaN3 GoDLiK3 on 2009-01-22
yes fully understand it could write it in my sleep lol but with psp they have alot of commands different from original C like
 #include <pspkernel.h>
#include <pspdebug.h>
dont know all of them 

#define printf pspDebugScreenPrintf /* Exit callback */
int exit_callback(int arg1, int arg2, void *common) {
          sceKernelExitGame();
          return 0;
}

/* Callback thread */
int CallbackThread(SceSize args, void *argp) {
          int cbid;

          cbid = sceKernelCreateCallback("Exit Callback", exit_callback, NULL);
          sceKernelRegisterExitCallback(cbid);

          sceKernelSleepThreadCB();

          return 0;
}

/* Sets up the callback thread and returns its thread id */
int SetupCallbacks(void) {
          int thid = 0;

          thid = sceKernelCreateThread("update_thread", CallbackThread, 0x11, 0xFA0, 0, 0);
          if(thid >= 0) {
                    sceKernelStartThread(thid, 0, 0);
          }

          return thid;
}

---

### Post by CptPicard on 2009-01-22
> **InSaN3 GoDLiK3 said:**
> yes fully understand it could write it in my sleep lol

Are you sure you can't just copy-paste it in your sleep, but actually understand how it works and what it does? ;)

> 
 but with psp they have alot of commands different from original C like
 #include <pspkernel.h>
#include <pspdebug.h>
dont know all of them 

Those aren't really called "commands", they are header includes for PSP-specific libraries. Again perfectly normal and elementary in C programming.

---

### Post by InSaN3 GoDLiK3 on 2009-01-22
well i don't copy and paste( you'll never learn by doing so ) i usually try and learn it on my own like i did lua but as you can tell C/C++ is very advance also im new to learning C so please give me a break

---

### Post by CptPicard on 2009-01-22
> **InSaN3 GoDLiK3 said:**
> also im new to learning C

Yeah... there is no point in trying to tackle what you're trying before you know C better. I mean, if you do not understand the concept of header files, you really need to go back to the very, very basics...

---

### Post by InSaN3 GoDLiK3 on 2009-01-22
we all have to get started some were including you some people chose were to start like me i want to start in psp C, we all learn differently and i don't know if there is a basic below "HELLO WORLD" because thats were im starting im pretty sure thats the basic basics anyways

---

### Post by CptPicard on 2009-01-22
First of all, there is no such thing as "PSP C". You are just simply trying to tackle programming on a much harder platform, with its associated libraries and architecture, than your current skillset will allow.

The basic Hello World in C is...

```

#include <stdio.h>

int main() {
  printf("Hello World!\n");
}

```


I am not trying to be mean here or anything, just giving you the obvious facts so that your learning process is smoother and more efficient. You need to learn to crawl before you can walk.

---

### Post by InSaN3 GoDLiK3 on 2009-01-22
true well ok your right ill start learning (which do you recommend C or C++ ) and ill get started right away

---

### Post by CptPicard on 2009-01-22
Keep on working on C... it is a fairly small language actually. Soon you'll actually understand what you are seeing in that PSP code snippet of yours.

---

### Post by InSaN3 GoDLiK3 on 2009-01-22
ok thank you ill add you on msn then im out peace :)

---

### Post by loganwm on 2009-01-22
I don't want to be rude, but I feel I should intervene, and please don't take what I say as flaming or hate speech or anything negative.

I've seen you posting around here and I'm assuming you've got a basic understanding of PSP Lua and probably some kind of web design language. Don't fear though I took the same track on my programming learning only I vacated the PSP platform for application development for Desktop environments.

Lesson #1
The Original Lua language used on the Desktop platform is a different dialect from the PSP Lua. The PSP Lua has many built in functions to handle graphics loading, audio loading, input, et cetera. *Most* programming languages do not have built-ins such as these.  Python and some other similiar languages have built-ins for similiar functions easily available, and SDL works well with C and C++ to do the same.

On the PSP Lua practically does the majority of the work for you, but it's just because it's designed for rapid development of Games and Simple Apps on the PSP.  Python is available on PSP as well, but as of last time I had checked it is NOT a current build and by no means is it interchange-able with the Desktop runtime environment.

Lesson #2
The Ubuntu Forums typically do not specialize in PSP programming, however we can and will help you with as many scenarios as we can.  We do ask that you post a detailed description of what you are trying to accomplish, write up clearly, be gracious when given input, and courteous when given criticism.  The majority of programming is the abstract ideas that drive the creation of the main algorithm and we CAN help you with that.

Lesson #3
Copy and Paste and direct transcription is *bad* in most scenarios.  When you read an article or tutorial, don't transcribe directly unless you're instructed to do so and be told why later.  When you read and know the material and then go back and try as much as possible without directly copying it you're more likely to retain the information.

Lesson #4
Open Source programming is a community affair.  Most programming done here at Ubuntu Forums is done in the name of Open Source Software that benefits the internet as a whole.  From personal experience I know that PSP software is roughly 50/50 on the Open Source issue. Some programs are Open Source, and some are not.  Your best bet is to find some simple Open Source PSP graphical programs and go through and read comments and try to comprehend what you are looking at.

If you have any questions or concerns, we're here to help you. Personally, I have similiar experience with the programming track you have chosen, and you can ask me anything any time and I'll respond at my earliest convenience.

Much respect and I welcome you to Ubuntu Forums if no one else has already welcomed you. :)

PS: Personally I program in C, but I know some C++. Believe me when I say, programming is slightly different on the PSP.

---


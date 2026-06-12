---
title: "SDL crash in Ubuntu"
date: 2009-12-12
forum: Programming Talk
---

### Post by BlueSorc on 2009-12-12
Hi,

I'm developing a program using the SDL libraries in the Code::Blocks IDE. Previously, I had been building it on a laptop running Windows Vista, and it has been running fine.

I've then moved the project across to my desktop running Jaunty Ubuntu. Because of code:blocks, getting the program to compile and link without any errors was fairly straightforward. The issue comes when it runs, and I get a crash.

Outputted text to the console seems to suggest that the crash is caused when I attempt to load an image file. Fiddling with the code confirms this, and I get a crash whenever I try to load an image file, whether its a BMP, PNG or JPEG, wether I'm using the IMG_Load() function from SDL_image or SDL's native LoadBMP(). I believe the crash is not caused when the program loads the image, but I believe that it simply is unable to load the image, causing an uninitialized pointer later on in the code.

I'm unfamiliar with developing on a non-windows environment, so I don't really have any idea where to start to fix this. As previously stated, the code compiles and it runs fine on Windows, so I don't believe its an issue with the code. It also links correctly, making me feel I have my linker options correct. I don't really have any idea what else to try; If anyone can even give me a starting point to Google from, it would be appreciated.

---

### Post by dwhitney67 on 2009-12-12
> **BlueSorc said:**
> ... I believe the crash is not caused when the program loads the image, but I believe that it simply is unable to load the image, causing an uninitialized pointer later on in the code.


Why don't you fix this issue?  It does not matter if you are working under Ubuntu, Windoze, or a '57 Chevy, this is an issue that should be addressed.

Never dereference a pointer unless you know that it is valid.

---

### Post by BlueSorc on 2009-12-12
Thing is that the pointer is not uninitialized in Windows. In Windows, the pointer is initialized by the LoadIMG() function. The difference is that, in Linux, this function does not seem to correctly load the image, thus it returns a null pointer, thus borking the program.

Is it possible that I should be setting my paths different in Linux? Is "Data/Images/Border.png" pointing at a different location in Linux than it is in Windows?

---

### Post by Zugzwang on 2009-12-12
> **BlueSorc said:**
> Thing is that the pointer is not uninitialized in Windows. In Windows, the pointer is initialized by the LoadIMG() function. The difference is that, in Linux, this function does not seem to correctly load the image, thus it returns a null pointer, thus borking the program.

Is it possible that I should be setting my paths different in Linux? Is "Data/Images/Border.png" pointing at a different location in Linux than it is in Windows?

So what you are saying is that you don't check for the return value of the loadImg function, which you should *always* do. See [here]("http://www.libsdl.org/projects/docs/SDL_image/SDL_image_7.html"), for example. A program should always inform the user if something unrecoverable went wrong such that the problem can be identified. If you don't want to deal with the problem and you are coding in C++, you can also throw an exception, so you at least know that something bad happened.

Note that a NULL pointer is not an uninitialised pointer. It is in fact initialised - To "0".

So I see three different possible causes of the problem:
- In Windows, you have to use "\" as path separator but in Linux it is "/".
- In Linux, you have to take care of the capitalisation of you filename. So if there is a file called "Hello.png" and your program tries to load "hello.png", the file will not be found.
- When starting the program, you are in a different directory. For example, your project might be in "/home/bluesorc/mycoolproject" but the IDE uses "/home/bluesorc" as starting path for the program. In this case, the image will of course not be found.

---

### Post by dwhitney67 on 2009-12-12
> **BlueSorc said:**
> ... thus it returns a null pointer, thus borking the program.


](*,)

Fix the code so such an event as you describe does *not* crash the program.

---

### Post by wmcbrine on 2009-12-12
The advice so far is sound, but I think what the OP would really like is to get the images working. Yes?

Make sure you have libsdl-image1.2 and libsdl-image1.2-dev installed.

---

### Post by Zugzwang on 2009-12-12
> **wmcbrine said:**
> 
Make sure you have libsdl-image1.2 and libsdl-image1.2-dev installed.

Since the OP stated that the program compiles well, I think that we can assume that these packages are already installed.

---


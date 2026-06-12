---
title: "Odd program output when using vectors in c++"
date: 2011-01-16
forum: Programming Talk
---

### Post by BlackPhantom on 2011-01-16
Hello all, sorry if this problem has been already solved.

Ok so my problem is that I am working on a game and it runs fine and all. Accept when I close out the program, the terminal prints out this long list:
```

*** glibc detected *** ./DigitalLight.out: free(): invalid next size (fast): 0x000000000175ffb0 ***
======= Backtrace: =========
/lib/libc.so.6(+0x774b6)[0x7f66186374b6]
/lib/libc.so.6(cfree+0x73)[0x7f661863dc83]
./DigitalLight.out[0x40606c]
./DigitalLight.out[0x405a72]
./DigitalLight.out[0x405212]
./DigitalLight.out[0x406a49]
/lib/libc.so.6(exit+0xe2)[0x7f66185f94f2]
/lib/libc.so.6(__libc_start_main+0x105)[0x7f66185ded95]
./DigitalLight.out[0x402069]
======= Memory map: ========
00400000-00409000 r-xp 00000000 08:06 3653707                            /home/chris/DigitalLight/DigitalLight.out
00609000-0060a000 r--p 00009000 08:06 3653707                            /home/chris/DigitalLight/DigitalLight.out
0060a000-0060b000 rw-p 0000a000 08:06 3653707                            /home/chris/DigitalLight/DigitalLight.out
0151c000-0190a000 rw-p 00000000 00:00 0                                  [heap]
7f6608000000-7f6608021000 rw-p 00000000 00:00 0 
7f6608021000-7f660c000000 ---p 00000000 00:00 0 
7f660e443000-7f660e444000 ---p 00000000 00:00 0 
7f660e444000-7f660ec44000 rw-p 00000000 00:00 0 
7f6612a1e000-7f6612a44000 r-xp 00000000 08:06 2908242                    /lib/libpng12.so.0.44.0
7f6612a44000-7f6612c43000 ---p 00026000 08:06 2908242                    /lib/libpng12.so.0.44.0
7f6612c43000-7f6612c44000 r--p 00025000 08:06 2908242                    /lib/libpng12.so.0.44.0
7f6612c44000-7f6612c45000 rw-p 00026000 08:06 2908242                    /lib/libpng12.so.0.44.0
7f6612c45000-7f6612c4a000 r-xp 00000000 08:06 574348                     /usr/lib/libXfixes.so.3.1.0
7f6612c4a000-7f6612e49000 ---p 00005000 08:06 574348                     /usr/lib/libXfixes.so.3.1.0
7f6612e49000-7f6612e4a000 r--p 00004000 08:06 574348                     /usr/lib/libXfixes.so.3.1.0
7f6612e4a000-7f6612e4b000 rw-p 00005000 08:06 574348                     /usr/lib/libXfixes.so.3.1.0
7f6612e4b000-7f6612e54000 r-xp 00000000 08:06 575745                     /usr/lib/libXrender.so.1.3.0
7f6612e54000-7f6613053000 ---p 00009000 08:06 575745                     /usr/lib/libXrender.so.1.3.0
7f6613053000-7f6613054000 r--p 00008000 08:06 575745                     /usr/lib/libXrender.so.1.3.0
7f6613054000-7f6613055000 rw-p 00009000 08:06 575745                     /usr/lib/libXrender.so.1.3.0
7f6613055000-7f661305e000 r-xp 00000000 08:06 574379                     /usr/lib/libXcursor.so.1.0.2
7f661305e000-7f661325d000 ---p 00009000 08:06 574379                     /usr/lib/libXcursor.so.1.0.2
7f661325d000-7f661325e000 r--p 00008000 08:06 574379                     /usr/lib/libXcursor.so.1.0.2
7f661325e000-7f661325f000 rw-p 00009000 08:06 574379                     /usr/lib/libXcursor.so.1.0.2
7f6613334000-7f66135d8000 r--p 00000000 08:06 590385                     /usr/lib/locale/locale-archive
7f66135d8000-7f661388b000 r-xp 00000000 08:06 575995                     /usr/lib/libvorbisenc.so.2.0.7
7f661388b000-7f6613a8a000 ---p 002b3000 08:06 575995                     /usr/lib/libvorbisenc.so.2.0.7
7f6613a8a000-7f6613aa6000 r--p 002b2000 08:06 575995                     /usr/lib/libvorbisenc.so.2.0.7
7f6613aa6000-7f6613aa7000 rw-p 002ce000 08:06 575995                     /usr/lib/libvorbisenc.so.2.0.7
7f6613aa7000-7f6613aef000 r-xp 00000000 08:06 574971                     /usr/lib/libFLAC.so.8.2.0
7f6613aef000-7f6613cef000 ---p 00048000 08:06 574971                     /usr/lib/libFLAC.so.8.2.0
7f6613cef000-7f6613cf0000 r--p 00048000 08:06 574971                     /usr/lib/libFLAC.so.8.2.0
7f6613cf0000-7f6613cf1000 rw-p 00049000 08:06 574971                     /usr/lib/libFLAC.so.8.2.0
7f6613cf1000-7f6613d08000 r-xp 00000000 08:06 2908238                    /lib/libnsl-2.12.1.so
7f6613d08000-7f6613f07000 ---p 00017000 08:06 2908238                    /lib/libnsl-2.12.1.so
7f6613f07000-7f6613f08000 r--p 00016000 08:06 2908238                    /lib/libnsl-2.12.1.so
7f6613f08000-7f6613f09000 rw-p 00017000 08:06 2908238                    /lib/libnsl-2.12.1.so
7f6613f09000-7f6613f0b000 rw-p 00000000 00:00 0 
7f6613f0b000-7f6613f10000 r-xp 00000000 08:06 575031                     /usr/lib/libXdmcp.so.6.0.0
7f6613f10000-7f661410f000 ---p 00005000 08:06 575031                     /usr/lib/libXdmcp.so.6.0.0
7f661410f000-7f6614110000 r--p 00004000 08:06 575031                     /usr/lib/libXdmcp.so.6.0.0
7f6614110000-7f6614111000 rw-p 00005000 08:06 575031                     /usr/lib/libXdmcp.so.6.0.0
7f6614111000-7f6614113000 r-xp 00000000 08:06 575651                     /usr/lib/libXau.so.6.0.0
7f6614113000-7f6614312000 ---p 00002000 08:06 575651                     /usr/lib/libXau.so.6.0.0
7f6614312000-7f6614313000 r--p 00001000 08:06 575651                     /usr/lib/libXau.so.6.0.0
7f6614313000-7f6614314000 rw-p 00002000 08:06 575651                     /usr/lib/libXau.so.6.0.0
7f6614314000-7f6614322000 r-xp 00000000 08:06 574390                     /usr/lib/libXi.so.6.1.0
7f6614322000-7f6614522000 ---p 0000e000 08:06 574390                     /usr/lib/libXi.so.6.1.0
7f6614522000-7f6614523000 r--p 0000e000 08:06 574390                     /usr/lib/libXi.so.6.1.0
7f6614523000-7f6614524000 rw-p 0000f000 08:06 574390                     /usr/lib/libXi.so.6.1.0
7f6614524000-7f6614535000 r-xp 00000000 08:06 574344                     /usr/lib/libXext.so.6.4.0
7f6614535000-7f6614734000 ---p 00011000 08:06 574344                     /usr/lib/libXext.so.6.4.0
7f6614734000-7f6614735000 r--p 00010000 08:06 574344                     /usr/lib/libXext.so.6.4.0
7f6614735000-7f6614736000 rw-p 00011000 08:06 574344                     /usr/lib/libXext.so.6.4.0
7f6614736000-7f661473a000 r-xp 00000000 08:06 2908347                    /lib/libuuid.so.1.3.0
7f661473a000-7f6614939000 ---p 00004000 08:06 2908347                    /lib/libuuid.so.1.3.0
7f6614939000-7f661493a000 r--p 00003000 08:06 2908347                    /lib/libuuid.so.1.3.0
7f661493a000-7f661493b000 rw-p 00004000 08:06 2908347                    /lib/libuuid.so.1.3.0
7f661493b000-7f661497b000 r-xp 00000000 08:06 2908284                    /lib/libdbus-1.so.3.5.2
7f661497b000-7f6614b7b000 ---p 00040000 08:06 2908284                    /lib/libdbus-1.so.3.5.2
7f6614b7b000-7f6614b7c000 r--p 00040000 08:06 2908284                    /lib/libdbus-1.so.3.5.2Aborted

```
I being a new programmer to Ubuntu have no idea as to what any of these mean, accept that they appear to be a list of memory addresses. I do use a lot of vectors in my program so I may be accessing a non-vector memory address. I have looked over my own code as best as I can and I see no places where I access a invalid vector slot. I can post my code if needed, but I would rather not. Any answers as to what this is, and/or a way to solve it would be greatly obliged.
-Chris Copeland

P.S.
Technical specifications of system/project:
 [LIST]
[*]Language:c++
[*]Other important API/Libraries: SDL && stl vector
[*]Ubuntu Distribution: 10.10 (64-bit)
[/LIST]

---

### Post by worksofcraft on 2011-01-16
I never saw one quite like that either, but what seems to have happened is that a shared library library called from another library ... etecetera is trying to free something from memory that has either already been destroyed or has been otherwise corrupted. 

It suggests it is something to do with libpng12, the png image handling runtime library. Have you tried compiling with -g switch and running it under the debugger gdb? It might give you an idea of where it is being called from in your own program.

---

### Post by BlackPhantom on 2011-01-16
I have tried using gdb, and it happens after I return from my main statement. But you said that it happens when a shared library is called from another library. I happen to be using a personal library for this project. And I do deallocate .pngs using SDL so I will check that and then keep you updated.
Thanks for responding so quickly.
-Chris Copeland

---

### Post by BlackPhantom on 2011-01-16
After further testing, I still haven't removed it. I tried directly including my library in my code, without use of libraries that is. Still get the output. It also seems that I get this problem on a somewhat random basis. It will happen on some runs and not on others. All the times I did similar actions, and run for a similar amount of time. As to my code for removing .pngs is very simple and is it is impossible to access invalid units. So I guess that either leaves corruption of some form, or some other outside source.

---

### Post by worksofcraft on 2011-01-16
> **BlackPhantom said:**
> After further testing, I still haven't removed it. I tried directly including my library in my code, without use of libraries that is. Still get the output. It also seems that I get this problem on a somewhat random basis. It will happen on some runs and not on others. All the times I did similar actions, and run for a similar amount of time. As to my code for removing .pngs is very simple and is it is impossible to access invalid units. So I guess that either leaves corruption of some form, or some other outside source.

It looks like it is something being done in a destructor that gets run on program exit.

One thing you could try... just as a test to see if it is related... not as a solution, is to deliberately NOT remove the png perhaps?

---

### Post by BlackPhantom on 2011-01-16
I still get it, even though I commented out the .png removal function. I am not sure what else it could be.
-Chris Copeland

---

### Post by BlackPhantom on 2011-01-16
More gdb test seem to show now that my program creates the output after I deallocate the .pngs. I don't know why it didn't happen the same way before. I added in some extra code to make sure I don't deallocate a null .png and I still get the output. So honestly I am clueless...
-Chris Copeland

---

### Post by MadCow108 on 2011-01-16
valgrind is the tool to find these kind of errors.

gdb will not tell you directly where you mess up the memory in a non fatal way, valgrind will.
setting the environment _MALLOC_CHECK to 2 can also help sometimes.

---

### Post by nvteighen on 2011-01-16
That output is the one you get from a faulty dynamic deallocation. As MadCow108 has told you, use valgrind, which is a memory debugger (install it from the repos).

Possible causes:
0. You're attempting to delete memory using an invalid pointer.
1. You're attempting to delete an object more than once.
2. You're mixing C allocation functions (malloc/realloc/free) with C++ new/delete. (rare)

---

### Post by MadCow108 on 2011-01-16
no the error is not a double or invalid free in the user code.

These errors indicate corruption of the internal data structure of the memory allocator by the user.
The debugging mechanisms in the allocator are able to detect corruption to a certain extent and will print out errors of this type at certain sequence points (e.g. calls to free or malloc). That why the point of crash is rarely connected to the actual point of corruption making gdb an inadequate tool for this.

The corruption can happen anywhere in your code and not just in your allocations and deallocations.
The main cause are buffer overflows (valgrind will detect these)

---

### Post by BlackPhantom on 2011-01-16
Ok I used valgrind to find the faulty function. It seems that it happens when I use SDL to load a .png. The output of valgrind was:
```

==3260== Memcheck, a memory error detector
==3260== Copyright (C) 2002-2010, and GNU GPL'd, by Julian Seward et al.
==3260== Using Valgrind-3.6.0.SVN-Debian and LibVEX; rerun with -h for copyright info
==3260== Command: /home/chris/DigitalLight/DigitalLight
==3260== 
==3260== Conditional jump or move depends on uninitialised value(s)
==3260==    at 0x7386E40: inflateReset2 (in /lib/libz.so.1.2.3.4)
==3260==    by 0x7386F2F: inflateInit2_ (in /lib/libz.so.1.2.3.4)
==3260==    by 0xBDC14AF: png_create_read_struct_2 (in /lib/libpng12.so.0.44.0)
==3260==    by 0xBDC1646: png_create_read_struct (in /lib/libpng12.so.0.44.0)
==3260==    by 0x50C9408: IMG_LoadPNG_RW (in /usr/lib/libSDL_image-1.2.so.0.8.2)
==3260==    by 0x50C528B: IMG_LoadTyped_RW (in /usr/lib/libSDL_image-1.2.so.0.8.2)
==3260==    by 0x5750ED0: image_manager::newImage(std::string, std::string) (CMC_Image.cpp:12)
==3260==    by 0x4041C9: init() (main.cpp:476)
==3260==    by 0x40212C: main (main.cpp:53)
==3260== 
^[^[==3260== 
==3260== HEAP SUMMARY:
==3260==     in use at exit: 148,191 bytes in 1,372 blocks
==3260==   total heap usage: 69,750 allocs, 68,378 frees, 24,065,231 bytes allocated
==3260== 
==3260== LEAK SUMMARY:
==3260==    definitely lost: 42 bytes in 3 blocks
==3260==    indirectly lost: 176 bytes in 4 blocks
==3260==      possibly lost: 8,176 bytes in 1 blocks
==3260==    still reachable: 139,797 bytes in 1,364 blocks
==3260==         suppressed: 0 bytes in 0 blocks
==3260== Rerun with --leak-check=full to see details of leaked memory
==3260== 
==3260== For counts of detected and suppressed errors, rerun with: -v
==3260== Use --track-origins=yes to see where uninitialised values come from
==3260== ERROR SUMMARY: 10 errors from 1 contexts (suppressed: 38 from 8)

```
I figured that the code was faulty was this (I included line numbers):
```

9  bool image_manager::newImage(string file,string name)
10 {
11	image.push_back(image_element());
12	image[image.size()-1].image=IMG_Load(file.c_str());
13	image[image.size()-1].file=file;
14	image[image.size()-1].name=name;
15	if(image[image.size()-1].image!=NULL)
16		return true;
17	else
18		return false;
19 }

```
The function arguments are:
```

476 IM.newImage("player.png","player");

```
I checked and the .png is there and named exactly the same as above. So I don't know what the problem could be. Any more help will be greatly appreciated.
-Chris Copeland

---

### Post by MadCow108 on 2011-01-16
the uninitialized jump in libz is a false positive. Its documented in their faq somewhere, so no need to investigate any furthere there.

Is that all output of a complete runthrough?
its weird, I would have expected an error of the type *invalid write*

---

### Post by dwhitney67 on 2011-01-16
> **BlackPhantom said:**
>  I can post my code if needed, but I would rather not. Any answers as to what this is, and/or a way to solve it would be greatly obliged.


If you don't want to post your code, then it it going to be tricky to get some quality help.  Most, if not all, of the participants on this forum are not clairvoyant or even psychic.  Thus it will be difficult for us to troubleshoot code we cannot see.

However, gleaning some information from the code snip you did offer, I would say that there is lots of room for improvement in your code.  A couple of things I would suggest is to avoid making unnecessary copies of class objects, and also to place code to initialize objects in the proper place.

Here's some code I tinkered with (by reverse-engineering your code snip), and that successfully loads four images:
```

#include <SDL/SDL.h>
#include <SDL/SDL_image.h>

#include <vector>
#include <string>
#include <iostream>

#include <cassert>


struct ImageElement
{
   ImageElement(const std::string file, const std::string& name)
      : image(IMG_Load(file.c_str())),
        imageFile(file),
        playerName(name)
   {
   }

   ~ImageElement()
   {
      if (image)
      {
         SDL_FreeSurface(image);
      }
   }

   SDL_Surface* image;
   std::string  imageFile;
   std::string  playerName;
};

class ImageManager
{
public:
   ImageManager()
   {
      IMG_Init(IMG_INIT_JPG | IMG_INIT_PNG | IMG_INIT_TIF);
   }

   ~ImageManager()
   {
      for (std::vector<ImageElement*>::iterator it = images.begin(); it != images.end(); ++it)
      {
         delete *it;
      }

      IMG_Quit();
   }

   bool newImage(const std::string& file, const std::string& name)
   {
      images.push_back(new ImageElement(file, name));  // note how I store a pointer to an ImageElement.

      return images.back()->image != 0;
   }

private:
   std::vector<ImageElement*> images;
};

int main()
{
   ImageManager imgr;

   assert(imgr.newImage("image001.jpg", "player1") == true);
   assert(imgr.newImage("image002.jpg", "player2") == true);
   assert(imgr.newImage("image003.jpg", "player3") == true);
   assert(imgr.newImage("image004.jpg", "player4") == true);
}

```

---

### Post by BlackPhantom on 2011-01-16
Well if you truly need to see my code, then here is the relevant code:
```

class image_manager
{
private:
	class image_element
	{
	public:
		image_element()
		{
			image=NULL;
			name=" ";
			file=" ";
		}
		SDL_Surface *image;
		string name,file;
	};
	SDL_Surface *background;
	bool tiled,backgroundExists,flipInFunction;
	vector <image_element> image;
public:
	image_manager();
	bool newImage(string file,string name);
	void cleanUp();
};

image_manager::image_manager()
{
	background=NULL;
	tiled=false;
	backgroundExists=false;
	flipInFunction=false;
}
bool image_manager::newImage(string file,string name)
{
	image.push_back(image_element());
	image[image.size()-1].image=IMG_Load(file.c_str());
	image[image.size()-1].file=file;
	image[image.size()-1].name=name;
	if(image[image.size()-1].image!=NULL)
		return true;
	else
		return false;
}
void image_manager::cleanUp()
{
	for(int i=0;i<image.size();i++)
		if(image[i].image!=NULL)
			SDL_FreeSurface(image[i].image);
	return;
}

```
If you need anymore just ask.
-Chris Copeland

---

### Post by dwhitney67 on 2011-01-17
Your code ran fine, although it could stand some improvement.

Here's a laundry list of things you could improve on:

1.  When passing a string to a function, pass it by reference unless you have a damn good reason to pass it by value.  Passing by value makes a copy of the string, and this will impact performance.

2.  When you initialize a class via the constructor, the area known as the body of the constructor is NOT where initialization should take place.  For example, take image_element:
```

class image_element
{
public:
   image_element()
     : image(NULL)   // this is where you initialize values
   {
      // nothing to be done here.
      // members 'file' and 'name' have already been initialized!
   }

   ...
};

```

3.  Cleanup of your SDL images should be done within the object that manages the image.  In other words, implement a destructor for image_element that calls SDL_FreeSurface() for the image is manages; don't implement a "cleanup" function in image_manager.

4.  In newImage(), the following code is creating TWO copies of image_element; one that you see in the statement below, the other that gets stored in the vector when you call push_back().
```

image.push_back(image_element());

```
Consider storing an allocated image_element object; that way you only create one object (on the heap).

5.  Again in newImage(), implement a better constructor for image_element that accepts the parameters necessary to fully construct the object.  Your current approach is to construct a dummy object (twice!), and then fill in the "blanks" afterwards.

Refer to my previous post to see if you can glean some ideas.  As for your current code, as I stated earlier, it works fine, although you should clean up any compiler warnings.  Use -Wall when you compile!

---

### Post by BlackPhantom on 2011-01-17
Thanks for all your input. As you can tell I am still a novice programmer so any help I can get is great. As to the error I think it is probably what MadCow108 said before with the answer in the faq. But still thank you greatly for looking at my code.
-Chris Copeland

---


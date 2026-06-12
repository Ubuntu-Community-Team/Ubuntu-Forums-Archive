---
title: "[SOLVED] class in a struct in a vector problem c++"
date: 2008-04-08
forum: Programming Talk
---

### Post by paukku92 on 2008-04-08
I have a problem in c++ that occurs after my program stops running, the program runs perfectly until i decide to shut it. I press esc and following error message turn up:

*** glibc detected *** ./rally: double free or corruption (out): 0x0817dd40 ***

I tested it with valgrind and got to know that the error occurs when its trying to free a object that is in a struct stored in a vector. Freeing other objects of the same class goes with no errors, but they are not stored in vectors. 

Some code/output:
Valgrind:
```
MR2.png (Not in a vector)
./Data/Images/gauge.png (Not in a vector)
./Data/Maps/Testing/bricks.png (Not in a vector)
./Data/Images/font.png (Not in a vector)
./Data/Maps/Testing/asphalt.png  (In a vector)
==7797== Invalid free() / delete / delete[]
==7797==    at 0x4020D18: operator delete[](void*) (vg_replace_malloc.c:256)
==7797==    by 0x805071E: Graphics::FreeImage() (graphics.cc:185)
==7797==    by 0x80507B2: Graphics::~Graphics() (graphics.cc:259)
==7797==    by 0x804ED85: TextureStruct::~TextureStruct() (engine.hh:70)
==7797==    by 0x804EDC4: void std::_Destroy<TextureStruct>(TextureStruct*) (stl_construct.h:107)
==7797==    by 0x804EDDA: void std::__destroy_aux<TextureStruct*>(TextureStruct*, TextureStruct*, __false_type) (stl_construct.h:122)
==7797==    by 0x804EE0B: void std::_Destroy<TextureStruct*>(TextureStruct*, TextureStruct*) (stl_construct.h:155)
==7797==    by 0x804EE25: void std::_Destroy<TextureStruct*, TextureStruct>(TextureStruct*, TextureStruct*, std::allocator<TextureStruct>) (stl_construct.h:182)
==7797==    by 0x804EE66: std::vector<TextureStruct, std::allocator<TextureStruct> >::~vector() (stl_vector.h:272)
==7797==    by 0x804C635: __tcf_1 (engine.cc:31)
==7797==    by 0x4366593: exit (in /lib/tls/i686/cmov/libc-2.6.1.so)
==7797==    by 0x804B805: quit(int) (utils.cc:30)
==7797==  Address 0x638CBF8 is 0 bytes inside a block of size 196,608 free'd
==7797==    at 0x4020D18: operator delete[](void*) (vg_replace_malloc.c:256)
==7797==    by 0x805071E: Graphics::FreeImage() (graphics.cc:185)
==7797==    by 0x80507B2: Graphics::~Graphics() (graphics.cc:259)
==7797==    by 0x804ED85: TextureStruct::~TextureStruct() (engine.hh:70)
==7797==    by 0x804CC16: LoadMap(std::string) (engine.cc:84)
==7797==    by 0x804AD19: main (main.cc:179)

```
Graphics::FreeImage()
(Pixels is a char pointer)
```
if(Pixels)
	{
		delete[] Pixels;
		Pixels=NULL;
		Width=0;
		Height=0;
		BitDepth=0;		//Number of bytes for each pixel
		Width=0;		//Width of the image
		Height=0;		//Height of the image
	}
```

---

### Post by Zugzwang on 2008-04-08
Hard to say what's the cause with seeing only such a small snipplet, but one common cause for these type of error is that you haven't declared a copy-constructor for your "Graphics" class but it is implicitly used somewhere so the compiler uses a bit-wise default copy operator which doesn't duplicate the "Pixels" as well.

Try to add a copy constructor which is private and throws an exception whenever it is called. See if an exception is thrown at runtime. If it is, then that's you problem.

Probably you may need to do that for the overloaded assignment operator as well, but I'm not sure.

---

### Post by paukku92 on 2008-04-08
Ok, copy is really made. And i can understand now why the error occurs.

The original object is destroyed right away but the object in the vector still points to the memory allocated by the object just destroyed. When the program stops, it tries to free the same memory, but TADAA, it fails. Thank you a lot for help.

---


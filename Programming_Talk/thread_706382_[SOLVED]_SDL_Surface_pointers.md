---
title: "[SOLVED] SDL_Surface pointers"
date: 2008-02-24
forum: Programming Talk
---

### Post by Zeotronic on 2008-02-24
For a while now I have been wondering about why SDL_Surfaces always return pointers for everything. Why does SDL always give me pointers to the surfaces? I've tried to find it on the site, but if its there I couldn't find it. I think that I would rather handle the surfaces myself, but I should know more about it before I mess with that. Does anyone know anything about the inner workings of the SDL_Surface? I really don't want to dig through the source code, I've got my own project to work on, I don't want to crawl through someone else's... at the moment.

---

### Post by slavik on 2008-02-24
What would you like SDL to give you???

SDL is another example of OO in a language that doesn't explicitly have it. :)

---

### Post by Zeotronic on 2008-02-24
> What would you like SDL to give you???
I dunno, a SDL_Surface? O.o

---

### Post by slavik on 2008-02-24
SDL_Surface is a structure. :)

Don't forget that SDL is written in C. :)

---

### Post by Zeotronic on 2008-02-24
> SDL_Surface is a structure.

Don't forget that SDL is written in C. 
Yes, I know this. Perhaps I am not grasping what your trying to say, but you dont seem to be particularly helpful. Of course an SDL_Surface is a structure... how could it be anything else? Here, perhaps it would be more productive of me to ask what SDL does with the surfaces that it sends me pointers to? I am trying to figure these things out because in more than one occasions I have needs for SDL surfaces that are single use only, and I'm incredibly worried about KILLING them after their use, for I have had problems in the past where it hadn't occured to me, and they overpopulated the RAM.

---

### Post by slavik on 2008-02-24
one thing you have to keep in mind is that an SDL_Surface might be somehow stored in the video hardware (if you use OPENGL or the HW_SURFACE flags).

as for why only pointers get returned, this is a standard C OO way. in C++/Java/Python/Perl/Ruby/etc. you get references, in C you get pointers. :)

Also, pointers are at most 8 bytes, while a structure might be much larger and part of the SDL_Surface is the pixels array which is allocated separately when the SDL_Surface is being created).

from SDL_video.h
```

typedef struct SDL_Surface {
	Uint32 flags;				/* Read-only */
	SDL_PixelFormat *format;		/* Read-only */
	int w, h;				/* Read-only */
	Uint16 pitch;				/* Read-only */
	void *pixels;				/* Read-write */
	int offset;				/* Private */

	/* Hardware-specific surface info */
	struct private_hwdata *hwdata;

	/* clipping information */
	SDL_Rect clip_rect;			/* Read-only */
	Uint32 unused1;				/* for binary compatibility */

	/* Allow recursive locks */
	Uint32 locked;				/* Private */

	/* info for fast blit mapping to other surfaces */
	struct SDL_BlitMap *map;		/* Private */

	/* format version, bumped at every change to invalidate blit maps */
	unsigned int format_version;		/* Private */

	/* Reference count -- used when freeing surface */
	int refcount;				/* Read-mostly */
} SDL_Surface;
```

notice how there are many pointers (to be allocated when the surface is created). this would make returning structures difficult since there is no deep copy in C for structs. :)

---

### Post by Zeotronic on 2008-02-24
While I am understanding clearly your posts, I cannot manage to grasp their usefulness... however, it does not matter, because I now remember how I overcame my problems the first time. Thank you for trying.

---

### Post by Lux Perpetua on 2008-02-24
This practice is not at all unique to SDL. It's customary to pass around pointers to structures rather than structures themselves; I almost never see the latter. In fact, if you find a function that appears to return any sort of nontrivial data type and not a pointer to it, chances are that data type is itself implemented as an **opaque pointer** (i. e., the type is really just a pointer to a structure that your code is not supposed to see). 

There is more than one reason for this. One reason is that if a library lets you handle a structure itself, rather than through pointers to it, then it has only two options: (1) commit to its current implementation of that structure and never change it, or (2) force you to recompile your client code every time an update to the library changes the implementation of that structure. The first option is restrictive on the maintainer of the library, and the second option is annoying for the user of the library. However, if you design your library so that client code only sees pointers to your structures, then both you and your clients are happy. 

Another reason is that the C language has "value" semantics and not "reference" semantics. This means that if you have a variable of any type and you need to give it to anybody else (examples: passing data to a function, returning something from a function, simply doing assignments), then unless you explicitly give a pointer to that variable, the other guy gets his own full copy of the variable. This is problematic because (1) copying a large structure just for the data to be seen in multiple places is a big waste of time and memory, and (2) copying a structure in C just copies its data fields byte for byte, which ignores the actual semantics of the type and is usually just plain wrong, so even if you really did want to copy the whole thing, this wouldn't do it properly!

Note that C++ doesn't have the second problem of the last paragraph because it allows you to write copy constructors that enforce proper copying of your data. C++ also introduces reference types which have reference semantics, not value semantics, so that the same object can be referred to in multiple places without explicitly using pointers.

---

### Post by cb951303 on 2008-02-24
if you define a local variable inside a function, you can't return it or its address because once the function terminates, locally created variables no longer exist.

but if you dynamically allocate memory inside the function (meaning you create a variable of desired size at run-time) you can return its address because that variable exists even after the function terminates. And it will be accessible by its address from anywhere.

I hope it doesn't confuse you more ...

---


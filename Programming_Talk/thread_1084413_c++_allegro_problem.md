---
title: "c++ allegro problem"
date: 2009-03-02
forum: Programming Talk
---

### Post by nzadLithium on 2009-03-02
Using C++ and allegro library.

I have a header file, in it I have:
```
#include <allegro.h>

typedef struct _character_images 
{
	BITMAP* face;
	BITMAP* characterfront[10];
} character_images;
```

I then call try to create a variable of this type from another source files (the header is included), like this:
```
character_images characterimages;
```

On compiling I receive:
characterselect.h:12: error: expected unqualified-id before numeric constant

This error is referring to the line BITMAP* face;

What am I doing wrong, and how do I fix it? XP

Thanks :)

---

### Post by Liviu-Theodor on 2009-03-02
There is a limit of how many include levels you can use, I think is 10. Maybe you reached that limit, if you say you did include all the stuff in a header file. Or maybe you need to define a project.

---

### Post by nzadLithium on 2009-03-02
The situation with the includes is:

file.cpp does #include <allegro.h> and #include "file.h"
file.h then has the code you saw before.

I just tried shifting my file.h include to be included first, then not include allegro.h as it is included via file.h. It seems to compile and program runs.

Must not like me including the same header twice through a header file? XP

---

### Post by Liviu-Theodor on 2009-03-02
Indeed you must include a header only once per file using it, so pay attention.

---

### Post by nzadLithium on 2009-03-02
hmm problem is not entirely fixed yet :S

header file remains the same.

creating the variable I am now doing like this:

```
character_images characterimages[50];
```

I then do:
```
characterimages[i]->face = load_bitmap(filepath, NULL);
```
where filepath is the location of a file.

And now I have this kind compiler output :S The last error repeats many times with the line number increasing (ie fix.inl:69 fix.inl:70 etc).
Damn writing this program has made me start pressing ';' when ending sentences. XP

```
characterselect.cpp:86: error: base operand of ‘->’ has non-pointer type ‘character_images’
characterselect.cpp:86: error: expected unqualified-id before numeric constant
characterselect.cpp:86: error: expected `;' before numeric constant
characterselect.cpp:87: error: no match for ‘operator==’ in ‘characterimages[i] == 0l’
/usr/include/allegro/inline/fix.inl:68: note: candidates are: int operator==(fix, fix)

```

---

### Post by lloyd_b on 2009-03-02
Shouldn't```
characterimages[i]->face = load_bitmap(filepath, NULL);
```be```
characterimages[i].face = load_bitmap(filepath, NULL);
```?

The former would be appropriate if you had defined characterimages as a "struct *character_images[50]"...

Lloyd B.

---

### Post by nzadLithium on 2009-03-02
hmm well that is getting closer, it got rid of all the error about using -> but all the others still remain :S

I then changed the header file so the struct is like:

```
typedef struct _character_images 
{
	BITMAP* face;
	BITMAP* characterfront[10];
} *character_images;
```

now I only have two errors, but they're the ones I started with XP

```
characterselect.cpp:75: error: expected unqualified-id before numeric constant
characterselect.cpp:75: error: expected `;' before numeric constant
```

whole header file goes like this:

```
#include <allegro.h>

#ifndef _START_H
#define _START_H

int characterselect_routine();

typedef struct _character_images 
{
	BITMAP* face;
	BITMAP* characterfront[10];
} *character_images;

#endif
```

Relevant code sections:

```

character_images characterimages[50];
struct dirent **dirlist;

...
//retrieved directory list in dirent structure here
...

for (int i=0; i<(filecount); i++)
{
	char filepath[266];
	strcpy(filepath, "characters/");
	strcat(filepath, dirlist[i]->d_name); //this is line 75
	printf("modellocation: %s ", filepath);
	characterimages[i].face = load_bitmap(filepath, NULL);
	if (characterimages[i].face == NULL)
	{
		printf("Loading %s failed. Check permissions, check file exists.",  filepath);
		exit(EXIT_FAILURE);
	}
}

```

I commented line 75 in the source so you can see where the error happens.

---

### Post by lloyd_b on 2009-03-02
Err, that change you made is a segfault looking for a place to happen - you're never allocating actual memory for that array, just a bunch of pointers.  Try the code change I mentioned above (changing "->" to "."), as with that example you were properly allocating memory for the array of structures, just not accessing it correctly.

I can't tell exactly what's wrong with line 75, since I can't see how you're loading dirlist[], but I *suspect* it's another case of using "->" where you should be using ".".

Remember, "var1->var2" means "access var2 from the structure pointed to by var1", while "var1.var2" means "access var2 from the structure var1"

Lloyd B.

---

### Post by nzadLithium on 2009-03-02
oh woops :S

That wasn't line 75 XP 

line 75 is this one :S 

```
characterimages[i].face = load_bitmap(filepath, NULL);
```

lol sry that was pretty fail XP

I will change the header back to how it was.

the dirlist stuff works fine, i've had it working for ages :D

so source is like this:

header:
```
#include <allegro.h>

#ifndef _START_H
#define _START_H

int characterselect_routine();

typedef struct _character_images 
{
	BITMAP* face;
	BITMAP* characterfront[10];
} character_images;

#endif
```

```
character_images characterimages[50];
struct dirent **dirlist;

...
//retrieved directory list in dirent structure here
...

for (int i=0; i<(filecount); i++)
{
	char filepath[266];
	strcpy(filepath, "characters/");
	strcat(filepath, dirlist[i]->d_name); 
	printf("modellocation: %s ", filepath);
	characterimages[i].face = load_bitmap(filepath, NULL); //this is line 75
	if (characterimages[i].face == NULL)
	{
		printf("Loading %s failed. Check permissions, check file exists.",  filepath);
		exit(EXIT_FAILURE);
	}
}
```

And errors are:

```
characterselect.cpp: In function ‘void draw_characterselect(int, int, int, int, int)’:
characterselect.cpp:75: error: expected unqualified-id before numeric constant
characterselect.cpp:75: error: expected `;' before numeric constant
characterselect.cpp:76: error: expected unqualified-id before numeric constant
characterselect.cpp:76: error: expected `)' before numeric constant
make: *** [all] Error 1

```

I marked the correct line 75 now :p

Sry for my failness XP

---

### Post by lloyd_b on 2009-03-02
I did a quick Google on that error - every instance I can find is a result of accidentally duplicating a symbol name...

Try changing the name of the typedef "character_images" and see if that has any effect.

Lloyd B.

---

### Post by nzadLithium on 2009-03-03
Tried adding a 5 on the end. It hasn't made a difference. Sorry for taking so long to reply, had to go to bed, then I was out all of yesterday. :)

---

### Post by nzadLithium on 2009-03-04
Well problem is fixed, turns out the names for variables inside the structure I was already using in some other header files... Damn i'm stupid XP Thx for the help lloyd_b :D

---


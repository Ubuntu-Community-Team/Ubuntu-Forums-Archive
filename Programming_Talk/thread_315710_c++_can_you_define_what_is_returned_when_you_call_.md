---
title: "c++ can you define what is returned when you call a struct???"
date: 2006-12-09
forum: Programming Talk
---

### Post by Choad on 2006-12-09
so for example if i wanted a sprite struct, that contained not only the sprite image but the number of frames etc. but i want the sprite struct to behave like an SDL_Surface for the most part..... example

struct Sprite
{
SDL_Surface * sprite;
int numberOfFrames;
}

Sprite * mySprite;

mySprite = LoadImage("bla.png");

mySprite->numberOfFrames = 5;


is this possible? because i seem to remember seeing something similar before

---

### Post by skirkpatrick on 2006-12-09
> **Choad said:**
> so for example if i wanted a sprite struct, that contained not only the sprite image but the number of frames etc. but i want the sprite struct to behave like an SDL_Surface for the most part..... example

struct Sprite
{
SDL_Surface * sprite;
int numberOfFrames;
}

Sprite * mySprite;

mySprite = LoadImage("bla.png");

mySprite->numberOfFrames = 5;


is this possible? because i seem to remember seeing something similar before


Change to **mySprite->sprite = LoadImage("bla.png");**

---

### Post by Choad on 2006-12-09
> **skirkpatrick said:**
> Change to **mySprite->sprite = LoadImage("bla.png");**
yeah thats the point, can i avoid doing thayt?

at the moment everything is stored as an SDL_Image, but i want to change their type to my own struct Sprite, but not have to re write all the code

---

### Post by duff on 2006-12-09
if you just need it for assignment:
```

#include <iostream>

struct Foo
{
   int x;
   float y;
   Foo &operator=(int z)
   {
      x=z;
      return *this;
   }
};

int main()
{
   Foo f;
   f.y = 3.14;
   f = 4;
   std::cout << f.x << "\t" << f.y << std::endl;
}
```

---

### Post by Choad on 2006-12-09
> **duff said:**
> if you just need it for assignment:
```

#include <iostream>

struct Foo
{
   int x;
   float y;
   Foo &operator=(int z)
   {
      x=z;
      return *this;
   }
};

int main()
{
   Foo f;
   f.y = 3.14;
   f = 4;
   std::cout << f.x << "\t" << f.y << std::endl;
}
```
what if i need it for more than asignment? (thanks tho.... its along the right lines of what i was looking for)

---

### Post by Wybiral on 2006-12-09
What other than assignments would you be wanting? You can always use a class.

---

### Post by Choad on 2006-12-09
> **Wybiral said:**
> What other than assignments would you be wanting? You can always use a class.
for example

```

SDL_BlitSurface(sprite, 
		NULL, 
		screen, 
		&rectTemp);

```

where sprite is a "Sprite" struct, but the function "SDL_BlitSurface" requires a struct of type "SDL_Surface" to be passed to it

and i am up for a class, if you would explain how to achieve what i am wanting :)

---

### Post by Wybiral on 2006-12-09
So you need to pass an object of type SDL_Surface to SDL_BlitSurface? Can't you just use:

```

SDL_BlitSurface(mySprite.sprite, 
		NULL, 
		screen, 
		&rectTemp);

```

Or am I misinterpreting this?

---

### Post by Choad on 2006-12-09
yeah, i could, but i dont want to :P

this isnt an end of the world scenario if its not possible, i just thought it was possible and would save me altering a load of code

---

### Post by Wybiral on 2006-12-09
Hmm... Not as far as I know. But then again, C++ is always surprising me.

---

### Post by duff on 2006-12-09
never underestimate C++
```
#include <iostream>

struct Foo
{
   int x;
   float y;
   Foo &operator=(int z)
   {
      x=z;
      return *this;
   }
   Foo &operator=(double z)
   {
      y=z;
      return *this;
   }
};

int main()
{
   Foo f;
   f = 3.14;
   f = 4;
   std::cout << f.x << "\t" << f.y << std::endl;
}
```

runing:```
./a.out 
4       3.14
```

---

### Post by Choad on 2006-12-09
what!?

that doesnt help me :(

---

### Post by Wybiral on 2006-12-09
Actually... Duff brings up a good point! You could write a wrapper for it.

```

void SDL_BlitSurface(Sprite thisSprite){
    SDL_BlitSurface(thisSprite.sprite, NULL, screen, &rectTemp);   
}

```

I didn't fill in the argument types for the wrapping function because I didn't know what they were supposed to be, but something like that would work because C++ allows you to use the same function name for two functions with different parameters!

---

### Post by duff on 2006-12-09
mis-understood what you wanted.  i thought you needed different assigment operators.  maybe this is what you want..

```

#include <iostream>

struct Foo
{
   int x;
   float y;
   operator int () { return x; }
   operator float () { return y; }
};

void foo (int x) { std::cout << x << std::endl; }
void bar (double x) { std::cout << x << std::endl; }

int main()
{
   Foo f;
   f.y = 3.14;
   f.x = 4;
   foo (f);
   bar (f);
}
```

---

### Post by skirkpatrick on 2006-12-09
What he wants to do is overload an existing structure.  Which you can do for classes but not structures.

I use SDL and C++ in some of the stuff I'm doing.

Either write your own class or do what Wybiral suggested.

---

### Post by duff on 2006-12-09
> **skirkpatrick said:**
> What he wants to do is overload an existing structure.  Which you can do for classes but not structures.

WTF? In C++ structs and classes are the exact same thing.  The only difference is the default accessibility in a struct is public, while class's default accessibility is private.  That's it.

---

### Post by Wybiral on 2006-12-09
I think his main problem is that he is using a pre-written function (part of the SDL library) and he can't change the way it inputs his arguments. Personally, I think it would be easiest to just write a function to wrap around the SDL function (similar to the example above)

---

### Post by Jengu on 2006-12-10
I think the best question is: **Why** are you trying to do this? Give us a more general idea of the problem. You say you want it to avoid having to rewrite a lot of code, but why would you want to rewrite it in the first place?

---


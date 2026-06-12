---
title: "Problems with SDL_Surface struct (in C)"
date: 2008-03-26
forum: Programming Talk
---

### Post by POW R TOC H on 2008-03-26
I want to draw pixels directly to the surface, so I simply use an pointer to point on pixel data like this :
```

//Let's assume I already loaded the image into a surface called 'pic', I
//loaded a PNG.

unsigned char pixel_pointer;
pixel_pointer = (unsigned char*)pic->pixels;

```

Now, let's say I want to fill a rectangle (yes, I know there are functions for that, this is only an example), I should simply be able to do this :

```

int i;
for (i = 0 ; i < (pic->w * pic->h) ; i++ )
{
//I am using 24 bits per pixel, so I need to fill only 3 bytes of data 
//for colors, no alpha...
*pixel_pointer = 0;
pixel_pointer ++;
*pixel_pointer = 255;
pixel_pointer ++;
*pixel_pointer = 0;
pixel_pointer ++;
}

```
This should do, right? No... Here's the problem : in every next row, colors shift differently, by a linearly growing amount of pixels. This led me to believe that there are unused pixels, just like in a .bmp file. I expected the info on how much pixels are unused to be in pic->unused, but it's not (turns out to be zero always, which doesn't explain the problem...)

So, can anyone give me an example of pixel manipulation on surfaces in SDL?
Thank you in advance...

---

### Post by uzusan on 2008-03-26
I think this might help - [http://lazyfoo.net/SDL_tutorials/lesson31/index.php](http://lazyfoo.net/SDL_tutorials/lesson31/index.php)

---

### Post by POW R TOC H on 2008-03-26
But I need to acces 8 bit chunks of the array, not 32 bit chunks. That way I can easily manipulate R G and B values of each pixel... Unless you have a better idea :D
Let's say I want to use 32 bpps. I would need to create an 32 bits integer whose 8 bits chunks represent each of the colors + alpha (I must use it, since it's 32 bits long)
How do I do this?
Please help, I'm a bit new to SDL... And yes, I am using Lazy Foo's tuts, they're amazing :D

---

### Post by POW R TOC H on 2008-03-26
And another question... My compiler (GCC) doesn't reckognise Uint32 as a data type! I included ctypes.h... What's the deal?

---

### Post by mike_g on 2008-03-26
Its strange that Uint32 is not recognised, I thought it was defined in SDL.h ???
Still you can always define it yourself:
```
#ifndef Uint32
#define Uint32 unsigned long
#endif
```
As for reading pixels, I didit something like:
```
Uint32 ReadPixel(int x, int y)
{
    return (Uint32)screen->pixels+(x+y*GRAPHICS_WIDTH)*4;
} 
```
It dosent do any bounds checking though, so if you read out of buffer its likely to crash.

I then tend to extract the colour components using bit shifting and masking. something like:
```
Uint8 GetRed(Uint32 col)
{
    return (col >> 16) & 255;
}
Uint8 GetGrn(Uint32 col)
{
    return (col >> 8) & 255;
}
Uit8 GetBlu(Uint32 col)
{
    return col & 255;
}
```
You can of course read colour components directly as bytes, just remember that the Byte ordering goes ARGB.

---

### Post by POW R TOC H on 2008-03-26
I understand that, but thank you. I need help with something else...
Say I have four values (RGB + A) which are in type unsigned char, and I want to copy all 4*8 bits to 32 bit unsigned integer...
I need a pointer that points to a group of 8 bits in a 32 bit variable (I need to access a char in an int :D )
Is there a way to do this?

---

### Post by mike_g on 2008-03-26
The get component functions I posted do what you are asking for. They extract an 8bit component value from a 32bit unsigned colour value.

Edit: sorry I misrad your post. Maybe you need something like:
```
Uint32 ToARGB(Uint8 a, Uint8 r, Uint8 g, Uint8 b)
{
    return (a<<24)+(r<<16)+(g<<8)+b;
}
```

---

### Post by POW R TOC H on 2008-03-26
Thank you so much! Where's the damn 'thanks' button..? Ahh, here it is!

---


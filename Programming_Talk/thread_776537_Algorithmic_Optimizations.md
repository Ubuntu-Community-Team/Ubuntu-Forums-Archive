---
title: "Algorithmic Optimizations"
date: 2008-04-30
forum: Programming Talk
---

### Post by Thorjelly on 2008-04-30
I am writing a diametric tile engine in C++ using the SDL library. I am pretty new at C++, having migrated from higher level languages like Python, and am still trying to figure out the nooks and crannies. Specifically, I am starting to optimize my drawing routine a bit (despite probably having better things to do, like actually adding more features hehe). Well anyway, here is my old DrawScene() function:

```
void DrawScene() {
  SDL_FillRect(screen, NULL, SDL_MapRGB(screen->format,0,0,0));

  // center the level on the screen

  int pw = SCREEN_WIDTH / 2 - (TILE_WIDTH + TILE_X_OFF) / 2 -
           (MyLevel.Width() * TILE_WIDTH - MyLevel.Depth() * TILE_X_OFF) / 2;
  int ph = SCREEN_HEIGHT / 2 - (TILE_HEIGHT + TILE_Y_OFF) / 2 -
           (MyLevel.Width() * TILE_Y_OFF - MyLevel.Height() * TILE_HEIGHT +
           MyLevel.Depth() * TILE_X_OFF) / 2;

  // draw the level

  for (int z=0;z<MyLevel.Depth();z++) {
    for (int x=0;x<MyLevel.Width();x++) {
      for (int y=0;y<MyLevel.Height();y++) {
        if (MyLevel.Tile(x,y,z) > 0) {
          int xb = x * TILE_WIDTH - z * TILE_X_OFF;
          int yb = z * TILE_X_OFF + x * TILE_Y_OFF - y * TILE_HEIGHT;
          int id = MyLevel.Tile(x,y,z);
          DrawIMG(MySet.Image(), xb+pw, yb+ph, MySet.Tile(id).ImageClip());
        }
      }
    }
  }
  SDL_Flip(screen);
}
```

Versus a new one, which for now rewrites the bits before the loops (yes, I know, probably not the main bottleneck of the function):

```
void DrawScene() {
  SDL_FillRect(screen, NULL, SDL_MapRGB(screen->format,0,0,0));

  // center the level on the screen

  int pw = (SCREEN_WIDTH - TILE_WIDTH - TILE_X_OFF -
           MyLevel.Width() * TILE_WIDTH + MyLevel.Depth() * TILE_X_OFF) >> 1;
  int ph = (SCREEN_HEIGHT - TILE_HEIGHT - TILE_Y_OFF -
           MyLevel.Width() * TILE_Y_OFF + MyLevel.Height() * TILE_HEIGHT -
           MyLevel.Depth() * TILE_X_OFF) >> 1;

  // draw the level

  for (int z=0;z<MyLevel.Depth();z++) {
    for (int x=0;x<MyLevel.Width();x++) {
      for (int y=0;y<MyLevel.Height();y++) {
        if (MyLevel.Tile(x,y,z) > 0) {
          int xb = x * TILE_WIDTH - z * TILE_X_OFF;
          int yb = z * TILE_X_OFF + x * TILE_Y_OFF - y * TILE_HEIGHT;
          int id = MyLevel.Tile(x,y,z);
          DrawIMG(MySet.Image(), xb+pw, yb+ph, MySet.Tile(id).ImageClip());
        }
      }
    }
  }
  SDL_Flip(screen);
}
```

I figure the second one would be faster because I've gotten rid of unnecessary devisions, distributed through the parentheses, and replaced the one necessary devision by two with a right bitshift. Both of these functions have exactly the same output. I'd figure this would be easier for the computer. But it is a whole 5 frames (out of an original ~60) slower! Why!

---

### Post by mike_g on 2008-04-30
Replaceing /2 with >>1 should not make a difference as the compiler should optimise this automatically. I'm not sure why its slower, it may be possible that some background task had an influence?

If you want speed gains here are my suggestions. remove as many calculations from the inner loop as possible. I havent tested this so cant say it will work but maybe something like:
```

int depth = MyLevel.Depth();
int width = MyLevel.Width();
int height = MyLevel.Height();  
  for (int z=0;z<depth;z++) 
  {
    for (int x=0;x<width;x++) 
    {
      int xb = x * TILE_WIDTH - z * TILE_X_OFF;
      int xpos = xb+pw;
      for (int y=0;y<height;y++) 
      {
        if (MyLevel.Tile(x,y,z) > 0) 
        {
          int yb = z * TILE_X_OFF + x * TILE_Y_OFF - y * TILE_HEIGHT;
          int id = MyLevel.Tile(x,y,z);
          DrawIMG(MySet.Image(), xpos, yb+ph, MySet.Tile(id).ImageClip());
        }
      }
    }
  }
```
You also have a few function calls in the inner loop. If theres not much going on inside them then inlining it can make it faster, but it may affect the readability of your code. 

Also, Are you using a 3 dimensional array? If so you can get big speed increases by flattening it, although again it affects the code readability.

On this line:
```
if (MyLevel.Tile(x,y,z) > 0)
```
You could precalc a list of 'masked' tiles. Basically you note if the first tile is masked or not then have a list of numbers. you then draw x tiles, skip x tiles, draw x tiles, skip x tiles, etc. This would mean you can remove the if statment from your inner loop as well as reduce the number of iterations. I only used this techinque in the past for blitting, but I see no reason why it shoudl not work for a tile editor.

---

### Post by Npl on 2008-04-30
use forward differences, thats the thing that comes to my mind first.

instead of

```
for (int z=0;z<depth;z++) 
  {
    ...
    int yb = z * TILE_X_OFF;
    ....use yb
   }
```

do 

```
int yb = 0;
for (int z=0;z<depth;z++) 
  {
    ...use yb
    yb += TILE_X_OFF;
    ..
   }
```

also, use own variables instead of multiple (possible expensive) function calls when you know the values dont change.
```
int lvlHeight = MyLevel.Height();
.. use lvlHeight instead of function calls ..
```

and the most important thing is to figure out if its better to use DrawIMG (thats an SDL-Function i think?) like you did or use a bitmap for drawing and then send that to SDL as whole. Cant talk about SDL, but in most toolkits its better to upload as much as possible per call instead using many calls

---

### Post by Thorjelly on 2008-04-30
> **mike_g said:**
> Replaceing /2 with >>1 should not make a difference as the compiler should optimise this automatically. I'm not sure why its slower, it may be possible that some background task had an influence?

Yeah, you know, I figured that the compiler would optimize that sort of thing but I still read on some sites that implied bit-shifting was simply a faster thing to do with no mention of compiler optimization. I thought it sounded odd, I don't know.

I suppose background tasks COULD be the culprit, but I've tested and retested and have found the differences very consistent.

> **mike_g said:**
> If you want speed gains here are my suggestions. remove as many calculations from the inner loop as possible. I havent tested this so cant say it will work but maybe something like:
...

Yeah, that boosted me by a fps or two.

> **mike_g said:**
> You also have a few function calls in the inner loop. If theres not much going on inside them then inlining it can make it faster, but it may affect the readability of your code.

Also, Are you using a 3 dimensional array? If so you can get big speed increases by flattening it, although again it affects the code readability.

Yes, I am using a 3 dimensional array. I'm not sure how to do either of these things.

> **mike_g said:**
> On this line:
```
if (MyLevel.Tile(x,y,z) > 0)
```
You could precalc a list of 'masked' tiles. Basically you note if the first tile is masked or not then have a list of numbers. you then draw x tiles, skip x tiles, draw x tiles, skip x tiles, etc. This would mean you can remove the if statment from your inner loop as well as reduce the number of iterations. I only used this techinque in the past for blitting, but I see no reason why it shoudl not work for a tile editor.

That's an idea, and I remember in a Python project I did something similar (for a pixel perfect collision detection system -- I was quite proud to have made hundreds and hundreds of lizards bouncing off of jagged floors and walls just in Python), but at this point in the project I would probably be better to keep the map format as flexible as possible.

> **Npl said:**
> use forward differences, thats the thing that comes to my mind first.

instead of

...

do 

...

I'm not quite sure I quite understand this either. You mean

```
int i = 0;
i += a*b+c*d;
```

is faster than

```
int i = a*b+c*d;
```

?

> **Npl said:**
> also, use own variables instead of multiple (possible expensive) function calls when you know the values dont change.
```
int lvlHeight = MyLevel.Height();
.. use lvlHeight instead of function calls ..
```

I tried this out earlier and was surprised that it really didn't seem to make any difference. I kept the function calls in because I thought they were easier to read. Now I tried it again, taking DrawIMG out for a moment to improve the "resolution", so to speak, of the change's speed, and have indeed noticed it makes a difference, albeit a very small one.

> **Npl said:**
> and the most important thing is to figure out if its better to use DrawIMG (thats an SDL-Function i think?) like you did or use a bitmap for drawing and then send that to SDL as whole. Cant talk about SDL, but in most toolkits its better to upload as much as possible per call instead using many calls

Oh, no, actually, it's my own function, sorry. (Well, copied, mostly, out of an SDL tutorial, hehe)

```
void DrawIMG(SDL_Surface* img, int x, int y, SDL_Rect dest2) {
  SDL_Rect dest;
  dest.x = x;
  dest.y = y;
  SDL_BlitSurface(img, &dest2, screen, &dest);
}
```

In SDL there is no "screen" precisely. The screen is just any surface object you construct and then plug into its video. Blitting to it is like blitting to any other surface; I don't think blitting to a surface and then drawing that surface to the screen would improve anything, because you are doing just the same thing when you blit to the screen in the first place. At least, that is how I understand it. I'll look into it a bit more, though.

---

### Post by Wybiral on 2008-04-30
As mentioned, modern compilers should optimize those types of things for you. But... Those aren't even in the main loops, why would you expect them to be much of a speedup (they're only being performed once a frame, so you shouldn't expect much if anything).

Your real speedup would come if you stopped rendering EVERYTHING each frame. Consider caching the images that aren't moving into one surface and rendering that instead of rendering them each separately.

Or using a hashtable and only storing important objects, not each tile on the screen (the background should be cached as one object and render as one, if it's not moving... Why render them individually?)

---

### Post by Thorjelly on 2008-04-30
Well... honestly, this thread wasn't really meant to be so much about "please optimize my code" as much as it was "why the heck is this faster than that". I shouldn't even be bothering optimizing at this point in the project, to be honest, but I am mostly doing this as a learning exercise, so I was curious as to why I got the results that I seemed to have gotten. That is mainly it. Really, heh, if I absolutely needed to make this faster the first thing I would do would probably be to switch to OpenGL and render textured rectangles on the screen instead of blitting 2D images. :P Sorry if I didn't make that terribly clear... but I thank everyone for the tips they've given me so far, anyway.

---

### Post by DavidBell on 2008-05-01
Not sure but I don't like the way your loops go z, x, y (ie not z, y, x) as far as I can tell you are accessing the image in vertical lines. You need to check how your image is stored - if it's like windows it will be in a contiguous area of memory that represents series of horizontal lines. 

It can make a huge difference if you process pixels more or less the order they are stored in RAM, because it can means your CPU L1/2 cache gets a lot more 'look ahead' hits. 

In windows I have seen the difference between handling an image as vertical lines vs horizontal lines cause a 70% speed reduction. That was reading, whereas you are writing, but I think it still is an issue, so the moral of the story is check how your image is stored and set up your loops to follow that as close as you can.

HTH DB

---

### Post by Npl on 2008-05-01
> **Thorjelly said:**
> I'm not quite sure I quite understand this either. You mean

```
int i = 0;
i += a*b+c*d;
```

is faster than

```
int i = a*b+c*d;
```

?Nope, if you are multiplying with a incrementing loop variable, you can save the multiplication and use addition instead.
```
for(int i = 0; i < 10; ++i)
{
  myFunction(i*SOMEVAL);
}
```

```
int v = 0;
for(int i = 0; i < 10; ++i)
{
  myFunction(v);
  v += SOMEVAL; // no multiplication in the inner loop
}
```

---


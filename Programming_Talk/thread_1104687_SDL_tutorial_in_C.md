---
title: "SDL tutorial in C"
date: 2009-03-23
forum: Programming Talk
---

### Post by swappo1 on 2009-03-23
Hello,

I am trying to convert an SDL tutorial from lazy foo from C++ to C but I don't know C++.  I have the following written in C++ and I am not sure how to convert the SDL_Rect* clip = NULL into something C will accept.  Here is the function and output.  Any ideas?
```
SDL_Rect clip[4];
..........................
void apply_surface(int x, int y, SDL_Surface* source, SDL_Surface* destination, SDL_Rect* clip = NULL)
{
	SDL_Rect offset;
	
	offset.x = x;
	offset.y = y;
	
	SDL_BlitSurface(source, clip, destination, &offset);
```
```
lazyfoo6.c:17: error: expected ‘;’, ‘,’ or ‘)’ before ‘=’ token
lazyfoo6.c:95: error: expected ‘;’, ‘,’ or ‘)’ before ‘=’ token

```

---

### Post by Simian Man on 2009-03-23
That is a default parameter.  Just remove it and wherever the apply_surface function is called with a missing parameter, substitute NULL for it.

Hope that makes sense.

---

### Post by swappo1 on 2009-03-23
If I understand you correctly, I should remove the = NULL from the function and prototype and use NULL for last argument of apply_surface.  Then I wouldn't blit the sprites to the surface.  I am not sure why SDL_Rect* clip is even set to NULL in the first place.  Here is where apply_surface is called.
```
apply_surface(0, 0, dots, screen, &clip[0]);
apply_surface(540, 0, dots, screen, &clip[1]);
apply_surface(0, 480, dots, screen, &clip[2]);
apply_surface(540, 480, dots, screen, &clip[3]);
```
If I remove = NULL from the function and prototype, all I get is a white screen when I should have four sprites blitted to the corners of the white screen.

---

### Post by swappo1 on 2009-03-23
Okay, I found the problem and it was unrelated to = NULL.

---


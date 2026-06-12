---
title: "Generating SDL Surface"
date: 2008-02-23
forum: Programming Talk
---

### Post by Zeotronic on 2008-02-23
As the title indicates, this thread is specifically about SDL, all others go back. Specifically SDL for C++. (there are other versions arn't there?)
I am not unexperianced in with SDL, but I do not have quite enough experiance yet it seems. I want to figure out how to make a empty image of a specified, ajustable (on creation at least) size. I want to do this to draw SDL Gfx primitives to it. My reasons for this are numerous and complicated. I had made a previous attempt, loading up a fully transparent PNG and drawing the primitive to it, but the primitive was transparent as well, which it shouldn't have been. I could draw it to a fully opaque PNG and it would show up, but that is not the goal, and is, to the best of my abilities, unusable. I don't suppose anyone would have any ideas on how to perform this task which I cannot to the best of my abilities accomplish.

---

### Post by cb951303 on 2008-02-23
[http://www.libsdl.org/cgi/docwiki.cgi/SDL_5fCreateRGBSurface](http://www.libsdl.org/cgi/docwiki.cgi/SDL_5fCreateRGBSurface)

You're not going to learn anything by ignoring to look at the documentations ;)

---

### Post by slavik on 2008-02-23
once you get a surface there is a saveBMP or similar function that takes a surface and saves it as a bitmap.

when you create a surface one of the components is pixels which is an array of pixels (there is also width and height) you should be able to modify those however you want (I have not tried it).

as for creating a new surface, look at how to create a surface, there are options for width/height/bitdepth

---

### Post by Zeotronic on 2008-02-24
> You're not going to learn anything by ignoring to look at the documentations 
You are mistaken to think that I do not look at the documentation, I just find it confusing sometimes! Thank you for pointing me at what I need.

---

### Post by Zeotronic on 2008-02-28
It is too bad, I have been messing with what you have advised for me for a few days now, but unfortunately I am ultimately having problems with it. (though I was having other problems too, which is why figuring this out took me so long.)
This is my command:
```
surface=SDL_CreateRGBSurface(SDL_HWSURFACE | SDL_SRCALPHA,32,32,16,0,0,0,0);
```
Ok, so in actuallity my command isn't quite that... but thats what it translates to (yes, I am sure that is correctly what it translates to) However, despite my various attempts, it has a black background... I cant make it transparent without making everything I blit to it transparent (which I do by calling the above code followed by SDL_SetAlpha() and such, followed by my blits.) I'm sorry if I'm not giving you enough code to figure out what I'm doing wrong with, but I don't want to drown you in all of my code. If you request it though, I will give you everything that could potentially be related.

I have tested, and I'm sure that what I blit too it would be properly transparent on its own, so to the best of my abilities this is what I'm having problems with.

---

### Post by cb951303 on 2008-03-01
uhm I'm not sure if that's related but here is a quote from sdl docs

```

Notes: Sometimes specifying an Alpha mask value could cause strange results. This can be worked around by setting the Amask parameter to 0, but still including the SDL_SRCALPHA flag, and then using SDL_SetAlpha, also with the SDL_SRCALPHA flag.
```

Can you elaborate a little bit more what you trying to achieve? Are you trying to blit opaque bitmaps to a fully transparent background bmp?
sorry if you already explained it, sometimes it's hard for me to understand english :)

---

### Post by mike_g on 2008-03-01
If i understand you right you want a colour mask, to mask out one particular color. If you add this line after you create your surface it will make all the black pixels transparent:
```
SDL_SetColorKey(surface, SDL_SRCCOLORKEY, SDL_MapRGB(surface->format, 0, 0, 0));
```
Then all non-black stuff you draw to the surface should be displayed.

---

### Post by Zeotronic on 2008-03-02
> If i understand you right you want a colour mask, to mask out one particular color.
I'm sorry, no, you do not understand me correctly... but thinking about it I may have to do something like that.
> uhm I'm not sure if that's related but here is a quote from sdl docs

*insert quote here*
I am aware, and have tried that but it does not give me the intended result.
> Can you elaborate a little bit more what you trying to achieve?
Yes, I will elaborate... I want to create a transparent surface for which to blit things onto... tiles, lettering... things that are essentually one object, but are not really. The reason I want to do this is primarily for rotaton... I don't want there to be holes in-between the tiles when I rotate a tile layer so I blit them all to one surface and rotate the surface. (besides the fact that it makes it easier to do)
However, I cannot manage to make a surface to blit to that is transparent... and when I have actually manage to create a transparent surface, everything I blit to it is made transparent, which makes it useless.
I hope now you can understand what I am trying to achieve.

---


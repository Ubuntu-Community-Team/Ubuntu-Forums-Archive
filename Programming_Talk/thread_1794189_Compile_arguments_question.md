---
title: "Compile arguments question?"
date: 2011-06-30
forum: Programming Talk
---

### Post by ThatCoolGuy220 on 2011-06-30
Hi im back long time since I asked my las question, jeje:KS well.

I have a doubt I was beginning with SDL libraries and I had set up Geany to work with them, now I included this argument on the Build options:

```
g++ -Wall -o "%e" "%f" -lmingw32 -lSDLmain -lSDL -lopengl32
-lglu32 

```

So as the compile one.

And everything works fine but this arguments are also present on other kind of proyects that arent SDL about.
 
Here it comes my newbie, quite no so smart question excuse me first:

I also work with Console only projects and these ones doesnt need this Arguments I think.

Will this arguments afect the way the program will work cause it still compiles but I would like to know if this is right



Thanks:popcorn:

---

### Post by Arndt on 2011-06-30
> **ThatCoolGuy220 said:**
> Hi im back long time since I asked my las question, jeje:KS well.

I have a doubt I was beginning with SDL libraries and I had set up Geany to work with them, now I included this argument on the Build options:

```
g++ -Wall -o "%e" "%f" -lmingw32 -lSDLmain -lSDL -lopengl32
-lglu32 

```

So as the compile one.

And everything works fine but here it comes my newbie, quite no so smart question excuse me first:


I also work with Console only projects and these ones doesnt need this Arguments I think.

Will this arguments afect the way the program will work cause it still compiles but I would like to avoid risk.



Thanks:popcorn:

I don't quite see what your question actually is. Are you wondering whether you need to include -lSDL or not? I would try to leave it out, and if the build succeeds, it means I didn't need it. On the other hand, having it there when it's unnecessary won't do any harm except if something in it happens to have the same name as something expected to be fetched from a library later on the command line, which is unlikely (but not impossible). You can eliminate the latter risk by putting it at the end of the command line.

---

### Post by ThatCoolGuy220 on 2011-06-30
thanks for your answer, yes I have it at the end of the line.


PD: I updated my first post, sorry english isnt my natal language but I try.

---

### Post by ThatCoolGuy220 on 2011-06-30
But what would you recomend

---

### Post by cgroza on 2011-06-30
When I use SDL I don't link to SDLmain, only SDL.

---


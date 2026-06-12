---
title: "SDL_GL attributes."
date: 2008-01-23
forum: Programming Talk
---

### Post by Senesence on 2008-01-23
In the SDL docs ([Link](http://www.libsdl.org/cgi/docwiki.cgi/SDL_5fGL_5fSetAttribute)), it's stated that the obtained SDL_GL attribute values can "differ" from those originally requested via SDL_GL_SetAttribute().

I've confirmed this with the following piece of code:

```

#include "SDL/SDL.h"
#include "SDL/SDL_opengl.h"
#include <iostream>
using namespace std;

int main(){
	SDL_Init(SDL_INIT_EVERYTHING);
	
	SDL_GL_SetAttribute(SDL_GL_RED_SIZE,      5);
	SDL_GL_SetAttribute(SDL_GL_GREEN_SIZE,    5);
	SDL_GL_SetAttribute(SDL_GL_BLUE_SIZE,     5);
	SDL_GL_SetAttribute(SDL_GL_DEPTH_SIZE,   16);
	SDL_GL_SetAttribute(SDL_GL_DOUBLEBUFFER,  1);
	
	SDL_SetVideoMode(640, 480, 16, SDL_OPENGL);
	
	SDL_GLattr Array[] = {SDL_GL_RED_SIZE, SDL_GL_GREEN_SIZE, SDL_GL_BLUE_SIZE};
	for (int i=0; i<3; i++){
		int temp;
		int *ptemp = &temp;
		SDL_GL_GetAttribute(Array[i], ptemp);
		cout << temp << endl; // spits out 8 for all
	}
	
	SDL_Delay(1000);
	
	SDL_Quit();
}

```

I request 5 for R, G and B, but I get 8 instead. Now, this is apparently normal behavior (because that's what the documentation implies), but I'm still wondering why this is so.

That is: Why can't the values obtained always be the values requested? What does it all depend on?

Thanks.

---

### Post by Senesence on 2008-01-24
No one knows?

Heh, I guess SDL is not as popular as I previously thought.:)

---

### Post by slavik on 2008-01-24
because OpenGL assigns 8 bits for each color, what does retrieving the depth give you?

---

### Post by Senesence on 2008-01-24
> **slavik said:**
> because OpenGL assigns 8 bits for each color

Yea, but then what's the point of having something like "SDL_GL_SetAttribute()" in the first place? It does nothing if OpenGL just defaults to 8 or some other arbitrary value.

It just doesn't make sense to me.

> what does retrieving the depth give you?

24

---

### Post by Tuna-Fish on 2008-01-25
> **Senesence said:**
> Yea, but then what's the point of having something like "SDL_GL_SetAttribute()" in the first place? It does nothing if OpenGL just defaults to 8 or some other arbitrary value.


8 isn't the only possible value, hdr needs more. try 16.

What values are supported ultimately depend on your vid card. If it cannot comprehend 5-bit colors, sdl isn't gonna give them to you.

---

### Post by Senesence on 2008-01-26
[QUOTE=Tuna-Fish]What values are supported ultimately depend on your vid card. If it cannot comprehend 5-bit colors, sdl isn't gonna give them to you.[/QUOTE]

Yea, that would make sense.

Although, you would think a card that supports 8 could also support 5 easily.

---

### Post by rnodal on 2008-02-17
Based on my understanding when you use those functions you are requesting the "minimum" required by your application. So it is normal for you to get more than what you want but if you get less SDL_SetVideoMode will fail. That's just based on my understanding so keep that in mind :). 

-r

---

### Post by slavik on 2008-02-17
that's how OpenGL is, it tried its best to give you want you want (even if it means doing it in software sometimes).

When ID wrote Doom3, the multiple render paths are there because if OpenGL sees something not supported by the video hardware, it will shrug its shoulders and tell the CPU to do it ... which won't be very fast. ;)

---


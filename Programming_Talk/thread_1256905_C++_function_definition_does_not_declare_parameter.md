---
title: "C++: function definition does not declare parameters"
date: 2009-09-03
forum: Programming Talk
---

### Post by matmatmat on 2009-09-03
I have this code:
```

241 class Ball{
242     public:
243     int x;
244     int y;
245     int yVel;
246     int xVel;
247     //The direction 1=right,up 2=right,down 3=left,up 4=left,down
248     int dir;
249     void SetP(int px, int py, SDL_Surface* bi);
250     void draw();
251     SDL_Rect box;
252     SDL_Surface *image;
253 };
254 
255 void Ball:SetP(int px, int py, SDL_Surface* bi){
256     x = px;
257     y = py;
258     box.x = x;
259     box.y = y;
260     box.h = BALL_HEIGHT;
261     box.w = BALL_WIDTH;
262     image = bi;
263 }

```
when compiled:
```

matio@matio-desktop:~/Projects/SDL/BREAKOUT$ g++ -g breakout.cpp -o breakout -lSDL -lSDL_image -lSDL_ttf
breakout.cpp:256: error: function definition does not declare parameters

```
whats wrong?

---

### Post by Zugzwang on 2009-09-03
Perhaps you should try 
```

void Ball::SetP(int px, int py, SDL_Surface* bi)

```
instead of
```

void Ball:SetP(int px, int py, SDL_Surface* bi)

```

---

### Post by Tony Flury on 2009-09-03
> **matmatmat said:**
> I have this code:
```

241 class Ball{
242     public:
243     int x;
244     int y;
245     int yVel;
246     int xVel;
247     //The direction 1=right,up 2=right,down 3=left,up 4=left,down
248     int dir;
249     void SetP(int px, int py, SDL_Surface* bi);
250     void draw();
251     SDL_Rect box;
252     SDL_Surface *image;
253 };
254 
255 void Ball:SetP(int px, int py, SDL_Surface* bi){
256     x = px;
257     y = py;
258     box.x = x;
259     box.y = y;
260     box.h = BALL_HEIGHT;
261     box.w = BALL_WIDTH;
262     image = bi;
263 }

```
when compiled:
```

matio@matio-desktop:~/Projects/SDL/BREAKOUT$ g++ -g breakout.cpp -o breakout -lSDL -lSDL_image -lSDL_ttf
breakout.cpp:256: error: function definition does not declare parameters

```
whats wrong?

My C++ is a bit rough - but should you not be using "this" somewhere ?

i.e.

```

255 void Ball:SetP(int px, int py, SDL_Surface* bi){
256     this.x = px;
257     this.y = py;
258     this.box.x = x;
259     this.box.y = y;
260     this.box.h = BALL_HEIGHT;
261     this.box.w = BALL_WIDTH;
262     this.image = bi;
263 }
```

As otherwise the compiler will think that x,y, box and image are local variables (which aren't declared anywhere).

---

### Post by matmatmat on 2009-09-03
Thanks, I didn't notice there was only one ':'

---

### Post by haTem on 2009-09-03
> **Tony Flury said:**
> My C++ is a bit rough - but should you not be using "this" somewhere ?

i.e.

```

255 void Ball:SetP(int px, int py, SDL_Surface* bi){
256     this.x = px;
257     this.y = py;
258     this.box.x = x;
259     this.box.y = y;
260     this.box.h = BALL_HEIGHT;
261     this.box.w = BALL_WIDTH;
262     this.image = bi;
263 }
```

As otherwise the compiler will think that x,y, box and image are local variables (which aren't declared anywhere).

That is unnecessary, the compiler knows that x, y, etc are class variables. The only time you would have to use the "this" pointer in that way would be if the names of the method parameters conflicted with the names of class variables.

---

### Post by Tony Flury on 2009-09-03
Shows you how ropey my C++ is :-)

---


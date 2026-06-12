---
title: "C++ Array Of Objects"
date: 2009-09-01
forum: Programming Talk
---

### Post by matmatmat on 2009-09-01
Can I have an array of C++ Objects?
```

MyObject array[100];
MyObject obj;
array[0] = obj;

```

---

### Post by MadCow108 on 2009-09-01
how about just trying?
of course you can

---

### Post by matmatmat on 2009-09-01
I have:
```

class Block{
    private:
    int x;
    int y;
    int hitn;
    int points;
    public:
    Block(int px, int py, SDL_Surface bi, int nhit, int po);
    void draw();
    SDL_Rect box; 
    SDL_Surface image;   
};

Block::Block(int px, int py, SDL_Surface bi, int nhit, int po){
    x = px;
    y = py;
    box.x = x;
    box.y = y;
    box.h = BLOCK_HEIGHT;
    box.w = BLOCK_WIDTH; 
    image = bi;
    hitn = nhit; 
    points = po;  
}
void Block::draw(){
    apply_surface( (int)x, (int)y, &image, screen);
}
 
// snip

Block bobj[1000];

```
which doesn't work:
```

breakout.cpp: In function &#8216;int main(int, char**)&#8217;:
breakout.cpp:264: error: no matching function for call to &#8216;Block::Block()&#8217;
breakout.cpp:123: note: candidates are: Block::Block(int, int, SDL_Surface, int, int)
breakout.cpp:110: note:                 Block::Block(const Block&)

```

---

### Post by MadCow108 on 2009-09-01
your object has no default constructor which it tries to call when you declare the array with obj array[x];
you need a default constructor Block() when using arrays of objects
so far I know there is no way to initialise an array ob objects with parameters.
you'll have to iterate over the array and set the values "by hand".

---

### Post by matmatmat on 2009-09-01
Thanks, it is now:
```

class Block{
    private:
    int x;
    int y;
    int hitn;
    int points;
    public:
    void SetP(int px, int py, SDL_Surface bi, int nhit, int po);
    void draw();
    SDL_Rect box; 
    SDL_Surface image;   
};

void Block::SetP(int px, int py, SDL_Surface bi, int nhit, int po){
    x = px;
    y = py;
    box.x = x;
    box.y = y;
    box.h = BLOCK_HEIGHT;
    box.w = BLOCK_WIDTH; 
    image = bi;
    hitn = nhit; 
    points = po;  
}
void Block::draw(){
    apply_surface( (int)x, (int)y, &image, screen);
}
 
// snip

Block bobj[1000];
int score = 10;
int hits = 1;
int x = 10;
int y = 10;
Block b;
b.SetP(x, y, rblock, hits, score);

```
when compiled:
```

breakout.cpp:298: error: no matching function for call to &#8216;Block::SetP(int&, int&, SDL_Surface*&, int&, int&)&#8217;
breakout.cpp:123: note: candidates are: void Block::SetP(int, int, SDL_Surface, int, int)

```

---

### Post by MadCow108 on 2009-09-01
your parameters passed to SetP are wrong.
rblock seems to be a pointer but it expects a non pointer value.
btw if SDL_Surface is some bigger object (e.g. expensive to copy) then you should pass it by reference:
void SetP(int px, int py, SDL_Surface & bi, int nhit, int po);
this is the C++ equivalent to passing of pointers what you usually do in C

---

### Post by Namtabmai on 2009-09-01
AFAIK you should never create a SDL_Surface yourself, this will be created by SDL for you, so change the parameters to be a pointer to a SDL_Surface.

```

SDL_Surface* bi

```

---

### Post by matmatmat on 2009-09-01
Thanks for the replies, I now have:
```

class Block{
    private:
    int x;
    int y;
    int hitn;
    int points;
    public:
    void SetP(int px, int py, SDL_Surface* bi, int nhit, int po);
    void draw();
    SDL_Rect box; 
    SDL_Surface *image;   
};

void Block::SetP(int px, int py, SDL_Surface* bi, int nhit, int po){
    x = px;
    y = py;
    box.x = x;
    box.y = y;
    box.h = BLOCK_HEIGHT;
    box.w = BLOCK_WIDTH; 
    image = bi;
    hitn = nhit; 
    points = po;  
}
void Block::draw(){
    apply_surface( (int)x, (int)y, &image, screen);
}

```
but this also gives an error:
```

breakout.cpp:135: error: cannot convert &#8216;SDL_Surface**&#8217; to &#8216;SDL_Surface*&#8217; for argument &#8216;3&#8217; to &#8216;void apply_surface(int, int, SDL_Surface*, SDL_Surface*, SDL_Rect*)&#8217;

```

---

### Post by MadCow108 on 2009-09-01
drop the & in front of the image in the apply_surface call as image is already a pointer now.
actually the error message already tells you all:
```

breakout.cpp:135: error: cannot convert &#8216;SDL_Surface**&#8217; to &#8216;SDL_Surface*&#8217; for argument &#8216;3&#8217; to &#8216;void apply_surface(int, int, SDL_Surface*, SDL_Surface*, SDL_Rect*)&#8217;
```
argument 3 SDL_Surface**: this means argument 3 (&image) is a pointer to a pointer
but it expects a SDL_Surface* which is just a pointer

---

### Post by napsy on 2009-09-01
You are passing a pointer to a pointer to a function that requires a pointer. I suggest you first learn how pointers work.

---

### Post by dwhitney67 on 2009-09-01
Consider the following (which employs your original Block class definition):
```

#include <vector>

...

std::vector<Block*> blocks;

blocks.push_back(new Block(x, y, surface, hits, score ));
// repeat for additional Block objects

```
Note that if you do not wish to allocate Block objects, then you can just declare std::vector<Block>; however, depending on your needs, you may be required to define/implement a copy-constructor within Block.

---

### Post by MadCow108 on 2009-09-01
important when using dwhitneys suggestion is that you still need to delete your allocated objects by hand.
the vector will not do that for you.

If you don't want to care about this put boost::shared_ptr to your objects into the vector
(or use boosts pointer containers)

---


---
title: "Toadeki - C++ Game Programming - Really that difficult?"
date: 2014-01-25
forum: Programming Talk
---

### Post by slooksterpsv on 2014-01-25
Talk about wanting to pull out my hair haha. Well it seems like programming is very difficult to me cause I'm expecting a lot out of my programs, but they run like crap. Here's the issues I'm seeing and what I'm asking:

I want to post my full Toadeki source - I'm a terrible commentor because most of my code is undocumented yet I know what does what, why, where and what for.
Toadeki - while it runs great, it seems like it's still slow. I'm using SDL2 and SDL_PRESENTVSYNC doesn't seem to be capping my frames at 60, yet when my map is drawn it caps it at 60 yet goes slower. I could implement a timer, that's not too hard, but still seems like I'm missing something. Moving the camera doesn't seem smooth or the player either.
Graphics - When copying graphics to memory I keep thinking I could optimize it based on where I'm standing at. The program runs at 640x480 windowed. Right now it draws all the tiles to the screen (visible screen), and doesn't draw the tiles outside so if the maps are large I don't have to draw them continuously (saved a lot of power). Now I'm wondering if I should do areas inside my camera. So for example

```

000000000
000000000
000000010
000000000
000000000

```

I'm where 1 is at and since there isn't anything else there hold the locations in a memory location where I won't have to draw all the 0's so it'd look like this:
```

[0000]00000
[0000]00000
[0000]00010
00000000000
00000000000

```

So what's between the braces will be their own image to blit, that may be a bit more costly to cpu usage though. My cpu usage on my prog is about 3-4%.

Any suggestions?

I'm using Vectors (amazing), drawing within a camera (speed efficient), there's no collision detection yet or other object layers (I have them setup just nothing in them) yet, but things move when I move towards the edge of the camera.

Any suggestions for optimizations? It's a 2D Game I'm working on.

---


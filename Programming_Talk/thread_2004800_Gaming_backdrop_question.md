---
title: "Gaming backdrop question"
date: 2012-06-16
forum: Programming Talk
---

### Post by pieman711 on 2012-06-16
I made a game years ago in blitz basic and am currently rewriting it in C++. Its a simple maze type game a bit like chips challenge. Currently I have the screen divided into the gaming window in the top left part of the screen, which currently has a fixed resolution, and the rest of the screen is taken up by just a black border.  If the resolution is changed then the amount of black area will change.
I wanted to know what is the best way of filling this space to make it look a bit more pretty. I could draw something in a Paint type program and just load it in but then I would imagine I would need a fixed resolution otherwise it would look off when it got changed. Another possibility is to make a simple tile type image and just repeat it to fill what ever space there is.

Is there another option I may have missed? 
I'm using allegro 5 as my programming library and am entirely self taught at programming so may have missed something fairly obvious here.

---

### Post by Barrucadu on 2012-06-16
Why not simply have the game window the same size as the actual window? That is, either make the game window fullscreen, or make your program not fullscreen.

---

### Post by pieman711 on 2012-06-16
I was thinking about that, I was hoping to use some decoration outside the window to make it look a bit nicer and possible have some information like the amount of time left before you have to move again and the number of keys left to pick up. 
Since I posted the initial question I've had a go with filling the background with a simple repeating tile. Looks ok so far and I've used this:

    for(x =0; x<=SCREENWIDTH; x=x+22){
        for(y=0;y<=SCREENHEIGHT;y=y+24){
            al_draw_bitmap(wallBmp, x, y,0);
        } 

So the number of tiles will change depending on the screen size (the tile is 22x24 pixels big)

It wasn't until i was typing the question that I thought up the idea of tiling it.

---


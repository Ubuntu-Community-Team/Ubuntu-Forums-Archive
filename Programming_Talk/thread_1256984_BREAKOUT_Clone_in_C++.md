---
title: "BREAKOUT Clone in C++"
date: 2009-09-03
forum: Programming Talk
---

### Post by matmatmat on 2009-09-03
Attached is my clone of Breakout in C++. When the ball bounces of the side it seems to make weird movements, also the last block never gets removed.

Can anyone help with these things?

---

### Post by Volt9000 on 2009-09-05
Well your problem is your assignment of x in your if clause in your draw function.

[php]
void Ball::draw(Uint32 deltaTicks){
    //If the dot went too far to the left

    if( x < 0 )

    {

        //Move back

        x = BALL_WIDTH;   //   <-------- THIS LINE HERE
        if (dir == 3){
            dir = 1;
        }else{
            dir = 2;
        }

    }

    //or the right

    else if( x + BALL_WIDTH > SCREEN_WIDTH)

    {

        //Move back

        x = SCREEN_WIDTH - BAT_WIDTH - 1; // <----- AND THIS ONE
....
[/php]

Think about it-- if x is less than 0, and all of a sudden you set it to BALL_WIDTH, which is 20, of course it will appear to jump.
Just comment out those lines I indicated and the jumping is gone.

As for the last block not being removed-- can you be more specific? The ball hits it, but it won't disappear, or you can't hit it?

---

### Post by matmatmat on 2009-09-11
You can hit it but it won't disappear.

---


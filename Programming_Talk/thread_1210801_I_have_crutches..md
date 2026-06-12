---
title: "I have crutches."
date: 2009-07-11
forum: Programming Talk
---

### Post by pepperphd on 2009-07-11
Hello Ubuntu community! I have been teaching myself to program for about three months now (C and C++) using whatever resources I can including a few fat books and the all powerful google search.  In trying to get a feel for what a big project actually feels like so I've been working on a 2d action game (think LTTP) using the SDL library. My code uses a disturbing number of ifs, switches, and function local statics. Here is a function I wrote for enemies that lazily gravitate towards the player and on contact cause damage. This is why I worry about the number of if statements I use.

Any advice or criticism is welcome. Thanks in advance.

```
void generic_gravitation()
        {
            if(status == 0)
                return;
    
            if(SDL_GetTicks() < invul_ticker + 1500 && invulnerable == true)
                return;
            else invulnerable = false;
            
            if(SDL_GetTicks() < stun_ticker + stun_time && stunned == true)
                return;
            else    stunned = false;

            ydiff = abs(player.coll_box.y) - abs(hit_box.y);
            xdiff = abs(player.coll_box.x) - abs(hit_box.x);

            if(player.coll_box.x > hit_box.x)
                x_vel = x_vel + 2;
            else    x_vel = x_vel - 2;


            if(player.coll_box.y > hit_box.y)
                y_vel = y_vel + 2;
            else    y_vel = y_vel - 2;

            if(x_vel > velocity_modifier)
                x_vel = velocity_modifier;
            
            if(x_vel < -velocity_modifier)
                x_vel = -velocity_modifier;
            
            if(y_vel > velocity_modifier)
                y_vel = velocity_modifier;
            
            if(y_vel < -velocity_modifier)
                y_vel = -velocity_modifier;

            if(abs(xdiff) > abs(ydiff))
            {
                if(x_vel > 0)
                    current_facing = RIGHT;
                else     current_facing = LEFT;
            }    
            else
            {
                if(y_vel > 0)
                    current_facing = DOWN;
                else    current_facing = UP;
            }

            old_x = hit_box.x;
            old_y = hit_box.y;
            
            hit_box.x += x_vel/2;
            hit_box.y += y_vel/2;

            if(check_collision(hit_box, player.sword_range) == true)
            {
                if(player.swinging == true && invulnerable == false)
                    take_damage(1);
            }
            
            if(check_collision(hit_box, player.coll_box) == true)
            {
                player.take_damage(1, current_facing);
                x_vel = y_vel = 0;
            }

            if(player.current_room->master_collision_check(hit_box) == true)    
            {
                hit_box.x = old_x;
                hit_box.y = old_y;
            }
        }
```

---

### Post by slavik on 2009-07-11
besides combining some of them and adding some else statements, I don't see how you can really reduce much of the code ... unless I am missing something.

---

### Post by Can+~ on 2009-07-12
*edit: Nevermind.

---

### Post by lavinog on 2009-07-12
> **Can+~ said:**
> ```

if(x_vel > velocity_modifier)
    x_vel = velocity_modifier;

if(x_vel < -velocity_modifier)
    x_vel = -velocity_modifier;

if(y_vel > velocity_modifier)
    y_vel = velocity_modifier;

if(y_vel < -velocity_modifier)
    y_vel = -velocity_modifier;

```
...

```

if(x_vel < -velocity_modifier || x_vel > velocity_modifier)
    x_vel = abs(velocity_modifier);

if(y_vel < -velocity_modifier || y_vel > velocity_modifier)
    y_vel = abs(velocity_modifier);

```



Wouldn't this keep setting the velocity to be positive once the negative velocity reaches its limit?

I think it would be better to use if..else if
```

if(x_vel > velocity_modifier)
    x_vel = velocity_modifier;

else if(x_vel < -velocity_modifier)
    x_vel = -velocity_modifier;

if(y_vel > velocity_modifier)
    y_vel = velocity_modifier;

else if(y_vel < -velocity_modifier)
    y_vel = -velocity_modifier;

```

You can also break the velocity up into a magnitude and a direction, this way you only have to work with a singe magnitude. This might be more what you are looking for because currently the object can travel faster if it is moving diagonally (not realistic to real life)

---

### Post by pepperphd on 2009-07-12
You're right about the diagonal movement and I knew of no way to fix it.  I'm not much of a mathematician (which I know is bad for a game programmers resume, so I'll work on it) so thanks for the advice, I'll look it up.  From what I gather the function is fine though, and I should not be worried about the prominence of if statements in my games.

---

### Post by fr4nko on 2009-07-12
For the mathematical point of view, if you want to limit the magnitude of the speed you could do something like that
```

double v_norm = sqrt(x_vel*x_vel + y_vel*y_vel);
if (v_norm > velocity_modifier)
  {
    double cost = x_vel / v_norm, sint = y_vel / v_norm;
    x_vel = velocity_modifier * cost;
    y_vel = velocity_modifier * sint;
  }

```In this way, if the speed is greater of velocity_modifier its magnitude is adjusted to this latter value without changing the direction.

In this way you have already reduced the number of if conditions. More generally, you're duplicating most of the code for x and y. You can get more elegant code by writing it in vectorial form. For example, instead of
```

hit_box.x += x_vel/2;
hit_box.y += y_vel/2;

/* ... */

hit_box.x = old_x;
hit_box.y = old_y;

```you could write
```
hit_box += vel / 2;
/* ... */
hit_box = old;

```to obtain this you should write a suitable class then embed the x and y coordinates and you should redifine the operators +=, / and =. The C way of doing this job would be
```

vector_scale (vel, 1/2.0);
vector_increment (hit_box, vel);
/* ... */
vector_assign (hit_box, old);

```In other part I have the impressions that you don't master enough the mathematics of vectors and your code is, as a result, confused. I was not able to understand the code about 'current_facing'.

As a final remarks, after line 8 you are sure that invulnerable is false so you don't need to check it.

Francesco

---

### Post by Can+~ on 2009-07-12
> **lavinog said:**
> Wouldn't this keep setting the velocity to be positive once the negative velocity reaches its limit?

Now that I woke up and drank several cups of coffee, I realize the piles of s*** I wrote before and the glaring mistake.

Anyway, +1 on using [vector math]("http://en.wikipedia.org/wiki/Vector_space") to solve positioning and speed.

---

### Post by pepperphd on 2009-07-12
> I was not able to understand the code about 'current_facing'. 

Oh that has to do with playing the correct animations. These are 2d sprites with four "facings": UP, DOWN, LEFT, RIGHT, which are #defined as 0, 1, 2, and 3, respectively. Thanks for all of the advice you've all been a great help.

---

### Post by fr4nko on 2009-07-13
> **pepperphd said:**
> Oh that has to do with playing the correct animations. These are 2d sprites with four "facings": UP, DOWN, LEFT, RIGHT, which are #defined as 0, 1, 2, and 3, respectively. Thanks for all of the advice you've all been a great help.
This is ok, what I didn't understood is the logic behind the code you are using to set up 'current_facing'. I was trying to understand the logic of the code to write it in a more compact vectorial form.

Francesco

---

### Post by pepperphd on 2009-07-13
> **fr4nko said:**
> This is ok, what I didn't understood is the logic behind the code you are using to set up 'current_facing'. I was trying to understand the logic of the code to write it in a more compact vectorial form.<br />
<br />
Francesco<br />
<br />

Okay. This is one of those times I think I'll have an easier time writing code like this than explaining it, because I can't quite picture in my head why it works but after testing it just works anyway.
```

ydiff = abs(player.coll_box.y) - abs(hit_box.y);
xdiff = abs(player.coll_box.x) - abs(hit_box.x);

```These two lines find the difference between the players coordinates and the mobs. Actually, now that I look at it, I don't need abs() in these two lines because a boxes x and y should never be below 0. Maybe thats why you were confused.  In the following (which is later in the function) it is however important:

```
if(abs(xdiff) > abs(ydiff))
{
        if(x_vel > 0)
                 current_facing = RIGHT;
        else     current_facing = LEFT;
}    
else
{
    if(y_vel > 0)
            current_facing = DOWN;
    else    current_facing = UP;
}
```This will take the values of the xdiff and ydiff numbers, which because I always subtract the mobs hit box from the players, may be negative.  First it divides the choices in half by determining whether the player is further away on the X or Y axis.  It then measures the mobs velocity along the axis on which the mob has greater velocity. If negative means the mob is moving LEFT or UP, and if positive means RIGHT or DOWN.

If the player is is 1 pixel away on the y axis and 100 away on the x axis, the mob should obviously be facing either right or left but not up or down.  That is what this solves.

Is this what you had trouble understanding?

---

### Post by fr4nko on 2009-07-13
Well I think you are doing confusion because you have not decided if the facing is determined by the velocity or by the relative position of the player respect to the hit box.

Anyway, I think you could write a function vector_get_direction that, given a vector returns the direction so that you can use it for whatever vector you want. You should pass the components of the vector that determinate the facing.

Here two possible implementation of the functions:
```
enum {
  RIGHT = 0,
  UP    = 1,
  LEFT  = 2,
  DOWN  = 3
};

int
vector_get_direction (float x, float y)
{
  int dir;

  if (x > 0)
    {
      if (y < x && y > -x)
    dir = RIGHT;
      else
    dir = (y > 0 ? UP : DOWN);
    }
  else
    {
      if (y < -x && y > x)
    dir = LEFT;
      else
    dir = (y > 0 ? UP : DOWN);
    }
  return dir;
}

int
vector_get_direction_2 (float x, float y)
{
  float xt = M_SQRT1_2 * (x - y), yt = M_SQRT1_2 * (x + y);
  int quad = floor(atan2 (yt, xt) / M_PI_2);
  return (quad < 0 ? quad + 4 : quad);
}

```the two functions gives the same results, the first one is more efficient, the second is more elegant. The first implementation is very similar to your code but note that by using this function you can improve the readability of the body of your main function.

I hope that helps.

Francesco

---


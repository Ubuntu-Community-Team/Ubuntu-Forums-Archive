---
title: "[SOLVED] Making a VERY simple game in C"
date: 2008-11-03
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-03
I wanted to make a very simple 2D space shooter in C, just to learn more C.

Started making it with SDL and OpenGL. Everything went fine, until I came across this problem:

What if I want to make my ship to shoot a missile, how can I have infinites missiles?
Like an array/list or something? When players shoots, there will be a missile. Shoot again, another one. 
And so on, it would be possible to have infinites missiles at the time.


I have done this before in python, but now, when I am learning C, I got no idea about this.

Everything is different in C, and because I got no teachers, no friends, or anybody who knows C and could help, I am stuck.


Could someone post me a small example, how to have data structure for missile, a list of missiles, and a function, 
which creates a missile, and adds it to the list?


Thanks.

---

### Post by pp. on 2008-11-03
> **crazyfuturamanoob said:**
> how can I have infinites missiles?

I don't see the problem. While a real ship has a counted number of real missiles, a programmed 'ship' does not. Just fire away and forget about counting the shots. It would be rather more strange if your simple 2D game ship had anything but an infinite number of missiles.

---

### Post by DrMega on 2008-11-03
It sounds like you're already on the right track. You just need an array of fixed size to hold the current coordinates and vectors of your missiles, along with a status indicator to say if it is current or not. A function to create a new one would look for the first "non-current" entry in the array, and set new coordinates and vectors in it. Make the array larger than the max number of missiles allowed (you said infinite but that's not practical). Then in your main loop, scan the array and add the x and y vectors to the x and y coordinates for each current entry in your missile array (so they move up the screen) and test for a collision with your other objects.

---

### Post by kknd on 2008-11-03
> **crazyfuturamanoob said:**
> 
What if I want to make my ship to shoot a missile, how can I have infinites missiles?
Like an array/list or something? When players shoots, there will be a missile. Shoot again, another one. 
And so on, it would be possible to have infinites missiles at the time.



You can mantain a linked list, and traverse it in each frame, updating the position and rendering each missile.

When a missile explode or goes out of scope, you simply remove it from the list (and free it if its dynamically allocated).

---

### Post by Sockerdrickan on 2008-11-03
#4 is right

---

### Post by DrMega on 2008-11-03
> **Tux0r said:**
> #4 is right

Number 4 is the best way, but let us not forget that the OP is just learning C, and linked lists in original C are not the simplest construct for beginners to get their head around. That's why I suggested the array method.

---

### Post by jimi_hendrix on 2008-11-03
i like the array method personally...coincidentally, before i sold my sole to my insane history class i was going to make a galaga clone with sdl...

---

### Post by Geekkit on 2008-11-03
The word 'simple' and 'C' in the same sentence? Not sure about that. ;)

Seriously though I think you can have your cake and eat it too. That is, you can have an array and an infinite number of missiles - or at least the perception of an infinite number of missiles being fired.

Figure out how large your screen is going to be and then figure out the size (height) of the missile. You most likely don't want to shoot missiles out over top of each other (wouldn't make the game very challenging) so you could use this as a starting point:

(screen height / missile height) + 1 = size of array

Then simply cycle the missiles. As a missile goes off screen, reset it's coordinates to the ship and then recycle.

If you have a rather large number of enemies coming however this might not work. In which case you could simply create a rather large array:

( 10 x (screen height / missile height)) = size of array

And simply cycle through them. I think cycling through them will be faster than using a linked list and creating objects in memory and then freeing memory up. With the array, you're almost like a stage manager telling the missile sprites if they go off the top of the stage, to go back to the bottom of the stage and be invisible until called up again. This has the advantage of not allocating/deallocating in memory which can be costly in performance and it will keep your game from suddenly drawing upon huge amounts of main memory.

Pseudo code would be something like (this would go within your drawing routing):

```
for each element in missile sprite array
  check to see if on_stage flag is set to on and if it is
    if currently indexed missile sprite y + height < 0
      set sprite to invisible, reset coordinates
    else if missile sprite hit enemy
      do scoring/explosion effects/other state checking
    else
      redraw said missile sprite using velocity and vector trajectory
end for
```

That's how I've done it in the past and it seems to work for me (not necessarily saying this is the only way or that it's the best either).

---

### Post by LaRoza on 2008-11-03
> **jimi_hendrix said:**
> i like the array method personally...coincidentally, before i sold my sole to my insane history class i was going to make a galaga clone with sdl...

What do you walk on?

> **Geekkit said:**
> The word 'simple' and 'C' in the same sentence? Not sure about that. ;)

C is extremely simple.

---

### Post by pp. on 2008-11-04
> **LaRoza said:**
> What do you walk on?

On borrowed soles, as you can C.

---

### Post by Geekkit on 2008-11-04
> **pp. said:**
> On borrowed soles, as you can C.

*groan* ... that was terrible ... both of you. :p

---

### Post by DrMega on 2008-11-04
> **jimi_hendrix said:**
> i sold my sole

> **LaRoza said:**
> What do you walk on?

He (or she) only said they sold one sole (ie "sole" note "soles") so they can hop.

---

### Post by Ferrat on 2008-11-04
> **DrMega said:**
> He (or she) only said they sold one sole (ie "sole" note "soles") so they can hop.

I can only speak for myself ofc. but I can walk normally without any soles?
And I usually walk on the ground or the floor :p

---

### Post by DrMega on 2008-11-04
> **Ferrat said:**
> I can only speak for myself ofc. but I can walk normally without any soles?
And I usually walk on the ground or the floor :p

One of my favourite meals is grilled sole with steamed seasonal vegatables.

---

### Post by crazyfuturamanoob on 2008-11-04
What type the list should be? I tried **int** but it can't store structs. :confused:

**int missiles[200];** will result in [B]error: incompatible types in assignment
[/B] when I add **structs** to that array.

---

### Post by DrMega on 2008-11-04
> **crazyfuturamanoob said:**
> What type the list should be? I tried **int** but it can't store structs. :confused:

**int missiles[200];** will result in [B]error: incompatible types in assignment
[/B] when I add **structs** to that array.

If I remember my old C days right, when you define a struct you give it a name. The name you choose becomes a new type, and you make an array of that type.

---

### Post by nvteighen on 2008-11-04
> **crazyfuturamanoob said:**
> What type the list should be? I tried **int** but it can't store structs. :confused:

**int missiles[200];** will result in [B]error: incompatible types in assignment
[/B] when I add **structs** to that array.
"**struct**" is not a data type, but a keyword. But, "**struct name**" is a data type.

If you want an array of x's (be x whatever data type you like), you use **x blah[n];** (where *n* is an **unsigned int**). So, if you want an array of **struct name** data, you use **struct name blah[n]**.

The syntax of **struct** is really confusing at the beginning... and also for not-so-beginners. That's why (almost) always using **typedef** saves a lot of unnecessary struggle. But the rule of thumb is the one I wrote at the first paragraph: **struct** + the data type name = data type.

---

### Post by crazyfuturamanoob on 2008-11-04
> **nvteighen said:**
> "**struct**" is not a data type, but a keyword. But, "**struct name**" is a data type.

If you want an array of x's (be x whatever data type you like), you use **x blah[n];** (where *n* is an **unsigned int**). So, if you want an array of **struct name** data, you use **struct name blah[n]**.

The syntax of **struct** is really confusing at the beginning... and also for not-so-beginners. That's why (almost) always using **typedef** saves a lot of unnecessary struggle. But the rule of thumb is the one I wrote at the first paragraph: **struct** + the data type name = data type.

Will I have to use typedef when creating the struct array? Or only when making the data structure for a missile?

---

### Post by crazyfuturamanoob on 2008-11-04
I tried this:
```

    /* a simple missile system */
    struct int missiles[MAX_MISSILES];
    
    typedef struct
    {
        int on_stage;
        int x, y;
        int speed;
    } Missile;
    
    /* empty the array */
    Missile nomissile = {0, 0, 0, 0};
    int index;
    for (index = 0; index<MAX_MISSILES; index++)
    {
        missiles[index] = nomissile;
    }
```
I get errors when I try to compile it. Something is wrong with the first line.

---

### Post by LaRoza on 2008-11-04
> **crazyfuturamanoob said:**
> 
I get errors when I try to compile it. Something is wrong with the first line.

Only 7 minutes? Try fixing it ;) Debugging is a pain, but it is an essential skill to acquire and you need to practice it.

---

### Post by crazyfuturamanoob on 2008-11-04
> **LaRoza said:**
> Only 7 minutes? Try fixing it ;) Debugging is a pain, but it is an essential skill to acquire and you need to practice it.

Easy to debug when I don't know nearly anything about C...

---

### Post by LaRoza on 2008-11-04
> **crazyfuturamanoob said:**
> Easy to debug when I don't know nearly anything about C...

I don't understand what you mean. 

If you are in the beginning stages of making this game, then you should use what you do know for the basis and learn the rest. If you overstep, you'll be stuck with code you don't understand, and your game will be sunk.

---

### Post by crazyfuturamanoob on 2008-11-04
I am trying to make this game just to learn the things I need to know to be able to make it.

Also, looked at pacman's source code: **Missile missiles[MAX_MISSILES];** :)

---

### Post by nvteighen on 2008-11-04
> **crazyfuturamanoob said:**
> I tried this:
```

    /* a simple missile system */
    struct int missiles[MAX_MISSILES];
    
    typedef struct
    {
        int on_stage;
        int x, y;
        int speed;
    } Missile;
    
    /* empty the array */
    Missile nomissile = {0, 0, 0, 0};
    int index;
    for (index = 0; index<MAX_MISSILES; index++)
    {
        missiles[index] = nomissile;
    }
```
I get errors when I try to compile it. Something is wrong with the first line.
Erm...

What the hell is "struct int"? Is that logical in the C "language system"?

---

### Post by DrMega on 2008-11-04
> **crazyfuturamanoob said:**
> I tried this:
```

    /* a simple missile system */
    struct int missiles[MAX_MISSILES];
    /**** DM: The above is a syntax error****/
    
    typedef struct
    {
        int on_stage;
        int x, y;
        int speed;
    } Missile;

    /**** DM: */
    Missile missileArray[MAX_MISSILES];
    int missileArrayIndex = 0;
    
    /* empty the array */
    Missile nomissile = {0, 0, 0, 0};
    int index;
    for (index = 0; index<MAX_MISSILES; index++)
    {
        missiles[index] = nomissile;
    }
```
I get errors when I try to compile it. Something is wrong with the first line.

You were nearly there I reckon.

> **nvteighen said:**
> Erm...

What the hell is "struct int"? Is that logical in the C "language system"?

That lad (or lass) has already said they are just learning C. Let's go easy:)

---

### Post by crazyfuturamanoob on 2008-11-04
[quote=DrMega]That lad (or lass) has already said they are just learning C. Let's go easy :)[/quote]
Yep, started a week or two ago.

---

### Post by nvteighen on 2008-11-04
> **DrMega said:**
> Y
That lad (or lass) has already said they are just learning C. Let's go easy:)

> **crazyfuturamanoob said:**
> Yep, started a week or two ago.

Oh, sorry of I was rude.

What I meant is if you can explain "struct int" in C's way to do things or not. Sometimes, just looking at the logic behind a language will tell you what's wrong (well, assuming the language is correctly designed... and there's no doubt C is).

Again, sorry.

---

### Post by Lux Perpetua on 2008-11-04
> **crazyfuturamanoob said:**
> What if I want to make my ship to shoot a missile, how can I have infinites missiles?
Like an array/list or something? When players shoots, there will be a missile. Shoot again, another one. 
And so on, it would be possible to have infinites missiles at the time.Old games like this only allowed a fixed number of shots on screen at one time. By "fixed", I mean typically three or even fewer. So you are well within your rights to do the same. Since you specified that your game was to be "very simple," my advice is to follow suit here.

---

### Post by DrMega on 2008-11-04
> **Lux Perpetua said:**
> Old games like this only allowed a fixed number of shots on screen at one time. By "fixed", I mean typically three or even fewer. So you are well within your rights to do the same. Since you specified that your game was to be "very simple," my advice is to follow suit here.

Old games imposed such limits because of the hardware of the day. With severe limitations on memory and even more severe on CPU (which also had to do most of the work a modern graphics card does, as there were very few co-processors back then). Managing more than a handful of sprites at any one time would have meant severe slowdowns during game play.

As for development complexity, it is no more or less complicated to manage 3 simultaneous sprites as it is to manage 3 billion. The only limitation is on the hardware (and of course practicals of screen size and playability).

---

### Post by Bichromat on 2008-11-04
> **nvteighen said:**
> (well, assuming the language is correctly designed... and there's no doubt C is)
Correctly designed ? :lolflag:

---

### Post by crazyfuturamanoob on 2008-11-05
> **Lux Perpetua said:**
> Old games like this only allowed a fixed number of shots on screen at one time. By "fixed", I mean typically three or even fewer. So you are well within your rights to do the same. Since you specified that your game was to be "very simple," my advice is to follow suit here.

Well, I managed to make this thing with arrays. 

There is no laag, even when the array's size is 5000, but that's probably my 4Gb RAM, which never fills up.

And there won't be 5000 missiles on the screen at the same time, probably.


But is there a faster way to do this, because having 5000 idle missiles with variable *on_stage 0* will eat memory.
What if and when each missiles has variables such as position, speed, direction, maybe gravity, particle effects, acceleration and stuff?

It will use a lot memory. Perhaps there is a way to dynamically extend and decrease the array? Like having only active missiles in the array at the time. When they get destroyed, shorten array by 1?

Like arrays/lists in python. They can be dynamically extended and shortened, why not arrays in C then? C is lower level.

---

### Post by DrMega on 2008-11-05
> **Bichromat said:**
> Correctly designed ? :lolflag:

It was correctly designed back in the days when it was designed. We have to remember that at the time, we had the likes of COBOL and FORTRAN, which were awful languages, or assembly, which of course was machine specific and very tedious. C was high level enough to write readable, maintainable code, but low level enough to do much of what would have previously been done in assembly.

> **crazyfuturamanoob said:**
> Well, I managed to make this thing with arrays. 

There is no laag, even when the array's size is 5000, but that's probably my 4Gb RAM, which never fills up.

And there won't be 5000 missiles on the screen at the same time, probably.


But is there a faster way to do this, because having 5000 idle missiles with variable *on_stage 0* will eat memory.
What if and when each missiles has variables such as position, speed, direction, maybe gravity, particle effects, acceleration and stuff?

It will use a lot memory. Perhaps there is a way to dynamically extend and decrease the array? Like having only active missiles in the array at the time. When they get destroyed, shorten array by 1?

Like arrays/lists in python. They can be dynamically extended and shortened, why not arrays in C then? C is lower level.

You don't need dynamic arrays (and to do them in C you have to mess about with pointers and memory allocation).

Keep an integer variable that holds the array index of the last used entry, and in all your loops when looping through the array, only loop up to that number.

When a missile is 'dead' (off screen, exploded, etc), set a flag in its entry (have an 'active' property in your struct perhaps) to indicate it is finished.

Have a new function that creates a missile. This function would scan your array and look for the first 'dead' missile entry and reuse it. If there are no such entries it would simply increment your 'last array index used variable and use the next available entry.

---

### Post by Bichromat on 2008-11-05
> **DrMega said:**
> It was correctly designed back in the days when it was designed.
Actually, I was thinking about messed up operator associativity and precedence, the use of '*' for multiplications, pointers and commentaries, and some other quirks.

---

### Post by DrMega on 2008-11-05
> **Bichromat said:**
> Actually, I was thinking about messed up operator associativity and precedence, the use of '*' for multiplications, pointers and commentaries, and some other quirks.

It was designed by programmers, not mathematicians, so we have to allow it it's little quirks.

As for the asterisk being used in loads of situations, I think that's OK. It is usually quite clearly what context it is being used in.

You could say that a car designed in the 1970's had a bad design because technology has moved on so far and we've learned so much since then. A programming language is no different in this respect.

---

### Post by nvteighen on 2008-11-05
> **Bichromat said:**
> Correctly designed ? :lolflag:

Well, C is fairly coninstently designed. Logical consistence is the main goal of any logical-formal language (like programming languages are)... The only quirks there is is the use of **};** in structs, unions and enums, which contradicts the general rule of "no semicolons needed after a code block ({ })".

> **DrMega said:**
> It was correctly designed back in the days when it was designed. We have to remember that at the time, we had the likes of COBOL and FORTRAN, which were awful languages, or assembly, which of course was machine specific and very tedious. C was high level enough to write readable, maintainable code, but low level enough to do much of what would have previously been done in assembly.


Why "**was** it correctly designed"? I think it's still correctly designed and the various modifications it underwent all respected the original design.

> **Bichromat said:**
> Actually, I was thinking about messed up operator associativity and precedence, the use of '*' for multiplications, pointers and commentaries, and some other quirks.

That's wrong. You can easily tell what a '*' is doing by simply looking at the code: if it's used as an unary operator, it's the dereference operator; if it's used as binary, multiplication; and if not used as an operator, but just as part of the strings "/*" or "*/" it's in a commentary. 

In languages supporting operator overloading, that's not quite simple to do, as you could have multiple binary '*' doing several and even unrelated stuff... In that case, it will be the operands which will define the operator's behaivor.

---

### Post by crazyfuturamanoob on 2008-11-05
I finally finished that game. Here you go, save as gltest.c, in 689 lines.
```

[color=#BC7A00] 
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <math.h>
#include <GL/gl.h>
#include <GL/glu.h>
#include "SDL.h"

# define pi 3.14159265358979323846
[/color]
[color=#408080]*/* screen width, height, and bit depth */*[/color]
[color=#BC7A00]#define SCREEN_WIDTH  640
#define SCREEN_HEIGHT 480
#define SCREEN_BPP     16
[/color]
[color=#408080]*/* Set up some booleans */*[/color]
[color=#BC7A00]#define TRUE  1
#define FALSE 0

#define MAX_MISSILES 200
#define MISSILE_SPEED 15
#define SHOOT_DELAY 6
#define MISSILE_SIZE 10

#define MAX_ENEMIES 200
#define ENEMY_SPEED 14
[/color][color=#B00040]int[/color] ENEMY_SPAWN_RATE [color=#666666]=[/color] [color=#666666]30[/color];
[color=#BC7A00]#define ENEMY_SPAWN_RATE_DECR 2

#define player_speed  12
#define muzzle_flash_size 100
[/color]
[color=#408080]*/* maximum distance outside window until missiles are destroyed */*[/color]
[color=#BC7A00]#define MISSILE_MAX_DIST 100
[/color]
[color=#408080]*/* player's variables. PLAYER'S DIAMETER IS 40 PIXELS! */*[/color]
[color=#B00040]int[/color] player_pos[[color=#666666]2[/color]] [color=#666666]=[/color] {[color=#666666]240[/color], [color=#666666]420[/color]};

[color=#B00040]int[/color] player_can_shoot [color=#666666]=[/color] [color=#666666]1[/color];
[color=#B00040]int[/color] player_shoot_alarm [color=#666666]=[/color] [color=#666666]0[/color];
[color=#B00040]int[/color] player_muzzle_flash [color=#666666]=[/color] [color=#666666]0[/color];
[color=#B00040]int[/color] player_on_stage [color=#666666]=[/color] [color=#666666]1[/color];

[color=#B00040]int[/color] ticks_to_death [color=#666666]=[/color] [color=#666666]60[/color];

[color=#408080]*/* structure for enemy ships */*[/color]
[color=#008000]**typedef**[/color] [color=#008000]**struct**[/color]
{
    [color=#B00040]int[/color] on_stage;
    [color=#B00040]int[/color] x, y;
    [color=#B00040]int[/color] can_shoot;
    [color=#B00040]int[/color] muzzle_flash;
} Enemy;
Enemy enemies[MAX_ENEMIES];

[color=#408080]*/* data structure for missile */*[/color]
[color=#008000]**typedef**[/color] [color=#008000]**struct**[/color]
{
    [color=#B00040]int[/color] on_stage;
    [color=#B00040]int[/color] x, y;
    [color=#B00040]int[/color] speed;
} Missile;

[color=#408080]*/* make a simple missile system */*[/color]
Missile missiles[MAX_MISSILES];

[color=#408080]*/* the background grid */*[/color]
[color=#B00040]int[/color] grid_offset [color=#666666]=[/color] [color=#666666]0[/color];
[color=#B00040]int[/color] grid_speed [color=#666666]=[/color] [color=#666666]2[/color];
[color=#B00040]int[/color] grid_size [color=#666666]=[/color] [color=#666666]32[/color];

[color=#B00040]float[/color] [color=#0000FF]radians[/color]( [color=#B00040]int[/color] degrees )
{
    [color=#B00040]float[/color] radians [color=#666666]=[/color] pi [color=#666666]*[/color] [color=#666666]180[/color] [color=#666666]/[/color] degrees;
    [color=#008000]**return**[/color] radians;
}

[color=#B00040]int[/color] [color=#0000FF]degrees[/color]( [color=#B00040]int[/color] radians )
{
    [color=#B00040]int[/color] degrees [color=#666666]=[/color] [color=#666666]180[/color] [color=#666666]*[/color] radians [color=#666666]/[/color] pi;
    [color=#008000]**return**[/color] degrees;
}

[color=#408080][i]/* function to check if a point is inside rect.

boxcheck( x1, y1, box_size, x2, y2 ); */[/i][/color]

[color=#008000]**typedef**[/color] [color=#008000]**struct**[/color] { [color=#B00040]int[/color] left, top, right, bottom; } Box;
[color=#B00040]int[/color] [color=#0000FF]boxcheck[/color]( [color=#B00040]int[/color] x1, [color=#B00040]int[/color] y1, [color=#B00040]int[/color] box_size, [color=#B00040]int[/color] x2, [color=#B00040]int[/color] y2 )
{
    [color=#408080]*/* x1 and y1 are the center of box, whichs is box_size * 2 big. x2 and y2 are the point to check */*[/color]
    Box bb1 [color=#666666]=[/color] {x1[color=#666666]-[/color]box_size[color=#666666]/[/color][color=#666666]2[/color], y1[color=#666666]-[/color]box_size[color=#666666]/[/color][color=#666666]2[/color], x1[color=#666666]+[/color]box_size[color=#666666]/[/color][color=#666666]2[/color], y1[color=#666666]+[/color]box_size[color=#666666]/[/color][color=#666666]2[/color]};
    [color=#B00040]int[/color] pass_x, pass_y;
    pass_x [color=#666666]=[/color] [color=#666666]0[/color];
    pass_y [color=#666666]=[/color] [color=#666666]0[/color];
    [color=#408080]*/* check for x */*[/color]
    [color=#008000]**if**[/color] ( (x2 [color=#666666]>[/color] bb1.left) [color=#666666]&&[/color] (x2 [color=#666666]<[/color] bb1.right) )
        pass_x [color=#666666]=[/color] [color=#666666]1[/color];
    [color=#408080]*/* and y */*[/color]
    [color=#008000]**if**[/color] ( (y2 [color=#666666]>[/color] bb1.top) [color=#666666]&&[/color] (y2 [color=#666666]<[/color] bb1.bottom) )
        pass_y [color=#666666]=[/color] [color=#666666]1[/color];
    [color=#408080]*/* if both x and y pass then return 1 */*[/color]
    [color=#008000]**if**[/color] (pass_x [color=#666666]&&[/color] pass_y)
        [color=#008000]**return**[/color] [color=#666666]1[/color];
    [color=#408080]*/* otherwise, return 0 */*[/color]
    [color=#008000]**return**[/color] [color=#666666]0[/color];
}

[color=#B00040]void[/color] [color=#0000FF]draw_lightsplash[/color]( [color=#B00040]int[/color] x, [color=#B00040]int[/color] y, [color=#B00040]int[/color] radius, [color=#B00040]int[/color] accuracy )
{
    glBegin(GL_TRIANGLE_FAN);
    
    glColor4ub([color=#666666]230[/color], [color=#666666]230[/color], [color=#666666]156[/color], [color=#666666]215[/color]);
    
    glVertex2f( x, y );
    
    glColor4ub([color=#666666]230[/color], [color=#666666]230[/color], [color=#666666]156[/color], [color=#666666]0[/color]);
    
    [color=#B00040]int[/color] angle;
    [color=#B00040]float[/color] theta;
    
    [color=#B00040]int[/color] step [color=#666666]=[/color] ([color=#666666]360[/color] [color=#666666]/[/color] accuracy);
    
    [color=#008000]**for**[/color] (angle [color=#666666]=[/color] [color=#666666]0[/color]; angle[color=#666666]<[/color][color=#666666]360[/color]; angle [color=#666666]+=[/color] step)
    {
        theta [color=#666666]=[/color] pi [color=#666666]*[/color] angle [color=#666666]/[/color] [color=#666666]180[/color];
        glVertex2f( x [color=#666666]+[/color] radius[color=#666666]*[/color]cos(theta), y [color=#666666]+[/color] radius[color=#666666]*[/color]sin(theta) );
    }
    
    glVertex2f( x [color=#666666]+[/color] radius , y );
    
    glEnd();
}

[color=#B00040]void[/color] [color=#0000FF]draw_player[/color] ( )
{
    glLoadIdentity();
    [color=#408080]*/* translate to player's position */*[/color]
    glTranslatef ( player_pos[[color=#666666]0[/color]], player_pos[[color=#666666]1[/color]], [color=#666666]0[/color] );
    
    [color=#408080]*/* draw partially transparent green triangle */*[/color]
    glBegin(GL_TRIANGLES);
    glColor4ub([color=#666666]0[/color], [color=#666666]230[/color], [color=#666666]0[/color], [color=#666666]170[/color]);
    glVertex2f([color=#666666]0[/color], [color=#666666]-[/color][color=#666666]15[/color]);
    glVertex2f([color=#666666]-[/color][color=#666666]20[/color], [color=#666666]15[/color]);
    glVertex2f([color=#666666]20[/color], [color=#666666]15[/color]);
    glEnd();
    
    [color=#408080]*/* draw outlines */*[/color]
    glLineWidth([color=#666666]3[/color]);
    glBegin(GL_LINE_LOOP);
    glColor4ub([color=#666666]0[/color], [color=#666666]255[/color], [color=#666666]0[/color], [color=#666666]200[/color]);
    glVertex2f([color=#666666]0[/color], [color=#666666]-[/color][color=#666666]15[/color]);
    glVertex2f([color=#666666]-[/color][color=#666666]20[/color], [color=#666666]15[/color]);
    glVertex2f([color=#666666]20[/color], [color=#666666]15[/color]);
    glEnd();
    glLineWidth([color=#666666]1[/color]);
    
    glLoadIdentity();
}

[color=#B00040]void[/color] [color=#0000FF]update_player[/color] ( )
{
    [color=#008000]**if**[/color] (player_on_stage [color=#666666]==[/color] [color=#666666]1[/color])
    {
            [color=#B00040]int[/color] e;
            [color=#008000]**for**[/color] (e [color=#666666]=[/color] [color=#666666]0[/color]; e[color=#666666]<[/color]MAX_ENEMIES; e[color=#666666]++[/color])
            {
                [color=#008000]**if**[/color] (boxcheck(player_pos[[color=#666666]0[/color]], player_pos[[color=#666666]1[/color]], [color=#666666]80[/color], enemies[e].x, enemies[e].y))
                {
                    player_on_stage [color=#666666]=[/color] [color=#666666]0[/color];
                    player_muzzle_flash [color=#666666]=[/color] [color=#666666]3[/color];
                }
            }
    }
}

[color=#B00040]int[/color] [color=#0000FF]add_enemy[/color]( [color=#B00040]int[/color] x, [color=#B00040]int[/color] y )
{
    [color=#B00040]int[/color] i;
    [color=#008000]**for**[/color] (i [color=#666666]=[/color] [color=#666666]0[/color]; i[color=#666666]<[/color]MAX_ENEMIES; i[color=#666666]++[/color])
    {
        [color=#008000]**if**[/color] (enemies[i].on_stage [color=#666666]==[/color] [color=#666666]0[/color])
        {
            enemies[i].on_stage [color=#666666]=[/color] [color=#666666]1[/color];
            enemies[i].x [color=#666666]=[/color] x;
            enemies[i].y [color=#666666]=[/color] y;
            enemies[i].can_shoot [color=#666666]=[/color] [color=#666666]1[/color];
            enemies[i].muzzle_flash [color=#666666]=[/color] [color=#666666]0[/color];
            [color=#408080]*/* return index of enemy */*[/color]
            [color=#008000]**return**[/color] i;
        }
    }
    [color=#408080]*/* no empty space for new enemy found, return -1 for error */*[/color]
    [color=#008000]**return**[/color] [color=#666666]-[/color][color=#666666]1[/color];
}

[color=#B00040]void[/color] [color=#0000FF]update_enemies[/color] ( )
{
    [color=#B00040]int[/color] e, m;
    [color=#008000]**for**[/color] (e [color=#666666]=[/color] [color=#666666]0[/color]; e[color=#666666]<[/color]MAX_ENEMIES; e[color=#666666]++[/color])
    {
        [color=#008000]**if**[/color] (enemies[e].on_stage [color=#666666]==[/color] [color=#666666]1[/color])
        {
            enemies[e].y [color=#666666]+=[/color] ENEMY_SPEED;
            [color=#408080]*/* kill this e if it is outside window, same max dist as missiles */*[/color]
            [color=#008000]**if**[/color] ( (enemies[e].y [color=#666666]<[/color] [color=#666666]-[/color]MISSILE_MAX_DIST ) [color=#666666]||[/color] (enemies[e].y [color=#666666]>[/color] SCREEN_HEIGHT[color=#666666]+[/color]MISSILE_MAX_DIST ) [color=#666666]||[/color] (enemies[e].x [color=#666666]<[/color] [color=#666666]-[/color]MISSILE_MAX_DIST ) [color=#666666]||[/color] (enemies[e].x [color=#666666]>[/color] SCREEN_WIDTH[color=#666666]+[/color]MISSILE_MAX_DIST ) )
                enemies[e].on_stage [color=#666666]=[/color] [color=#666666]0[/color];
            [color=#008000]**for**[/color] (m [color=#666666]=[/color] [color=#666666]0[/color]; m[color=#666666]<[/color]MAX_MISSILES; m[color=#666666]++[/color])
            {
                [color=#008000]**if**[/color] (boxcheck(enemies[e].x, enemies[e].y, [color=#666666]40[/color], missiles[m].x, missiles[m].y) [color=#666666]==[/color] [color=#666666]1[/color])
                {
                    enemies[e].on_stage [color=#666666]=[/color] [color=#666666]0[/color];
                    enemies[e].muzzle_flash [color=#666666]=[/color] [color=#666666]2[/color];
                }
            }
        }
    }
}

[color=#B00040]void[/color] [color=#0000FF]draw_enemies[/color] ( )
{
    [color=#B00040]int[/color] e;
    [color=#008000]**for**[/color] (e [color=#666666]=[/color] [color=#666666]0[/color]; e[color=#666666]<[/color]MAX_ENEMIES; e[color=#666666]++[/color])
    {
        [color=#008000]**if**[/color] (enemies[e].on_stage [color=#666666]==[/color] [color=#666666]1[/color])
        {
            glLoadIdentity();
            [color=#408080]*/* translate to enemy's position */*[/color]
            glTranslatef ( enemies[e].x, enemies[e].y, [color=#666666]0[/color] );
            glRotatef( [color=#666666]180[/color], [color=#666666]0[/color], [color=#666666]0[/color], [color=#666666]1[/color] );
            
            [color=#408080]*/* draw partially transparent green triangle */*[/color]
            glBegin(GL_TRIANGLES);
            glColor4ub([color=#666666]230[/color], [color=#666666]64[/color], [color=#666666]0[/color], [color=#666666]170[/color]);
            glVertex2f([color=#666666]0[/color], [color=#666666]-[/color][color=#666666]15[/color]);
            glVertex2f([color=#666666]-[/color][color=#666666]20[/color], [color=#666666]15[/color]);
            glVertex2f([color=#666666]20[/color], [color=#666666]15[/color]);
            glEnd();
            
            [color=#408080]*/* draw outlines */*[/color]
            glLineWidth([color=#666666]3[/color]);
            glBegin(GL_LINE_LOOP);
            glColor4ub([color=#666666]255[/color], [color=#666666]64[/color], [color=#666666]0[/color], [color=#666666]200[/color]);
            glVertex2f([color=#666666]0[/color], [color=#666666]-[/color][color=#666666]15[/color]);
            glVertex2f([color=#666666]-[/color][color=#666666]20[/color], [color=#666666]15[/color]);
            glVertex2f([color=#666666]20[/color], [color=#666666]15[/color]);
            glEnd();
            glLineWidth([color=#666666]1[/color]);
            
            glLoadIdentity();
        }
        [color=#408080]*/* now possible muzzle flash */*[/color]
        [color=#008000]**if**[/color] (enemies[e].muzzle_flash [color=#666666]>=[/color] [color=#666666]1[/color])
        {
            draw_lightsplash( enemies[e].x, enemies[e].y[color=#666666]+[/color][color=#666666]20[/color], muzzle_flash_size, [color=#666666]36[/color]);
            enemies[e].muzzle_flash [color=#666666]-=[/color] [color=#666666]1[/color];
        }
    }
}

[color=#B00040]int[/color] [color=#0000FF]add_missile[/color]([color=#B00040]int[/color] x, [color=#B00040]int[/color] y, [color=#B00040]int[/color] speed)
{
    [color=#408080]*/* i niinkuin index */*[/color]
    [color=#B00040]int[/color] i;
    [color=#008000]**for**[/color] (i [color=#666666]=[/color] [color=#666666]0[/color]; i[color=#666666]<[/color]MAX_MISSILES; i[color=#666666]++[/color])
    {
        [color=#008000]**if**[/color] (missiles[i].on_stage [color=#666666]==[/color] [color=#666666]0[/color])
        {
            missiles[i].on_stage [color=#666666]=[/color] [color=#666666]1[/color];
            missiles[i].x [color=#666666]=[/color] x;
            missiles[i].y [color=#666666]=[/color] y;
            missiles[i].speed [color=#666666]=[/color] speed;
            [color=#408080]*/* return index of missile in the list */*[/color]
            [color=#008000]**return**[/color] i;
        }
    }
    [color=#408080]*/* if not found empty missile slot, then return -1 for error */*[/color]
    [color=#008000]**return**[/color] [color=#666666]-[/color][color=#666666]1[/color];
}

[color=#B00040]void[/color] [color=#0000FF]update_missiles[/color]()
{
    [color=#B00040]int[/color] ind;
    [color=#008000]**for**[/color] (ind [color=#666666]=[/color] [color=#666666]0[/color]; ind[color=#666666]<[/color]MAX_MISSILES; ind[color=#666666]++[/color])
    {
        [color=#008000]**if**[/color] (missiles[ind].on_stage [color=#666666]==[/color] [color=#666666]1[/color])
        {
            missiles[ind].y [color=#666666]+=[/color] missiles[ind].speed;
            [color=#408080]*/* if this missile is outside window, the kill it */*[/color]
            [color=#008000]**if**[/color] ( (missiles[ind].y [color=#666666]<[/color] [color=#666666]-[/color]MISSILE_MAX_DIST ) [color=#666666]||[/color] (missiles[ind].y [color=#666666]>[/color] SCREEN_HEIGHT[color=#666666]+[/color]MISSILE_MAX_DIST ) [color=#666666]||[/color] (missiles[ind].x [color=#666666]<[/color] [color=#666666]-[/color]MISSILE_MAX_DIST ) [color=#666666]||[/color] (missiles[ind].x [color=#666666]>[/color] SCREEN_WIDTH[color=#666666]+[/color]MISSILE_MAX_DIST ) )
                missiles[ind].on_stage [color=#666666]=[/color] [color=#666666]0[/color];
        }
    }
}

[color=#B00040]void[/color] [color=#0000FF]draw_missiles[/color]()
{
    
    [color=#B00040]int[/color] m;
    [color=#008000]**for**[/color] (m [color=#666666]=[/color] [color=#666666]0[/color]; m[color=#666666]<[/color]MAX_MISSILES; m[color=#666666]++[/color])
    {
        [color=#408080]*/* if missile exists, then draw it */*[/color]
        [color=#008000]**if**[/color] (missiles[m].on_stage [color=#666666]==[/color] [color=#666666]1[/color])
            draw_lightsplash( missiles[m].x, missiles[m].y, MISSILE_SIZE, [color=#666666]10[/color] );
    }
    
}

[color=#B00040]void[/color] [color=#0000FF]update_grid_position[/color] ()
{
    grid_offset [color=#666666]+=[/color] grid_speed;
    [color=#008000]**if**[/color] (grid_offset [color=#666666]>[/color] grid_size)
        grid_offset [color=#666666]=[/color] [color=#666666]0[/color];
}

[color=#B00040]void[/color] [color=#0000FF]draw_grid[/color] ( )
{
    glBegin(GL_LINES);
    glColor4ub([color=#666666]230[/color], [color=#666666]192[/color], [color=#666666]0[/color], [color=#666666]170[/color]);
    [color=#408080]*/* draw vertical lines */*[/color]
    [color=#B00040]int[/color] width;
    [color=#008000]**for**[/color] (width [color=#666666]=[/color] [color=#666666]0[/color]; width [color=#666666]<[/color] SCREEN_WIDTH; width [color=#666666]+=[/color] grid_size)
    {
        glVertex2f(width, [color=#666666]0[/color]);
        glVertex2f(width, SCREEN_HEIGHT);
    }
    [color=#408080]*/* now horizontal ones */*[/color]
    [color=#B00040]int[/color] height;
    [color=#008000]**for**[/color] (height [color=#666666]=[/color] grid_offset; height [color=#666666]<[/color] SCREEN_HEIGHT; height [color=#666666]+=[/color] grid_size)
    {
        glVertex2f([color=#666666]0[/color], height);
        glVertex2f(SCREEN_WIDTH, height);
    }
    glEnd();
}

[color=#408080]*/* I use this variable to store the state of all keyboard buttons */*[/color]
Uint8 [color=#666666]*[/color]keystate;

[color=#408080]*/* This is our SDL surface */*[/color]
SDL_Surface [color=#666666]*[/color]surface;

[color=#408080]*/* function to release/destroy our resources and restoring the old desktop */*[/color]
[color=#B00040]void[/color] [color=#0000FF]Quit[/color]( [color=#B00040]int[/color] returnCode )
{
    [color=#408080]*/* clean up the window */*[/color]
    SDL_Quit( );

    [color=#408080]*/* and exit appropriately */*[/color]
    exit( returnCode );
}

[color=#408080]*/* function to reset our viewport after a window resize */*[/color]
[color=#B00040]int[/color] [color=#0000FF]resizeWindow[/color]( [color=#B00040]int[/color] width, [color=#B00040]int[/color] height )
{
    [color=#408080]*/* Height / width ration */*[/color]
    GLfloat ratio;
 
    [color=#408080]*/* Protect against a divide by zero */*[/color]
    [color=#008000]**if**[/color] ( height [color=#666666]==[/color] [color=#666666]0[/color] )
    height [color=#666666]=[/color] [color=#666666]1[/color];

    ratio [color=#666666]=[/color] ( GLfloat )width [color=#666666]/[/color] ( GLfloat )height;

    [color=#408080]*/* Setup our viewport. */*[/color]
    glViewport( [color=#666666]0[/color], [color=#666666]0[/color], ( GLint )width, ( GLint )height );

    [color=#408080][i]/*
     * change to the projection matrix and set
     * our viewing volume.
     */[/i][/color]
    glMatrixMode( GL_PROJECTION );
    glLoadIdentity( );

    [color=#408080]*/* Set our perspective */*[/color]
    glOrtho([color=#666666]0[/color], (GLint)width, (GLint)height, [color=#666666]0[/color], [color=#666666]-[/color][color=#666666]1[/color], [color=#666666]1[/color]);

    [color=#408080]*/* Make sure we're chaning the model view and not the projection */*[/color]

    glMatrixMode( GL_MODELVIEW );

    [color=#408080]*/* Reset The View */*[/color]
    glLoadIdentity( );

    [color=#008000]**return**[/color]( TRUE );
}

[color=#408080]*/* function to handle key press events */*[/color]
[color=#B00040]void[/color] [color=#0000FF]handleKeyPress[/color]( SDL_keysym [color=#666666]*[/color]keysym )
{
    [color=#008000]**switch**[/color] ( keysym[color=#666666]->[/color]sym )
    {
    [color=#008000]**case**[/color] SDLK_ESCAPE:
        [color=#408080]*/* ESC key was pressed */*[/color]
        Quit( [color=#666666]0[/color] );
        [color=#008000]**break**[/color];
    [color=#008000]**case**[/color] SDLK_F1:
        [color=#408080][i]/* F1 key was pressed
         * this toggles fullscreen mode
         */[/i][/color]
        SDL_WM_ToggleFullScreen( surface );
        [color=#008000]**break**[/color];
    [color=#008000]**default**[/color][color=#666666]:[/color]
        [color=#008000]**break**[/color];
    }

    [color=#008000]**return**[/color];
}

[color=#408080]*/* general OpenGL initialization function */*[/color]
[color=#B00040]int[/color] [color=#0000FF]initGL[/color]( GLvoid )
{

    [color=#408080]*/* Enable Texture Mapping ( NEW ) */*[/color]
    glEnable( GL_TEXTURE_2D );
    
    [color=#408080]*/* Set the background black */*[/color]
    glClearColor( [color=#666666]0.0f[/color], [color=#666666]0.0f[/color], [color=#666666]0.0f[/color], [color=#666666]1.0f[/color] );

    [color=#408080]*/* Depth buffer setup */*[/color]
    glClearDepth( [color=#666666]1.0f[/color] );

    [color=#408080]*/* Enables Depth Testing */*[/color]
    glDisable( GL_DEPTH_TEST );
    [color=#408080]*/* The Type Of Depth Test To Do */*[/color]
    glDepthFunc( GL_LEQUAL );
    
    [color=#408080]*/* enable alpha/transparency */*[/color]
    glEnable( GL_ALPHA_TEST );
    glAlphaFunc( GL_NOTEQUAL, [color=#666666]0.0f[/color] );
    
    [color=#408080]*/* enable blending */*[/color]
    glEnable( GL_BLEND);
    glBlendFunc( GL_SRC_ALPHA, GL_ONE_MINUS_SRC_ALPHA );

    [color=#008000]**return**[/color]( TRUE );
}

[color=#408080]*/* Here goes our drawing code */*[/color]
[color=#B00040]int[/color] [color=#0000FF]drawGLScene[/color]( GLvoid )
{

    [color=#408080]*/* Clear The Screen And The Depth Buffer */*[/color]
    glClear( GL_COLOR_BUFFER_BIT ); [color=#408080]*/* | GL_DEPTH_BUFFER_BIT ); */*[/color]
    glLoadIdentity();
    
    update_grid_position();
    draw_grid();
    
    update_player();
    [color=#008000]**if**[/color] (player_on_stage [color=#666666]==[/color] [color=#666666]1[/color])
        draw_player();
    
    update_enemies();
    draw_enemies();
    
    update_missiles();
    draw_missiles();
    
    [color=#008000]**if**[/color] (player_muzzle_flash [color=#666666]>=[/color] [color=#666666]1[/color])
    {
        draw_lightsplash( player_pos[[color=#666666]0[/color]], player_pos[[color=#666666]1[/color]][color=#666666]-[/color][color=#666666]20[/color], muzzle_flash_size, [color=#666666]36[/color]);
        player_muzzle_flash [color=#666666]-=[/color] [color=#666666]1[/color];
    }

    [color=#408080]*/* Draw it to the screen */*[/color]
    SDL_GL_SwapBuffers( );

    [color=#008000]**return**[/color]( TRUE );
}

[color=#B00040]int[/color] [color=#0000FF]main[/color]( [color=#B00040]int[/color] argc, [color=#B00040]char[/color] [color=#666666]**[/color]argv )
{
    [color=#408080]*/* empty the array of missiles */*[/color]
    [color=#B00040]int[/color] index;
    [color=#008000]**for**[/color] (index [color=#666666]=[/color] [color=#666666]0[/color]; index[color=#666666]<[/color]MAX_MISSILES; index[color=#666666]++[/color])
    {
        missiles[index].on_stage [color=#666666]=[/color] [color=#666666]0[/color];
        missiles[index].x [color=#666666]=[/color] [color=#666666]0[/color];
        missiles[index].y [color=#666666]=[/color] [color=#666666]0[/color];
        missiles[index].speed [color=#666666]=[/color] [color=#666666]0[/color];
    }
    
    [color=#408080]*/* empty the array of enemies */*[/color]
    [color=#008000]**for**[/color] (index [color=#666666]=[/color] [color=#666666]0[/color]; index[color=#666666]<[/color]MAX_ENEMIES; index[color=#666666]++[/color])
    {
        enemies[index].on_stage [color=#666666]=[/color] [color=#666666]0[/color];
        enemies[index].x [color=#666666]=[/color] [color=#666666]0[/color];
        enemies[index].y [color=#666666]=[/color] [color=#666666]0[/color];
        enemies[index].can_shoot [color=#666666]=[/color] [color=#666666]0[/color];
        enemies[index].muzzle_flash [color=#666666]=[/color] [color=#666666]0[/color];
    }
    [color=#B00040]int[/color] ticks_to_next_enemy [color=#666666]=[/color] ENEMY_SPAWN_RATE;
    
    [color=#408080]*/* Flags to pass to SDL_SetVideoMode */*[/color]
    [color=#B00040]int[/color] videoFlags;
    [color=#408080]*/* main loop variable */*[/color]
    [color=#B00040]int[/color] done [color=#666666]=[/color] FALSE;
    [color=#408080]*/* used to collect events */*[/color]
    SDL_Event event;
    [color=#408080]*/* this holds some info about our display */*[/color]
    [color=#008000]**const**[/color] SDL_VideoInfo [color=#666666]*[/color]videoInfo;
    [color=#408080]*/* whether or not the window is active */*[/color]
    [color=#B00040]int[/color] isActive [color=#666666]=[/color] TRUE;

    [color=#408080]*/* initialize SDL */*[/color]
    [color=#008000]**if**[/color] ( SDL_Init( SDL_INIT_VIDEO ) [color=#666666]<[/color] [color=#666666]0[/color] )
    {
        fprintf( stderr, [color=#BA2121]"Video initialization failed: %s[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color],
             SDL_GetError( ) );
        Quit( [color=#666666]1[/color] );
    }

    [color=#408080]*/* Fetch the video info */*[/color]
    videoInfo [color=#666666]=[/color] SDL_GetVideoInfo( );

    [color=#008000]**if**[/color] ( [color=#666666]![/color]videoInfo )
    {
        fprintf( stderr, [color=#BA2121]"Video query failed: %s[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color],
             SDL_GetError( ) );
        Quit( [color=#666666]1[/color] );
    }

    [color=#408080]*/* the flags to pass to SDL_SetVideoMode */*[/color]
    videoFlags  [color=#666666]=[/color] SDL_OPENGL;          [color=#408080]*/* Enable OpenGL in SDL */*[/color]
    videoFlags [color=#666666]|=[/color] SDL_GL_DOUBLEBUFFER; [color=#408080]*/* Enable double buffering */*[/color]
    videoFlags [color=#666666]|=[/color] SDL_HWPALETTE;       [color=#408080]*/* Store the palette in hardware */*[/color]
    [color=#408080]*/*videoFlags |= SDL_RESIZABLE;*/*[/color]       [color=#408080]*/* Enable window resizing */*[/color]

    [color=#408080]*/* This checks to see if surfaces can be stored in memory */*[/color]
    [color=#008000]**if**[/color] ( videoInfo[color=#666666]->[/color]hw_available )
    videoFlags [color=#666666]|=[/color] SDL_HWSURFACE;
    [color=#008000]**else**[/color]
    videoFlags [color=#666666]|=[/color] SDL_SWSURFACE;

    [color=#408080]*/* This checks if hardware blits can be done */*[/color]
    [color=#008000]**if**[/color] ( videoInfo[color=#666666]->[/color]blit_hw )
    videoFlags [color=#666666]|=[/color] SDL_HWACCEL;

    [color=#408080]*/* Sets up OpenGL double buffering */*[/color]
    SDL_GL_SetAttribute( SDL_GL_DOUBLEBUFFER, [color=#666666]1[/color] );

    [color=#408080]*/* get a SDL surface */*[/color]
    surface [color=#666666]=[/color] SDL_SetVideoMode( SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_BPP,
                videoFlags );

    [color=#408080]*/* Verify there is a surface */*[/color]
    [color=#008000]**if**[/color] ( [color=#666666]![/color]surface )
    {
        fprintf( stderr,  [color=#BA2121]"Video mode set failed: %s[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color], SDL_GetError( ) );
        Quit( [color=#666666]1[/color] );
    }

    [color=#408080]*/* initialize OpenGL */*[/color]
    initGL( );

    [color=#408080]*/* resize the initial window */*[/color]
    resizeWindow( SCREEN_WIDTH, SCREEN_HEIGHT );

    [color=#408080]*/* wait for events */*[/color]
    [color=#008000]**while**[/color] ( [color=#666666]![/color]done )
    {
        [color=#408080]*/* handle the events in the queue */*[/color]

        [color=#008000]**while**[/color] ( SDL_PollEvent( [color=#666666]&[/color]event ) )
        {
            [color=#008000]**switch**[/color]( event.type )
            {
            [color=#008000]**case**[/color] SDL_ACTIVEEVENT:
                [color=#408080][i]/* Something's happend with our focus
                 * If we lost focus or we are iconified, we
                 * shouldn't draw the screen
                 */[/i][/color]
                [color=#008000]**if**[/color] ( event.active.gain [color=#666666]==[/color] [color=#666666]0[/color] )
                isActive [color=#666666]=[/color] FALSE;
                [color=#008000]**else**[/color]
                isActive [color=#666666]=[/color] TRUE;
                [color=#008000]**break**[/color];                
            [color=#008000]**case**[/color] SDL_VIDEORESIZE:
                [color=#408080]*/* handle resize event */*[/color]
                surface [color=#666666]=[/color] SDL_SetVideoMode( event.resize.w,
                            event.resize.h,
                            [color=#666666]16[/color], videoFlags );
                [color=#008000]**if**[/color] ( [color=#666666]![/color]surface )
                {
                    fprintf( stderr, [color=#BA2121]"Could not get a surface after resize: %s[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color], SDL_GetError( ) );
                    Quit( [color=#666666]1[/color] );
                }
                resizeWindow( event.resize.w, event.resize.h );
                [color=#008000]**break**[/color];
            [color=#008000]**case**[/color] SDL_KEYDOWN:
                [color=#408080]*/* handle key presses */*[/color]
                handleKeyPress( [color=#666666]&[/color]event.key.keysym );
                [color=#008000]**break**[/color];
            [color=#008000]**case**[/color] SDL_QUIT:
                [color=#408080]*/* handle quit requests */*[/color]
                done [color=#666666]=[/color] TRUE;
                [color=#008000]**break**[/color];
            [color=#008000]**default**[/color][color=#666666]:[/color]
                [color=#008000]**break**[/color];
            }
        }

        SDL_PumpEvents();
        keystate [color=#666666]=[/color] SDL_GetKeyState([color=#008000]NULL[/color]);
        
        [color=#008000]**if**[/color] (player_on_stage [color=#666666]==[/color] [color=#666666]1[/color])
        {
            [color=#408080]*/* move player around */*[/color]
            [color=#008000]**if**[/color] ( keystate[SDLK_LEFT] ) 
                { 
                [color=#008000]**if**[/color] (player_pos[[color=#666666]0[/color]] [color=#666666]>[/color] [color=#666666]0[/color])
                    player_pos[[color=#666666]0[/color]] [color=#666666]=[/color] (player_pos[[color=#666666]0[/color]] [color=#666666]-[/color] player_speed);
                }
            
            [color=#008000]**if**[/color] ( keystate[SDLK_RIGHT] ) 
                {
                [color=#008000]**if**[/color] (player_pos[[color=#666666]0[/color]] [color=#666666]<[/color] SCREEN_WIDTH)
                    player_pos[[color=#666666]0[/color]] [color=#666666]=[/color] (player_pos[[color=#666666]0[/color]] [color=#666666]+[/color] player_speed);
                }
            
            [color=#408080]*/* check for shooting key press, space */*[/color]
            [color=#008000]**if**[/color] ( keystate[SDLK_SPACE] )
                [color=#008000]**if**[/color] ( player_can_shoot [color=#666666]==[/color] [color=#666666]1[/color] )
                {
                    add_missile( player_pos[[color=#666666]0[/color]], player_pos[[color=#666666]1[/color]][color=#666666]-[/color][color=#666666]20[/color], [color=#666666]-[/color]MISSILE_SPEED );
                    player_can_shoot [color=#666666]=[/color] [color=#666666]0[/color];
                    [color=#408080]*/* how long will the muzzle flash last */*[/color]
                    player_muzzle_flash [color=#666666]=[/color] [color=#666666]2[/color];
                    player_shoot_alarm [color=#666666]=[/color] SHOOT_DELAY;
                }
                
            
            [color=#408080]*/* handle shooting delay */*[/color]
            [color=#008000]**if**[/color] ( player_can_shoot [color=#666666]==[/color] [color=#666666]0[/color] )
            {
                [color=#408080]*/* reduce shooting alarm by 1 */*[/color]
                player_shoot_alarm [color=#666666]-=[/color] [color=#666666]1[/color];
                [color=#408080]*/* if alarm is 0, then reload weapon to be able to shoot again */*[/color]
                [color=#008000]**if**[/color] ( player_shoot_alarm [color=#666666]<=[/color] [color=#666666]0[/color] )
                    player_can_shoot [color=#666666]=[/color] [color=#666666]1[/color];
            }
        }
        
        ticks_to_next_enemy [color=#666666]-=[/color] [color=#666666]1[/color];
        
        [color=#008000]**if**[/color] (ticks_to_next_enemy [color=#666666]<=[/color] [color=#666666]0[/color])
        {
            [color=#B00040]int[/color] x [color=#666666]=[/color] ( rand() [color=#666666]%[/color] SCREEN_WIDTH );
            add_enemy( x, [color=#666666]-[/color][color=#666666]50[/color] );
            [color=#008000]**if**[/color] (ENEMY_SPAWN_RATE [color=#666666]>[/color] ENEMY_SPAWN_RATE_DECR)
                ENEMY_SPAWN_RATE [color=#666666]-=[/color] ENEMY_SPAWN_RATE_DECR;
            ticks_to_next_enemy [color=#666666]=[/color] ENEMY_SPAWN_RATE;
        }
        
        [color=#408080]*/* draw the scene, no matter is the window active or not */*[/color]
        drawGLScene( );
        [color=#408080][i]/*if ( isActive )
        drawGLScene( ); */[/i][/color]
        
        [color=#008000]**if**[/color] (player_on_stage [color=#666666]==[/color] [color=#666666]0[/color])
        {
            ticks_to_death [color=#666666]-=[/color] [color=#666666]1[/color];
            [color=#008000]**if**[/color] (ticks_to_death [color=#666666]<=[/color] [color=#666666]0[/color])
                Quit( [color=#666666]0[/color] );
        }
        
        [color=#408080]*/* 50 frames per second */*[/color]
        usleep( [color=#666666]20000[/color] );
    }

    [color=#408080]*/* clean ourselves up and exit */*[/color]
    Quit( [color=#666666]0[/color] );

    [color=#408080]*/* Should never get here */*[/color]
    [color=#008000]**return**[/color]( [color=#666666]0[/color] );
}

```

Also, here is the makefile:
```

CC = gcc -Wall -ansi

all:
	$(CC) gltest.c -o gltest -lGL -lGLU `sdl-config --cflags --libs`

clean:
	@echo Cleaning up...
	@rm gltest
	@echo Done.

```

And controls of that game are arrow keys and space. Goal is to survive as long as possible, without colliding the enemies.

---

### Post by DrMega on 2008-11-05
> **nvteighen said:**
> Why "**was** it correctly designed"? I think it's still correctly designed and the various modifications it underwent all respected the original design.

C underwent a fairly major transformation when it was standardised by ANSI (prior to which it was loosely termed K&R C to differentiate. C++ deviated from the "spirit" of C by becoming higher level and taking away some of the developer's freedom (I've heard it said that if a C programmer wants to hang himself, C would be happy to help him do it). C# is pretty much nothing like C. It looks similar at a glance, in the same way that Java does, but C# is so far removed from original C that I don't think they can be compared really.

Don't get me wrong, I like C and its descendants, but if you don't need to look very hard to see how it has (perfectly understandable) flaws in it's design.

> **crazyfuturamanoob said:**
> I finally finished that game. Here you go, save as gltest.c, in 689 lines.

Well done, I'll give that a go.

---

### Post by LaRoza on 2008-11-05
> **DrMega said:**
> C# is pretty much nothing like C. It looks similar at a glance, in the same way that Java does, but C# is so far removed from original C that I don't think they can be compared really.


No, C# is like Java, not C. It only has a similar syntax as C.

It went: C -> C++ -> D, but Java -> C# because MS couldn't get away with their normal tactics on Java. [http://www.javaworld.com/javaworld/jw-01-2001/jw-0124-iw-mssuncourt.html](http://www.javaworld.com/javaworld/jw-01-2001/jw-0124-iw-mssuncourt.html)

---

### Post by crazyfuturamanoob on 2008-11-05
is C# same than C++?

---

### Post by LaRoza on 2008-11-05
> **crazyfuturamanoob said:**
> is C# same than C++?

Not at all. It is Microsoft's Java, so to speak.

---

### Post by cmay on 2008-11-05
@grayzyfuturamanoob
cool :)

---

### Post by DrMega on 2008-11-05
> **LaRoza said:**
> No, C# is like Java, not C. It only has a similar syntax as C.

Isn't that kind of what I said?

---

### Post by LaRoza on 2008-11-05
> **DrMega said:**
> Isn't that kind of what I said?

Sorry if I misread it, but your post seemed to imply that C# was somehow related to C and C++, whereas it is directly inspired by Java, despite all three having similiar syntax, C -> C++ -> D lines are different from Java -> C# lines.

---

### Post by Lux Perpetua on 2008-11-05
> **crazyfuturamanoob said:**
> I finally finished that game. Here you go, save as gltest.c, in 689 lines.Not bad!

---

### Post by crazyfuturamanoob on 2008-11-09
> **kknd said:**
> You can mantain a linked list, and traverse it in each frame, updating the position and rendering each missile.

When a missile explode or goes out of scope, you simply remove it from the list (and free it if its dynamically allocated).

Array is much easier for missiles, but when making some more complex things, an array of fixed size isn't good.

How does that linked list work? Could you post me a small example?

---

### Post by nvteighen on 2008-11-09
What you need is probably a double-linked list, because single-linked lists make removal of middle-nodes a bit more difficult.

Please, study this demo I've written. It should give you an idea how this works; there may be some controversial issues, like the use of dynamic memory which in some cases may be overkill.

Anyway, this is one of those cases in which you start missing some high-level languages' constructs.

```
[color=#BC7A00]#include <stdio.h>
#include <malloc.h>
[/color]
[color=#008000]**struct**[/color] NODE_T
{
    [color=#B00040]int[/color] data;
    [color=#008000]**struct**[/color] NODE_T [color=#666666]*[/color]next;
    [color=#008000]**struct**[/color] NODE_T [color=#666666]*[/color]prev; [color=#408080]*/* <-- This, if you want a double-linked list */*[/color]
};

[color=#008000]**typedef**[/color] [color=#008000]**struct**[/color] NODE_T node_t;

node_t [color=#666666]*[/color][color=#0000FF]node_new[/color]([color=#B00040]int[/color] data)
{
    [color=#408080][i]/* We use calloc() for allocation because so we don't care about stack
     * issues. If we only relied on stack-based allocation, the list would not
     * work because the destinations pointed by the pointers would be destroyed
     * after each function's return. I choose calloc() over malloc() because it
     * sets everything to 0/NULL, specially important for the pointers. */[/i][/color]
    node_t [color=#666666]*[/color]node [color=#666666]=[/color] (node_t [color=#666666]*[/color])calloc([color=#666666]1[/color], [color=#008000]**sizeof**[/color](node_t));

    [color=#408080][i]/* Only set the 'data' member if calloc() succeeded (i.e. the result was not
     * NULL). Without this check, we'd get a heap corruption complain. */[/i][/color]
    [color=#008000]**if**[/color](node [color=#666666]!=[/color] [color=#008000]NULL[/color])
        node[color=#666666]->[/color]data [color=#666666]=[/color] data;

    [color=#408080][i]/* We always return 'node'; if calloc() did succeed, it returns a pointer to
     * the allocated memory but if it didn't, it will return NULL. */[/i][/color]
    [color=#008000]**return**[/color] node;
}

[color=#B00040]void[/color] [color=#0000FF]node_free[/color](node_t [color=#666666]*[/color]node)
{
    [color=#408080][i]/* We could implement this as a macro, too:

       #define node_free(node) free(node) */[/i][/color]

    free(node);
}

[color=#B00040]void[/color] [color=#0000FF]node_append[/color](node_t [color=#666666]*[/color]previous, node_t [color=#666666]*[/color]following)
{
    [color=#408080]*/* This is self-evident, I think. */*[/color]
    previous[color=#666666]->[/color]next [color=#666666]=[/color] following;
    following[color=#666666]->[/color]prev [color=#666666]=[/color] previous;
}

[color=#B00040]void[/color] [color=#0000FF]node_unlink[/color](node_t [color=#666666]*[/color]node)
{
    [color=#408080][i]/* This is a bit trickier. Before cutting the node's links, we have to
     * modify those of its parent and child so we never break the chain of
     * links. Think of this using boxes an arrows in paper and you'll get it
     * very clear. Also, we have to check whether there's or not an parent and
     * child (no parent: we're at the root node; no child: at the end of
     * list), otherwise we'd fall into illegal memory access. */[/i][/color]

    [color=#008000]**if**[/color](node[color=#666666]->[/color]next [color=#666666]!=[/color] [color=#008000]NULL[/color])
        node[color=#666666]->[/color]next[color=#666666]->[/color]prev [color=#666666]=[/color] node[color=#666666]->[/color]prev;

    [color=#008000]**if**[/color](node[color=#666666]->[/color]prev [color=#666666]!=[/color] [color=#008000]NULL[/color])
        node[color=#666666]->[/color]prev[color=#666666]->[/color]next [color=#666666]=[/color] node[color=#666666]->[/color]next;

    node[color=#666666]->[/color]prev [color=#666666]=[/color] [color=#008000]NULL[/color];
    node[color=#666666]->[/color]next [color=#666666]=[/color] [color=#008000]NULL[/color];
}

[color=#B00040]void[/color] [color=#0000FF]node_delete[/color](node_t [color=#666666]*[/color]node)
{
    [color=#408080]*/* Just a shortcut: unlink and then destroy the data in memory. */*[/color]

    node_unlink(node);
    node_free(node);
}

[color=#B00040]void[/color] [color=#0000FF]printer[/color](node_t [color=#666666]*[/color]root)
{
    node_t [color=#666666]*[/color]tracker [color=#666666]=[/color] [color=#008000]NULL[/color];

    [color=#408080][i]/* Look: We just use the next pointer to traverse the whole list to the
     * end. No tricks! */[/i][/color]
    [color=#008000]**for**[/color](tracker [color=#666666]=[/color] root; tracker [color=#666666]!=[/color] [color=#008000]NULL[/color]; tracker [color=#666666]=[/color] tracker[color=#666666]->[/color]next)
        printf([color=#BA2121]"%d "[/color], tracker[color=#666666]->[/color]data);

    printf([color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]);
}

[color=#B00040]int[/color] [color=#0000FF]main[/color]([color=#B00040]void[/color])
{
    [color=#408080]*/* Now, to show this works! */*[/color]

    node_t [color=#666666]*[/color]root [color=#666666]=[/color] node_new([color=#666666]45[/color]);
    node_t [color=#666666]*[/color]second [color=#666666]=[/color] node_new([color=#666666]34[/color]);
    node_t [color=#666666]*[/color]third [color=#666666]=[/color] node_new([color=#666666]1[/color]);

    node_append(root, second);
    node_append(second, third);

    printer(root);

    node_unlink(second);
    printf([color=#BA2121]"Now, after unlinking the second node:[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]);

    printer(root);

    [color=#408080]*/* I'm a environment-conscious developer: I clean my garbage by myself. */*[/color]
    node_free(root);
    node_free(second);
    node_free(third);

    [color=#008000]**return**[/color] [color=#666666]0[/color];
}

```

---


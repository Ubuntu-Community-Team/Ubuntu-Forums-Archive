---
title: "assigning element values in 'cascaded' STRUCT"
date: 2007-08-09
forum: Programming Talk
---

### Post by nss0000 on 2007-08-09
Gents:

Continuing my adventures in C-land:

Following a K&R example -- passing STRCT-containing-STRUCT to a function -- I managed the following working_but_irritating code:

  #include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

/* mfs5.c  8.9.07... passing STRUCT containing a STRUCT*/

struct point { int x; int y; };
struct area { struct point pta;  struct point ptb; };
float my_dis( struct area );

main( int argc, char *argv[] )
{
 struct point pta;
 struct point ptb;  
 struct area screen;
 float dis;
  
  if ( argc != 5 )
    {
      printf("Wake up, Jackson and enter 4 integer values\n");
      exit(0);
     }

 pta.x = atoi(argv[1]);
 pta.y = atoi(argv[2]);
 ptb.x = atoi(argv[3]);
 ptb.y = atoi(argv[4]);

 screen.pta.x = pta.x;
 screen.pta.y = pta.y;
 screen.ptb.x = ptb.x;
 screen.ptb.y = ptb.y; 

 printf("And the point_coordinates are ... %d%d%d%d\n", pta.x, pta.y, ptb.x, ptb.y);
 printf("And the screen_coordinates are ... %d%d%d%d\n", screen.pta.x, screen.pta.y, screen.ptb.x, screen.ptb.y);

    dis = my_dis(screen);
    printf("And the distance between point is ... %f\n", dis);

 return 0;
}

/* functionland */

float my_dis( struct area q )
{
  float d, dd;

   printf("Down here ... %d%d%d%d\n", q.pta.x, q.pta.y, q.ptb.x, q.ptb.y); 
   d = (float) (q.pta.x - q.ptb.x)*(q.pta.x - q.ptb.x) + (q.pta.y - q.ptb.y)*(q.pta.y - q.ptb.y);
   dd = pow( d , 0.5 );

 return dd;
}

My question is: why do I need to assign numeric values to BOTH  AREA & the POINT structures , since AREA is defined thru two POINT STRUCTs?? (ex) why isn't the value for pta.x 'shuffled across' to screen.pta.x ? 
Yep, tho it works , I'm "over-reaching" my skills with this code. Thanks for any comments.

---

### Post by Rocket2DMn on 2007-08-09
The values inside each structure are their own separate entities.  You created "struct point pta" and your definition of "struct area" also has a "point pta", but just because they are named the same, does not make them so.
"struct point pta;" is a variable struct in your main() function, but the struct definition "struct area { struct point pta; struct point ptb; };" is not related to that.
When you declared
   "struct point pta;"
      and 
   "struct area screen;"
you created 2 different structure variables that are unrelated, they do not share values despite the similar names.  screen.pta1 is a variable inside screen.
It is difficult to explain as this is more OOP (object oriented programming).  If you learn java, you will have a better understanding, but until then, just recognize that you declared them separately, so they are not related.  They are stored in memory at different locations as different variables.

---

### Post by Mirrorball on 2007-08-09
I'm not sure I understood your question. When you defined struct area screen, screen has two points, screen.pta and screen.ptb. The points pta and ptb you defined separately are not screen's, they are different points. When you assign values to them, you are not assigning values to screen's points.

---

### Post by nss0000 on 2007-08-09
Thanks for your responses:

I expected that if a (STRUCT) data_type is defined in-terms-of a previously defined  STRUCT data_type, then actual data vales would "flow" between them. 
Why did I think this? Because when you define a STRUCT you also must five a "NAME" to the variables ... which really shocked me:

 ... you can't say:  STRUCT firstguy { int; int; }; ... but must say:
     STRUCT firstguy { int x; int y;}; Yikes, so I'm thinking ...

  Then STRUCT secondguy { STRUCT firstguy pta; }; ... grabs the two values for int x and int y. I mean, why else would you have to give those variables names ???? So wrong-as-it-is, that's what I  thought.

Thanks again. Really appreciate your comments:

nss
*******

---

### Post by Rocket2DMn on 2007-08-09
No problem, next week we'll do pointers and then you CAN actually do that...  On second thought, I'll let your professor explain that.  Enjoy coding, you're doing well!

---

### Post by nss0000 on 2007-08-09
BigR:

Yes, the pointer STRUCT formulation comes next in the damnable K&R CH#6 pages. If it weren't for:
 
 [http://www.space.unibe.ch/comp_doc/c_manual/C/SYNTAX/syntax.html](http://www.space.unibe.ch/comp_doc/c_manual/C/SYNTAX/syntax.html)

... I'd really be hosed. OTOH I have no fear of the professors obscurity ... as I am the professor -- by heavens' grace EE not CS. Circuit theory and Maxwells Equations are monuments to clarity as compared to coding syntax.

---

### Post by nss0000 on 2007-08-10
And yep -- STRUCT are stump_dumb compared to multi-dim arrays, in that you can toss about any_old variable NAMEs when assigning specific values to elements of the array passed by a function. But you MUST use the globally defined NAMES for a STRUCT ... boohoo I thought I was moving "uptown".   

I can still hardly believe it .... a <STRUCT foo...>  doesn't appear to "know the structure" of foo !!!   Gawdsakes somebody must like it , but they must be 'in irons' as a sailor would put it..

---

### Post by Mirrorball on 2007-08-10
I still don't understand what your real problem with structs is. To me the syntax is very clear, although that might be because I'm used to it. Do you realize you could have written:
```

screen.pta.x = atoi(argv[1]);
screen.pta.y = atoi(argv[2]);
screen.ptb.x = atoi(argv[3]);
screen.ptb.y = atoi(argv[4]);

```

---

### Post by nss0000 on 2007-08-10
BigM:

Yep I know that ... and what I also know is that ya CAN'T write:

screen.door.open = argv[1];
screen.door.closed = argv[2];

... even tho as defined a data_type of STRUCT area{}  better have 2-points & 4-ints dangling off the end. Who cares what name you call the 'hinges'? 

Answer --- C cares.  

BTW: Again, many thanks to you and other commenters for your insights and "thumps". Many eyes make for shallow bugs ... or suchlike. 
This morning I wrote my first function-returning-STRUCT after passing a 'cascaded' STRUCT. I need do a few more such tasks, then take_up the *pointer version of passing STRUCT. I can feel the pain already.

---

### Post by Mirrorball on 2007-08-10
> **nss0000 said:**
> 
... even tho as defined a data_type of STRUCT area{}  better have 2-points & 4-ints dangling off the end. Who cares what name you call the 'hinges'? 

Then how would the compiler know what member you are assigning data to? Also a struct's members are named according to their meaning. For instance, a circle struct might have a center and a radius:
```

struct circle
{
    struct point center;
    double radius;
};

```Variable names are not arbitrary. When you wanted to create a circle, you would write:
```

struct circle my_circle;
my_circle.center.x = 0;
my_circle.center.y = 0;
my_circle.radius = 1;

```And it would have been meaningful. A circle has a center and a radius. A point has x and y coordinates. Structs were not made to hold arbitrary data. You will learn more about this when you study object orientation.

---


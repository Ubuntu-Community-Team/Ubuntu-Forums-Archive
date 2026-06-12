---
title: "chasing people in video games"
date: 2011-05-07
forum: Programming Talk
---

### Post by druca on 2011-05-07
Hello all,

I had a quick question about vector algebra etc. My game isn't working so well. 

I have this game and the "bad guys" are supposed to be chasing me. I've done this before in C/C++ but its not working so well in Scheme...I'll just write it in Cish syntax. 

Anyway the algorithm goes like this:

vector_direction = vector_normalize( 
                         vector_distance( player, sprite )) ;

nextpos += (direction * velocity ) ;

sprite.goto( nextpos )

is there something I am not taking into account here? My sprites are going everywhere! Thank you ahead of time for your help.

---

### Post by Tony Flury on 2011-05-08
what does Vector Normalize do ?

You appear to be basing the Direction on just a distance..

Don't you want to calculate the vector between you and the bad guy, and move along that vector ?

---

### Post by ziekfiguur on 2011-05-08
I assume vector_normalize normalizes the vector to a length of 1.
Then, like Tony Flury said you should do something like this:
```
vector_direction = vector_normalize(player - sprite);

nextpos += (direction * velocity);

sprite.goto(nextpos);
```

---

### Post by druca on 2011-05-08
Yes sorry vector_normalize takes a vector and turns it into a unit vector or direction vector. I give it the player - sprite vector to normalize. I think I almost figured it out. I swapped the two in another function. Dumb me. Thank you for all of your help. 

Just a few more questions. They chase me first and then they start to back up until they align with me, then stop. Do I have to take into account positive or negative values if the center of my world is (0 , 0 , 0 ) or should that not matter? I can just change my world position if anything. 

Thank you again!

---


---
title: "Programming AI Physics in C++"
date: 2007-07-24
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2007-07-24
Hey Guys

I was wondering if anyone had a good tutorial on how to program some AI to calculate trajectories in the same what that gorrilas.bas or worms does for its CPU player?

I can handle the human part of it and have that working but I can find any reaonably easy to follow info on how to do this for a CPU player.

And help and suggestions would be great!

Thanks In Advance!

Mike

---

### Post by [h2o] on 2007-07-24
One possible solution I could think of is:
1. Pick an angle
2. Solve power needed to hit player (using regular mechanics)
3. If hit (no structures in the way) then randomize both parameters (or the game will soon be boring ;))
4. If no hit, then try new angle and goto 1

Don't forget to limit the number of tries the computer gets, or it might get stuck forever.

This is a quite straightforward but no so elegant solution though, there are probably lots of other better ways to do it.

---

### Post by KIAaze on 2007-07-24
Now, what could you possibly need that for? ^^

---

### Post by Mickeysofine1972 on 2007-07-24
> **KIAaze said:**
> Now, what could you possibly need that for? ^^

HAHA you rumbled me! I admit it is for the iTeam project! I have programmed the players ability to throw bombs and stuff but I was wanting to know of there any equasions that I can use to calculate how to hit another player for the AI .

Seriously there is little or no info about how to get this done so I put it to you Ubuntu guys how can I calculate the right velocity and angle to fire at for my CPU player?

Mike

---

### Post by KIAaze on 2007-07-24
I would be happy to code this part myself. :)
I haven't done anything yet for iteam.

But, this should help you get started:

```
(x0,y0)=shooter;
(x,y)=target;
X=x-x0;
Y=y-y0;
v0x=v0*cos(a);
v0y=v0*sin(a);
gravity=g>0

y
^
|         |  g
+-->x     v

v0=sqrt(1/2*g*X^2/(cos(a)^2*(X*tan(a)-Y)));

```

I haven't double-checked it yet, but I think it's correct.

---

### Post by Mickeysofine1972 on 2007-07-24
> **KIAaze said:**
> I would be happy to code this part myself. :)
I haven't done anything yet for iteam.

But, this should help you get started:

```
(x0,y0)=shooter;
(x,y)=target;
X=x-x0;
Y=y-y0;
v0x=v0*cos(a);
v0y=v0*sin(a);
gravity=g>0

y
^
|             |    g
+-->x     v

v0=sqrt(1/2*g*X^2/(cos(a)^2*(X*tan(a)+Y)));

```

I haven't double-checked it yet, but I think it's correct.

Ok but what does that mean in english?

is g gravity and what is v0 is it the initial lenght of the velocity vector? plus how do we guess the angle?

This seems like it could work but i need to make sure i get it first lol

can you draw me a picture? hehe XD

Mike

---

### Post by hod139 on 2007-07-24
[http://en.wikipedia.org/wiki/Trajectory_of_a_projectile](http://en.wikipedia.org/wiki/Trajectory_of_a_projectile)

---

### Post by KIAaze on 2007-07-24
There was a mistake in my formula.
It's 
```
v0=sqrt(1/2*g*X^2/(cos(a)^2*(X*tan(a)**-**Y)));

```
;)

> **Mickeysofine1972 said:**
> Ok but what does that mean in english?

is g gravity and what is v0 is it the initial lenght of the velocity vector? plus how do we guess the angle?

This seems like it could work but i need to make sure i get it first lol

can you draw me a picture? hehe XD

Mike

Yes, "g" is the gravity and "v0" is the initial velocity.
"a" is the angle ("a" for "alpha").

The angle only has to verify the following equation:
```
X*tan(a)-Y>0
```
Which makes sense when you rewrite it as:
```
tan(a)>Y/X if X>0
tan(a)<Y/X if X<0

```

This means that if the enemy is at an angle of 45 degrees to you, you have to shoot higher than 45 degrees.  :roll:

I can't draw an image right now (I'm at work, so being on the forums is already a bit uncomfortable. ^^), but the Wikipedia link above seems quite good.

I might write the function for you this evening. :)

Here's how I currently see the main algorithm:

1)choose angle a so that X*tan(a)-Y>0
2)
for(a=0;a<2*pi;a++)
{
   v0=calc_velocity(a);
   hit=simulation();
   if(hit) break;
}
4)we now have a (v0,a) combination that hits
5)randomize v0 and a a little bit using gaussian distributions centered on v0 and a for example
(I don't know exactly how to do that yet in C/C++, but using a uniform distribution, it's easy: just use the rand() function)
6)shoot

Note: To detect if there's a hit or not, a simulation of the shot taking into account the environment will have to be made everytime.

I've never written such an AI before, so maybe there's a better way to do this. ^^'

---

### Post by Mickeysofine1972 on 2007-07-24
> **KIAaze said:**
> There was a mistake in my formula.
It's 
```
v0=sqrt(1/2*g*X^2/(cos(a)^2*(X*tan(a)**-**Y)));

```
;)



Yes, "g" is the gravity and "v0" is the initial velocity.
"a" is the angle ("a" for "alpha").

The angle only has to verify the following equation:
```
X*tan(a)-Y>0
```
Which makes sense when you rewrite it as:
```
tan(a)>Y/X if X>0
tan(a)<Y/X if X<0

```

This means that if the enemy is at an angle of 45 degrees to you, you have to shoot higher than 45 degrees.  :roll:

I can't draw an image right now (I'm at work, so being on the forums is already a bit uncomfortable. ^^), but the Wikipedia link above seems quite good.

I might write the function for you this evening. :)

Here's how I currently see the main algorithm:

1)choose angle a so that X*tan(a)-Y>0
2)
for(a=0;a<2*pi;a++)
{
   v0=calc_velocity(a);
   hit=simulation();
   if(hit) break;
}
4)we now have a (v0,a) combination that hits
5)randomize v0 and a a little bit using gaussian distributions centered on v0 and a for example
(I don't know exactly how to do that yet in C/C++, but using a uniform distribution, it's easy: just use the rand() function)
6)shoot

Note: To detect if there's a hit or not, a simulation of the shot taking into account the environment will have to be made everytime.

I've never written such an AI before, so maybe there's a better way to do this. ^^'

Kewl ty for explaining

I hadnt realised that you have to do a test until you get it right lol! i was expecting something like a discreet set of code that just new first time round lol

in that case i welcome your contribution! I have a good idea how to do it now :guitar:

i looked at the wiki link and I lost the will to live lmao!

Mike

---

### Post by hod139 on 2007-07-24
> **Mickeysofine1972 said:**
> 
I hadnt realised that you have to do a test until you get it right lol! i was expecting something like a discreet set of code that just new first time round lol

For projectile motion, you can solve the equations exactly, there is no testing.  The wikipedia articles shows exactly how.

> 
i looked at the wiki link and I lost the will to live lmao!
Oh.  


Let me see if I can help.
Given:
(0, 0) : location of the shooter, you can always adjust coordinates so this is true
(x, y): location of the target

Step 1, pick a velocity v.
Step 2, use the "Angle &#952; required to hit coordinate (x,y)" formula in the wikipedia article.  The formula can have 0, 1, or 2 real solutions.  If 0, then the selected velocity is not big enough to reach the target. If 1 real solution, use that real one.  If 2 real solutions, pick your favorite  (it doesn't matter).

To add noise so the computer doesn't always win, you can add a random offset to the (x, y) location, or you can change the velocity after you solved for the angle.

---

### Post by Mickeysofine1972 on 2007-07-24
ty hod 

I think i need to find a nice kiddies tutorial on how to make functions out of mathematical equations.

Thats a good idea for a tutorial i think ..... hmmm

Ok i will try the trial and error way first then after I grow a bit more brains i will have a go with the more exact,(and probably less cpu intensive), method

Mike

---

### Post by KIAaze on 2007-07-24
Well, my method also uses an exact calculation.  :)

The function v0=calc_velocity(a) is nothing else than:
v0=sqrt(1/2*g*X^2/(cos(a)^2*(X*tan(a)-Y)));

More precisely, it's v0=calc_velocity(a,g,x0,y0,x,y) where:
[LIST]
[*](x0,y0)=shooter;
[*](x,y)=target;
[*]X=x-x0;
[*]Y=y-y0;
[/LIST]

The error and trial is only necessary because of obstacles like trees or other in the game.

I have no idea how to do this without trial and error since the environment could be anything.

With the function suggested by hod139, it's the same.
The only difference is that you fix the velocity and then calculate the angle instead of vice-versa.

To start testing, you could just use the exact calculation and add random offsets.
The trial and error can be added afterwards.

---

### Post by ankursethi on 2007-07-24
**Offtopic Note to iTeam Developers :**
I've tried the pre-pre-alpha version of iTeam from the SVN repository (or was it CVS? Whatever) and the ovrall feel is a bit like Wormux. The problem lies in the fact that there are no separate sprites when the player jumps or gets hit.

I suggest that there be a separate sprite for positions like "jump", "hit" etc. to make it feel a bit realistic and Worms/GunBound like.

---

### Post by hod139 on 2007-07-24
> **KIAaze said:**
> 
The error and trial is only necessary because of obstacles like trees or other in the game.

I have no idea how to do this without trial and error since the environment could be anything.

This is a very good point.  

> 
With the function suggested by hod139, it's the same.
The only difference is that you fix the velocity and then calculate the angle instead of vice-versa.
I never meant to imply that my method was better or different, sorry if I did.  As you explained, it is the same thing with a different unknown variable. 

Mickeysofine1972, here is some code to help you out.  It assumes there are no obstacles in the path of the trajectory.
```

#include<iostream>
#include<cmath>

int main()
{
   const double g = 9.81;  // gravitation constant of acceleration
   double x = 10; // x location of target
   double y = 10; // y location of target

   // step 1, pick a velocity (really this is a speed, but wikipedia called it a velocity)
   double v = 20;

   // step 2, find the angle, assuming launching from (0, 0)
   double v_squared = v*v; // compute once to save computation
   double V_fourth = v_squared * v_squared; // compute once to save computation

   double insideSqrt = V_fourth - g*(g*x*x + 2*y*v_squared);
   if(insideSqrt < 0)
   { // only imaginary solutions
     std::cout << "Initial speed is too low, no solution! \n";
     exit(1);
   }
   
   double sol1 = atan( (v_squared + sqrt(insideSqrt) ) / (g*x) );
   double sol2 = atan( (v_squared - sqrt(insideSqrt) ) / (g*x) );

   std::cout << "To hit the target at (" << x << ", " << y << ") \n";
   std::cout << "with intial speed " << v << "\n";
   std::cout << "launch with an angle of " << sol1 * 180./M_PI << " degrees \n";
   std::cout << "or an angle of " << sol2 * 180./M_PI << " degrees" << std::endl;

   return 0;
}

```

---

### Post by KIAaze on 2007-07-24
Here's my version:
```
#include <stdio.h>
#include <stdlib.h>
#include <iostream>
#include <math.h>

using namespace std;

double calc_velocity(double a_deg, double g, double x0, double y0, double x, double y);
double deg2rad(double a_deg);
double rad2deg(double a_rad);
double rand_uniform(double min, double max);

int main(int argc,char *argv[])
{
  double a=45;//angle (in degrees) in regard to the ground level (x axis)
  double x0=0;//x position of the shooter
  double y0=0;//y position of the shooter
  double x=10;//x position of the target
  double y=0;//y position of the target
  double g=9.81;//gravity
  double error=1;//maximum artificial error that will be added to the velocity
  
  //calculate "exact" velocity
  double v0=calc_velocity(a,g,x0,y0,x,y);
  cout<<"velocity: v0="<<v0<<endl;
  
  //add an artificial error to the velocity
  v0=rand_uniform(v0-error,v0+error);
  cout<<"velocity with a maximum error offset of "<<error<<": v0="<<v0<<endl;
}

double calc_velocity(double a_deg, double g, double x0, double y0, double x, double y)
{
  double a_rad=deg2rad(a_deg);
  double X=x-x0;
  double Y=y-y0;
  double v0=sqrt(1/2.*g*X*X/(cos(a_rad)*cos(a_rad)*(X*tan(a_rad)-Y)));
  return(v0);
}

double deg2rad(double a_deg)
{
  return(a_deg*M_PI/180.);
}

double rad2deg(double a_rad)
{
  return(a_rad*180./M_PI);
}

double rand_uniform(double min, double max)
{
  srand( time(NULL) );
  double x=min+(max-min)*rand()/(double)RAND_MAX;
  return(x);
}

```

This still needs a nice SDL simulation to be tested and visualized. :)

I could add a gaussian random distribution, but I don't think it's necessary for this game. :roll:
The difference would be that the probability of big errors is lower than the one of small errors.

---

### Post by Mickeysofine1972 on 2007-07-24
> **ankursethi said:**
> **Offtopic Note to iTeam Developers :**
I've tried the pre-pre-alpha version of iTeam from the SVN repository (or was it CVS? Whatever) and the ovrall feel is a bit like Wormux. The problem lies in the fact that there are no separate sprites when the player jumps or gets hit.

I suggest that there be a separate sprite for positions like "jump", "hit" etc. to make it feel a bit realistic and Worms/GunBound like.

If you try getting doddis branch from the trunk you will find that he has built the animation system and jorge has supplied us with animation too so you will start to see that filter into the main trunk as we go. Thanks for taking the time to give feedback though its always great to hear people are interested.

Also, a big thank you to hod139 and KIAaze for the code, I will make sure you get some credit it when its part of the game.

Mike

PS :- found a kiddies algebra lesson :lolflag:

---

### Post by hod139 on 2007-07-24
> **KIAaze said:**
> Here's my version:
```

<snip>
double rand_uniform(double min, double max)
{
  srand( time(NULL) );
  double x=min+(max-min)*rand()/(double)RAND_MAX;
  return(x);
}

```
You should not seed the random number generator every call to this function.  You should seed it only once.

Also, do you mind if I make general comments about the rest of your code?

---

### Post by KIAaze on 2007-07-24
> **hod139 said:**
> Also, do you mind if I make general comments about the rest of your code?
Not at all.
In fact, I would be happy about comments. :)

---

### Post by Mickeysofine1972 on 2007-07-24
Ok 

I think that i can find the highest point on the terrain between the player and the target but without the looping tests. well, sort of cos i have to loop through the SDLSurface and find the highest pixel in there hehe but I think this might prove faster.

what do you think?

Mike

---

### Post by Mickeysofine1972 on 2007-07-24
BTW hod139 ty for pointing out that tan-1 is actually a atan!

I've learn loads since I got into this mathmatics stuff lol :guitar:

Mike

---

### Post by Wybiral on 2007-07-24
Algebraically solve for a given time using the typical physics formulas for projectiles.

X_vel = (X_destination - X_origin) / destination_time
Y_vel = -(Y_origin - 0.5 * gravity * pow(destination_time, 2) - Y_destination) / destination_time

You can get the power/angle from that vector.

---

### Post by hod139 on 2007-07-24
My comments inlined.
> **KIAaze said:**
> 
```

#include <stdio.h> **should be #include <cstdio>**
#include <stdlib.h> **should be #include <cstdlib>**
#include <iostream>
#include <math.h> **should be #include <cmath>**

using namespace std;  [B]Not wrong, but frowned upon since it brings in the entire std namespace for just using std::cout and std::endl.

// If you really don't want to write std::cout and std::endl, consider
using std::cout;
using std::endl
[/B] 
double calc_velocity(double a_deg, double g, double x0, double y0, double x, double y);

**// minor, consider inlining these functions for performance gain**
double deg2rad(double a_deg);
double rad2deg(double a_rad);
double rand_uniform(double min, double max);

[B]// If you are not going to use argc or argv why declare them?
int main(void)
[/B] int main(int argc,char *argv[])
{
  double a=45;//angle (in degrees) in regard to the ground level (x axis)
  double x0=0;//x position of the shooter
  double y0=0;//y position of the shooter
  double x=10;//x position of the target
  double y=0;//y position of the target
  double g=9.81;//gravity
  double error=1;//maximum artificial error that will be added to the velocity
  
  //calculate "exact" velocity
  double v0=calc_velocity(a,g,x0,y0,x,y);
  cout<<"velocity: v0="<<v0<<endl;
  
  //add an artificial error to the velocity
  v0=rand_uniform(v0-error,v0+error);
  cout<<"velocity with a maximum error offset of "<<error<<": v0="<<v0<<endl;
}

double calc_velocity(double a_deg, double g, double x0, double y0, double x, double y)
{
  double a_rad=deg2rad(a_deg);
  double X=x-x0;
  double Y=y-y0;

// [B]cos(a_rad) is very expensive.  You only have to call it once and store the result.  
Also, why do the 1/2 floating point division every time.  We know that answer is 0.5.  
Lastly, don't waste the time to allocate v0, then copy it in the return.  Compilers can do neat tricks with returning the result of an expression
  double c_a = cos(a_rad);[/B]
**  return sqrt( 0.5 * g * X*X / ( ****c_a*********c_a ***** (X * tan(a_rad) - Y) ) );**
  double v0=sqrt(1/2.*g*X*X/(cos(a_rad)*cos(a_rad)*(X*tan(a_rad)-Y)));
  return(v0);
}

**// inline this function**
double deg2rad(double a_deg)
{
  return(a_deg*M_PI/180.);
}

**// inline this function**
double rad2deg(double a_rad)
{
  return(a_rad*180./M_PI);
}

[B]// again, don't waste allocating and copying x, just return the result
// Also, consider inlining
[/B] double rand_uniform(double min, double max)
{
  srand( time(NULL) ); // **bad, only call srand once**
  double x=min+(max-min)*rand()/(double)RAND_MAX;
  return(x);

  **// return **min+(max-min)*rand()/(double)RAND_MAX;
}

```

---

### Post by hod139 on 2007-07-24
> **Mickeysofine1972 said:**
> BTW hod139 ty for pointing out that tan-1 is actually a atan!

Yeah, there is a huge difference between atan = arctan = tan^{-1} and 1/tan.

---

### Post by KIAaze on 2007-07-24
```
#include <stdio.h> should be #include <cstdio>
#include <stdlib.h> should be #include <cstdlib>
#include <iostream>
#include <math.h> should be #include <cmath>

```
Why?

```
using namespace std;  Not wrong, but frowned upon since it brings in the entire std namespace for just using std::cout and std::endl.

```
I didn't know it was bad. I was just trying to avoid the warnings. :)

```
// minor, consider inlining these functions for performance gain
```
Yeah, I suspected this coming up. It was just to separate the prototypes from the functions completely.

```
// If you are not going to use argc or argv why declare them?
```
Because I was planning on using them. ^^

```
// cos(a_rad) is very expensive.  You only have to call it once and store the result.  
Also, why do the 1/2 floating point division every time.  We know that answer is 0.5.  
Lastly, don't waste the time to allocate v0, then copy it in the return.  Compilers can do neat tricks with returning the result of an expression

```
Yeah, I don't have a lot of experience yet with speed optimizations. :roll:
I knew the storage trick, but didn't know that direct returns are faster.

---

### Post by hod139 on 2007-07-24
> **KIAaze said:**
> ```
#include <stdio.h> should be #include <cstdio>
#include <stdlib.h> should be #include <cstdlib>
#include <math.h> should be #include <cmath>

```Why?

The .h headers are deprecated and will eventually be dropped.  They only exist now to ease the transition to the C++ headers, which protect the standard template library in the std namespace.

> 
```
using namespace std;  Not wrong, but frowned upon since it brings in the entire std namespace for just using std::cout and std::endl.

```I didn't know it was bad. I was just trying to avoid the warnings. :)
Pulling in an entire namespace using the using directive also exists for legacy reasons, to ease the transition to namespace; however, it goes completely against the point of namespaces.   It will be good to get into the habit of using the std:: prefix, or pulling in only what you need.

---

### Post by Mickeysofine1972 on 2007-07-24
> **Wybiral said:**
> Algebraically solve for a given time using the typical physics formulas for projectiles.

X_vel = (X_destination - X_origin) / destination_time
Y_vel = -(Y_origin - 0.5 * gravity * pow(destination_time, 2) - Y_destination) / destination_time

You can get the power/angle from that vector.

This make alot more sense to me! Maybe I'm just a vector man lol

Mike

---


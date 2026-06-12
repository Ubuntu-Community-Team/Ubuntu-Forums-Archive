---
title: "what the hell is mcount.c??? (C++)"
date: 2009-07-26
forum: Programming Talk
---

### Post by PoopLoops on 2009-07-26
I'm making a gravity simulator in C++, which is being compiled on Ubuntu with GCC/G++.

If I up the number of crap flying around in my universe and bouncing off of each other, I get a segfault saying that mcount.c freaked out on line 60, because apparently, there is no such file or directory called mcount.c, which is confusing since I was just told that it is freaking out in absentia.  Here is the error I get:

```
Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb743b6c0 (LWP 18061)]
0xb7aa503a in __mcount_internal (frompc=134517640, selfpc=134516379) at mcount.c:60
60	mcount.c: No such file or directory.
	in mcount.c
(gdb) bt
#0  0xb7aa503a in __mcount_internal (frompc=134517640, selfpc=134516379) at mcount.c:60
#1  0xb7aa5b6f in mcount () from /usr/lib/debug/libc.so.6
#2  0x08048e9b in addVectors ()
#3  0x08049388 in Comet::move ()
#4  0x080494a7 in Comet::move ()
#5  0x080494a7 in Comet::move ()
#6  0x080494a7 in Comet::move ()

```

and it goes off to infinity with Comet::move ()

Comet::move () looks like this:

```

void Comet::move(double accel[], double sWidth, double sHeight, Uint32 deltaTicks)
{
	double tempVel[2];
	
	addVectors(accel,vel,vel); // addVectors(A,B,C) => C = A + B
	tempVel[0] = vel[0]*(static_cast<double>(deltaTicks)/35.0);
	tempVel[1] = vel[1]*(static_cast<double>(deltaTicks)/35.0);
	addVectors(tempVel,pos,pos);
	
	double sizes[2] = {sWidth,sHeight};
	
	for(int i = 0; i < DIMENSIONS; i++)
	{
		if( (pos[i] - radius < 0) || (pos[i] + radius > sizes[i]) )
		{
			vel[i] = -vel[i];
			move(accel,sWidth,sHeight, deltaTicks);
		}

		if( (pos[i] < -10) || (pos[i] > sizes[i] + 10) )
		{
			pos[i] = posInit[i];
			vel[i] = -0.1*vel[i];
		}
	}
}
```

and addVectors looks like this:

```

void addVectors(double A[], double B[], double total[])
{
	for(short i = 0; i < DIMENSIONS; i++)
	{
		total[i] = A[i] + B[i];
	}
}
```

DIMENSIONS is a const that is set in the same file as addVectors, which is a separate file from the one that Comet::move() is in, though.

So I can't tell what's wrong off the bat.  deltaTicks is just to calculate framerate, DIMENSIONS is set to 2.

I didn't notice this happening until I raised the number of objects on the screen.  However, what allowed me to do that in the first place was me implementing an object generator that uses GSL's random number generator for everything from position to velocity, size, mass, and color.  To seed the RNG, I use clock() and time(NULL) from time.h, though that is only to generate the objects, and the segfaults often happen after the program's been running for a few seconds.

I would have thought that if too much **** had been going on at once, things would slow down instead of crashing.  So I'm not sure if I am actually missing some file or if it's an old version or something.  Any help? :)

---

### Post by croto on 2009-07-26
Hi,

I see two calls to addVectors in Comet::move

addVectors(accel,vel,vel); // addVectors(A,B,C) => C = A + B
addVectors(tempVel,pos,pos);

The first call may segfault if accel or vel are not arrays of length larger or equal to DIMENSION. The second call may have problems if pos length is not >= DIMENSION (tempVel seems to be fine, although it is defined as an array of length 2, why not DIMENSION?). 
I'll double check that accel, vel and pos are fine (and not NULL for example). Print out some debugging information, like the value of those pointers at the entry point of the function.

---

### Post by PoopLoops on 2009-07-26
How would I do that using something like gdb?

So far everything is in 2D, so I am certain that the problem is not with DIMENSION and array sizes.  Also, errors would be a lot more certain if that were the case, whereas I really can't predict when I'll get a seg fault.  Sometimes it runs fine until I get bored of it, other times it gets a seg fault before any animation even starts.

Only thing I can think of off the top of my head is that the boundary detection calls move() again, with the only difference being a negative velocity.  So if the entire object was behind the boundary, it would keep flipping the sign of the velocity forever without getting anywhere.  But, that doesn't sit right with me because my object spawning has safeguards against that.  First I give the object a random radius, within some range.  Then I give it a random velocity in X and Y, also within a range.  Lastly I set the position, which has to be inside my screen of course.  The safeguard is that I make my max equal to my set max, minus the radius of the object, minus the velocity of the object, then multiply that number times the randomly generated number from 0-1.  Oh snap.  I guess I could get an object that spawns at 0 with a negative velocity... I'll have to fix that.

But that still leaves the problem of getting the same segfault mid-run.  Only thing I can think of is to have the loop update more often, so the objects can't "jump" the boundary and get stuck.  But I doubt that that is the problem in that particular case...

---

### Post by MadCow108 on 2009-07-26
how are you simulating gravity?
maybe your algorithm is not stable. multiple step methods have the tendency to do be unstable.

also it may well be the case that it sticks in a deadlock flippeng the velocity because it can land outside of boundaries due too rounding errors or numerical effects. Just checking when they get created is probably not safe enough.
That it will call move so long until the stack is exceeded and terminates with a sec fault.

---

### Post by PoopLoops on 2009-07-26
> **MadCow108 said:**
> how are you simulating gravity?
maybe your algorithm is not stable. multiple step methods have the tendency to do be unstable.

The seg faults also happen when I turn off gravity and just let the objects fly around and collide.  But to answer your question, I use Newton's law to calculate the acceleration of a given object, with r^2 + 0.0005 in the denominator in order to prevent any singularities.  Also, when two objects collide, I make them go through one move() "step" at zero acceleration so that they don't suck each other in through their boundaries.  But, like I said, this was all turned off and the seg faults were happening already.

> also it may well be the case that it sticks in a deadlock flippeng the velocity because it can land outside of boundaries due too rounding errors or numerical effects. Just checking when they get created is probably not safe enough.
That it will call move so long until the stack is exceeded and terminates with a sec fault.

Right.  That's a good point.  I have a safeguard against that in the form of checking how far past the boundary an object is and if it's too far, it gets teleported back to it's initial position and has its velocity divided by 10.  So, I could add in checking to see how many times velocity has been flipped, and if it goes over say 4 times, I'll skip to teleporting it back.

Secondly, the object could very well be teleported inside of another object, especially when I have a lot of crap flying around.  I can't think of a good way off the top of my head to protect against that.  When spawning objects, I just check if a new object's position would overlap with an already existing object's position.  If yes, then it generates a new position.  If it goes 2000 times without finding anything suitable, then it cancels that object and doesn't make any more (I get to decide how many it tries to make).

I think the first thing I'll do is have the objects go slower and see if that stops the segfaults from happening.  If yes, then I can make them go even slower and have the loop update more often to compensate.

Quick question, though.  I am using SDL for my graphics.  My screen is 800x600 pixels.  And it seems the minimum I can have something move is 1 pixel.  That makes it seem kind of choppy.  Is there some trick for making objects move smoother?  Like if I wanted to have an object move really slow, it would kind of jerk into position instead of smoothly moving, you know?

Oh, and thanks for all your help. :D

---

### Post by PoopLoops on 2009-07-26
Yeah, thinking about it some more, if I have an object of radius 2 pixels and it's going at a speed of 4px/s, then it can easily get inside of an object of radius 2 or less, which would still be close enough to a "singularity" and would account for why I see crap exploding outwards some times.  I'll have to make it update the state of each object four times as often, so technically the object would be moving at 1px/s, but it would still look as if it were going 4px/s.

---

### Post by MadCow108 on 2009-07-26
what you do sounds like an euler algorithm. do you actually get proper closed stable orbits?
if I remember correctly the euler method is not precise enough for planetary motion simulation.
You should look into Runge-Kutta methods or leapfrog if you need physically better results which are still relativly easy to implement.

edit: just tested out of boredom. euler doesn't even give a single stable orbit in a keppler problem unless the timestep is ridicilusly small :)
4. order runge-kutta is very accurate but results are still not physical as it violates energy/momentum convervation.
leapfrogs stays physical even for long times. so its probably the method of choice for simple problems.

so don't expect correct physical results from your program (except I misinterpreted your algorithm description)
attached my short script (beware: very inefficient code and bad style.. :) ). can be plottet with gnuplot

---

### Post by PoopLoops on 2009-07-26
The last iteration of my code had planets that were fixed in space and not effected by anything, and the comets would fly around them, not interacting with each other either.  I never encountered any problems with that setup, and the orbits looked stable for the amount of time I ran the program, which would be a few minutes at a time.  Running a simple setup of one planet and a single comet going in a circular orbit didn't give me any sort of deviations I could notice.

But my loop would take a single comet, and cycle through all the planets and add up their contributions, move that comet, then move on to the next comet.  That won't work if comets are affecting each other, since a comet would move before its contributions to other comets was factored in.  So I'll have to restructure it to calculate everything first and then move all the comets afterwards.

---

### Post by dribeas on 2009-07-27
Looks like a stack overflow to me. Check the method for recursive calls and whether you may be running into infinite recursion. Check that the conditions inside the for are appropriate.

---

### Post by PoopLoops on 2009-07-27
Yes, that was the problem.  I made the loop update more often and slowed down the in-game speeds, so everything still *looks* the same, but it's not as likely that an object will get past another object's boundaries.

This is kind of a crude safeguard, so I'm looking into continuous collision detection now.  Looks like I'll have to really overhaul my code. :)

---

### Post by MindSz on 2009-07-27
Just to clarify tho, the error you get is that mcount.c can't find the file or directory referred to in line 60, and not that mcount.c can't be found. :)

---

### Post by MadCow108 on 2009-07-27
here's what you can expect from the different algorithms I mentioned:
the first is euler with stepsize 0.001. it clearly is garbage although it has by far the smallest stepsize (it gets better for even smaller stepsizes).
the second is runge kutte 4 with stepsize 0.05, you see the orbit losses energy (also notice it goes berserk line when the orbit gets to small) although it gets better for smaller stepsizes it is still a major flaw because energy/momentum conservation must be preserved in classical physical systems
the third is leapfrog over driftnkick with stepsize 0.001. its very stable and it will always preserve energy as it is a so called symplectic integrator. But for bigger stepsizes you get orbit precession (but no energy drift!). There exist better leapfrog like algorithms which can reduce the need for the low stepsize but I would have to look them up

---

### Post by dribeas on 2009-07-27
> **MindSz said:**
> Just to clarify tho, the error you get is that mcount.c can't find the file or directory referred to in line 60, and not that mcount.c can't be found. :)

In fact it it gdb trying to find the code of mcount.c to show where the error occurred and failing to locate the source.

---

### Post by PoopLoops on 2009-07-27
> **MadCow108 said:**
> here's what you can expect from the different algorithms I mentioned:
the first is euler with stepsize 0.001. it clearly is garbage although it has by far the smallest stepsize (it gets better for even smaller stepsizes).
the second is runge kutte 4 with stepsize 0.05, you see the orbit losses energy (also notice it goes berserk line when the orbit gets to small) although it gets better for smaller stepsizes it is still a major flaw because energy/momentum conservation must be preserved in classical physical systems
the third is leapfrog over driftnkick with stepsize 0.001. its very stable and it will always preserve energy as it is a so called symplectic integrator. But for bigger stepsizes you get orbit precession (but no energy drift!). There exist better leapfrog like algorithms which can reduce the need for the low stepsize but I would have to look them up

I have no idea how to interpret those graphs, unfortunately.This started out as a dinky little simulator just to learn C++, but I think I will go ahead and find better algorithms for it and see how far I can take this.  If my ATI card actually supported 3D on Ubuntu, I'd try to use OpenGL to make the thing 3D.

But the funny thing is that you sometimes *want* energy loss, since energy gets radiated out all the time based on the temperature of an object, and collisions of macro objects don't always conserve momentum, since part of the energy gets absorbed as heat.  But I can factor that in later.

I've gotten rid of the seg fault, though.  It did have to do with getting an infinite recursion.

---

### Post by cheruvim on 2012-05-30
So does any one know the answer to the original question?

What the heck is mcount? I've been seeing a few installations fail because of mcount and I have no idea what it is.

---

### Post by cheruvim on 2012-05-30
> **cheruvim said:**
> So does any one know the answer to the original question?

What the heck is mcount? I've been seeing a few installations fail because of mcount and I have no idea what it is.


Here we go...

[http://freebsd.active-venture.com/FreeBSD-srctree/newsrc/libkern/mcount.c.html](http://freebsd.active-venture.com/FreeBSD-srctree/newsrc/libkern/mcount.c.html)

Interesting.

---

### Post by oldos2er on 2012-05-30
Closed. Please don't bump old threads.

---


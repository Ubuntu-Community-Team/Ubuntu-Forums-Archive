---
title: "HOWTO: Intro to OpenGL part 1 Using SDL"
date: 2006-12-06
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2006-12-06
Hi 

Theres a new HOWTO on the Ubuntu Games Developer Resource Wiki!

It was written by our OpenGL Guru Wybiral and we give a massive thumbs up to his work and contributions! 

Well done mate thats a blinder!

Heres the link:
[http://ubuntu-gamedev.wikispaces.com/](http://ubuntu-gamedev.wikispaces.com/)

Mike

---

### Post by hod139 on 2006-12-06
Just wondering, where should we leave comments about the tutorials: here in the thread or on the wiki.

---

### Post by Mickeysofine1972 on 2006-12-06
Hi Hod139!

In here will do fine ;-)

Mike

---

### Post by hod139 on 2006-12-06
Cool.  First, I'm glad to finally see some OpenGL code (I'm TA'ing a graphics class right now so I'm in full blown OpenGL mode!).

First, non-OpenGL specific comments,
About the code, I don't know why you started including the SDL headers again as:
```

#include <SDL/SDL.h>
```This is not the "correct" way (correct meaning portable) to include SDL.  From  the official SDL [website:]("http://www.libsdl.org/faq.php?action=listentries&category=2#19")
> 
**Q:****Do I #include <SDL.h> or <SDL/SDL.h>?** [B]
A:[/B]The most portable way to include SDL headers is to use quotes around the header name:
 #include "SDL.h"

I've mentioned this before and some of your tutorials include it the portable way, and others don't.  The beauty of SDL is that all your demos should run on Linux, Windows, Macs, etc (whatever SDL supports) but not if you don't include the headers correctly.  To compile the code on Ubuntu, you then use 
```

gcc `sdl-config --cflags --libs`
```Also, just a suggestion, in the event loops you should probably be checking for the following event:
```

event.type == SDL_QUIT

```This event corresponds to the user clicking the close box (the x in the top right corner of the window) with the mouse.  This is a natural way to close windows, and is something that most users probably expect.


As for the openGL specific comments, This line
```

SDL_SetVideoMode(width, height, 24, SDL_OPENGL | SDL_GL_DOUBLEBUFFER);

```doesn't seem right too me.  It seems to work, but shouldn't you be setting the surface to either hardware or software?  Maybe SDL has a default to software?  Anyways, SDL allows you to safely determine if the user has hardware support enabled, and the following snippet should probably go in your next tutorial.  
```

int videoFlags = SDL_OPENGL | SDL_GL_DOUBLEBUFFER;

// This checks to see if surfaces can be stored in memory
if ( videoInfo->hw_available )
   videoFlags |= SDL_HWSURFACE;
else
   videoFlags |= SDL_SWSURFACE;screen = SDL_SetVideoMode( W, H, BPP, videoFlags );
```In the discussion the following sentence appears:
> 
Next we have "glLoadIdentity" which simply resets our orientation...
This isn't quite true.  I know this tutorial is aimed at beginners, so you should either say don't worry about this line or be 100% accurate.

glLoadIdentity sets the *current matrix* to the identity matrix.  This may or may not be the modeling matrix.   It could for example be the projection matrix etc.  The reason it is important to call glLoadIdentity is because we use the modeling matrix to position and orient all the models in the scene (for example translate, rotate, skew), and most transformations multiply the current matrix by the specified matrix, and set the result to the current matrix.  If you don't clear it, then you continue to combine previous transformation matrices with the new one.

Again, this is kind of complicated material and can be skipped for the first tutorial, but I just wanted to clarify that glLoadIdentity doesn't "simply resets our orientation".  There are in fact many times when you don't want to call glLoadIdentity every frame.

In the discussion of the coordinate frame, you should mention that OpenGL uses a "right-handed" frame.  This is important because DirectX uses a left-handed system (so silly!!).  In the left handed system, positive z points into the screen, not out like in OpenGL's right handed system.

In the discussion about translations:
> 
```

glLoadIdentity();
glTranslatef(0, 0, -10);
// SNIP: Draw red square
glTranslatef(-3, 0, 0);
// SNIP: Draw blue square

```First we translate the entire coordinate system back 10 units (-10 on the Z axis), then we draw the red QUAD. Next we translate the entire coordinate system 3 units to the left (-3 on the X axis), then we draw the blue QUAD. You should notice two things, first, we didn't need to translate the blue QUAD back 10 units (remember, opengl is a STATE-machine, it only changes when we tell it to) because we already set the coordinate system back. Secondly, when we translated the coordinate system to the left before we drew the blue QUAD, we didn't affect the red QUAD at all... Remember, if it's already drawn the before the translation, then the translation will not affect it
This analysis is not correct.  Let M represent the current modelView matrix, T_z translation matrix in the z direction, and T_x the translation matrix in the x direction.  Here is what is really going on:
M = IdentityMatrix
M *= T_z(-10)
Draw red square, and multiply coordinate frame by current M
M *= T_x(-3)
Draw blue square, and multiply coordinate frame by current M

The state machine analysis isn't really correct.  
> 
Remember, if it's already drawn the before the translation, then the translation will not affect it
This is perhaps all that you should have said at this point.

For rotations, you should mention that a positive rotation rotates counter-clockwise about the positive axis.  Another common problem that arises with openGL rotations is that the openGL commands want degrees, where all math commands want radians.  Just remember that.

> 
Here is an example...
 ```
        glTranslatef(0, 0, -10);

        glRotatef(45, 0, 0, 1);

        glBegin(GL_QUADS);
        glColor3f(1,0,0);
        glVertex3f(-1, 1, 0);
        glVertex3f( 1, 1, 0);
        glVertex3f( 1,-1, 0);
        glVertex3f(-1,-1, 0);
        glEnd();
``` First, we pushed the coordinate system back so we can see, then we rotated the coordinate system 45 degree's on the Z axis.
WRONG!  First the quad is rotated 45 degrees about the z-axis, followed by a translation of -10 units in the z direction. The translation operations happen from the bottom up.  Think back to the modelView matrix I mentioned eariler.  In this case: M = T_z(-10) * R_z(45).  Let P equal a point that OpenGL moves, the transformation looks like:
P' = M*p 
P' = T_z(-10) * R_z(45) *P.
Now perhaps it is more clear that the rotation is being applied first (see hos the first operation on P is the rotation).


PHEW, sorry for the long post.  Guess I had a lot to say.

---

### Post by VDM on 2006-12-06
Nice comments, hod139. I hope this gets edited into the article.

Havn't read it all in depth, but i sure will.
There still is a simple top view 3d game on me todo list, so ill be following this part with intrest!

Keep up the work! :mrgreen:

---

### Post by Mickeysofine1972 on 2006-12-06
> **hod139 said:**
> Cool.  First, I'm glad to finally see some OpenGL code (I'm TA'ing a graphics class right now so I'm in full blown OpenGL mode!).

First, non-OpenGL specific comments,
About the code, I don't know why you started including the SDL headers again as:
```

#include <SDL/SDL.h>
```This is not the "correct" way (correct meaning portable) to include SDL.  From  the official SDL [website:]("http://www.libsdl.org/faq.php?action=listentries&category=2#19")
I've mentioned this before and some of your tutorials include it the portable way, and others don't.  The beauty of SDL is that all your demos should run on Linux, Windows, Macs, etc (whatever SDL supports) but not if you don't include the headers correctly.  To compile the code on Ubuntu, you then use 
```

gcc `sdl-config --cflags --libs`
```Also, just a suggestion, in the event loops you should probably be checking for the following event:
```

event.type == SDL_QUIT

```This event corresponds to the user clicking the close box (the x in the top right corner of the window) with the mouse.  This is a natural way to close windows, and is something that most users probably expect.


As for the openGL specific comments, This line
```

SDL_SetVideoMode(width, height, 24, SDL_OPENGL | SDL_GL_DOUBLEBUFFER);

```doesn't seem right too me.  It seems to work, but shouldn't you be setting the surface to either hardware or software?  Maybe SDL has a default to software?  Anyways, SDL allows you to safely determine if the user has hardware support enabled, and the following snippet should probably go in your next tutorial.  
```

int videoFlags = SDL_OPENGL | SDL_GL_DOUBLEBUFFER;

// This checks to see if surfaces can be stored in memory
if ( videoInfo->hw_available )
   videoFlags |= SDL_HWSURFACE;
else
   videoFlags |= SDL_SWSURFACE;screen = SDL_SetVideoMode( W, H, BPP, videoFlags );
```In the discussion the following sentence appears:
This isn't quite true.  I know this tutorial is aimed at beginners, so you should either say don't worry about this line or be 100% accurate.

glLoadIdentity sets the *current matrix* to the identity matrix.  This may or may not be the modeling matrix.   It could for example be the projection matrix etc.  The reason it is important to call glLoadIdentity is because we use the modeling matrix to position and orient all the models in the scene (for example translate, rotate, skew), and most transformations multiply the current matrix by the specified matrix, and set the result to the current matrix.  If you don't clear it, then you continue to combine previous transformation matrices with the new one.

Again, this is kind of complicated material and can be skipped for the first tutorial, but I just wanted to clarify that glLoadIdentity doesn't "simply resets our orientation".  There are in fact many times when you don't want to call glLoadIdentity every frame.

In the discussion of the coordinate frame, you should mention that OpenGL uses a "right-handed" frame.  This is important because DirectX uses a left-handed system (so silly!!).  In the left handed system, positive z points into the screen, not out like in OpenGL's right handed system.

In the discussion about translations:
This analysis is not correct.  Let M represent the current modelView matrix, T_z translation matrix in the z direction, and T_x the translation matrix in the x direction.  Here is what is really going on:
M = IdentityMatrix
M *= T_z(-10)
Draw red square, and multiply coordinate frame by current M
M *= T_x(-3)
Draw blue square, and multiply coordinate frame by current M

The state machine analysis isn't really correct.  
This is perhaps all that you should have said at this point.

For rotations, you should mention that a positive rotation rotates counter-clockwise about the positive axis.  Another common problem that arises with openGL rotations is that the openGL commands want degrees, where all math commands want radians.  Just remember that.

WRONG!  First the quad is rotated 45 degrees about the z-axis, followed by a translation of -10 units in the z direction. The translation operations happen from the bottom up.  Think back to the modelView matrix I mentioned eariler.  In this case: M = T_z(-10) * R_z(45).  Let P equal a point that OpenGL moves, the transformation looks like:
P' = M*p 
P' = T_z(-10) * R_z(45) *P.
Now perhaps it is more clear that the rotation is being applied first (see hos the first operation on P is the rotation).


PHEW, sorry for the long post.  Guess I had a lot to say.

For someone who said they didn't have time to contribute to our project you have an awful lot to say! :-D

I can't comment on the suggestions on that HOWTO as I am not familiar with OpenGL and if time had allowed I would have been able to research this myself. As it is, I read through this myself as a newbie and found it very informative, I'm looking forward to the next one actually!

However, on the point about the SDL headers, I have tried your suggestion and have also gotten other ubuntu users to try using your method and also mine. Yours either doesn't work on edgy or generates errors that don't exist. So, because I am interested in Ubuntu/Linux games development, mostly ubuntu I might add, I chose to go with the option that works for MOST of us. So far your the only person that has commented and said that its a problem. Everyone else who reads these howtos has found that to be fine.

Really Mr Hod139 you could have used the time it took to write this post to write a howto and help us out!

Mike

---

### Post by Wybiral on 2006-12-06
I'm aware of all the things you pointed out (except the "SDL.h" thing, but that wasn't really the topic of the tutorial). And, as far as everything else goes, I know how OpenGL's matrix stack works, I worded things the way I did because I didn't want to blow someones mind with matrix mathematics if they're just getting into 3d. I wanted this tutorial to be readable to people who understand very little math. I do intend to write more parts to this and I will clarify later on... But for now, people do NOT need to know all of that to use OpenGL and IMO, it would only confuse them at this point.

---

### Post by Mickeysofine1972 on 2006-12-06
> **Wybiral said:**
> I'm aware of all the things you pointed out (except the "SDL.h" thing, but that wasn't really the topic of the tutorial). And, as far as everything else goes, I know how OpenGL's matrix stack works, I worded things the way I did because I didn't want to blow someones mind with matrix mathematics if they're just getting into 3d. I wanted this tutorial to be readable to people who understand very little math. I do intend to write more parts to this and I will clarify later on... But for now, people do NOT need to know all of that to use OpenGL and IMO, it would only confuse them at this point.

Well said!

Mike

---

### Post by hod139 on 2006-12-06
First, if I sound like I am attacking anything that has been done I am not.  I know it takes a lot of time and effort to produce these tutorials and I think you have done a wonderful job in getting stuff working.  That said...

> 
However, on the point about the SDL headers, I have tried your suggestion and have also gotten other ubuntu users to try using your method and also mine. Yours either doesn't work on edgy or generates errors that don't exist. So, because I am interested in Ubuntu/Linux games development, mostly ubuntu I might add, I chose to go with the option that works for MOST of us. So far your the only person that has commented and said that its a problem. Everyone else who reads these howtos has found that to be fine.
If sdl-config is not working in Edgy then we really should file a bug report, as that is the "correct" or portable way to use SDL.  I did not know it was not working in Edgy (I am running dapper), and as such I agree that you should go with what works for now.

> 
Really Mr Hod139 you could have used the time it took to write this post to write a howto and help us out!
Not that I have to defend myself, but I feel I need to.  It took me about 20 minutes to read the howto and write the reply.  It would take me much much longer to write a howto from scratch and I don't have the kind of time right now.  As hinted to in my earlier post, I am a graduate student and this is the so called crunch time of the semester.  I plan on writing a couple of guides during the semester break, probably on collision detection and perhaps particle systems.  Time willing, maybe even an article on dynamic simulation.  These will all take some time to write correctly though, and I want to make sure anything I write is of the highest quality.

As I said earlier, it is much easier and less time consuming to read and critique a howto than it is to write one.  You have to remember when writing a howto that many people (some even experts in the field that you didn't expect) will be reading it.  When reading guides, one implicitly (and often incorrectly) assumes the author is an expert in the field and trusts the advice.  If this advice is wrong than that serves no one.  Please don't take any of my criticisms personally, they are only meant to ensure that the material posted is correct and of the highest quality.

If you want to send me review drafts of howtos before posting them then I will find the time to read them and make comments privately.  I just don't have the time at the moment to commit to writing a guide from scratch.

---

### Post by Mickeysofine1972 on 2006-12-06
I look forward to your contributions

Mike

---

### Post by Wybiral on 2006-12-06
I certainly understand where you are coming from and I take no offense to your comment. You are right, if I were writing an OpenGL reference book or something then it would be terribly wrong. But it is called "Intro to OpenGL part 1".

I've written a number of tutorials before and I am aware that even if it is good (not saying that this particular one is great or anything), there will always be people out there trying to look smarter then the author (not say that thats what you did, I'm just saying I'm used to this kind of critique)

---

### Post by hod139 on 2006-12-06
> **Wybiral said:**
> I certainly understand where you are coming from and I take no offense to your comment. You are right, if I were writing an OpenGL reference book or something then it would be terribly wrong. But it is called "Intro to OpenGL part 1".

I've written a number of tutorials before and I am aware that even if it is good (not saying that this particular one is great or anything), there will always be people out there trying to look smarter then the author (not say that thats what you did, I'm just saying I'm used to this kind of critique)
I understand how personal one's own code can be, and when it gets critiqued how it feels.  I'm glad you realize that I'm not attacking you or anything you have done.  I think these tutorials are an excellent idea and  contributers deserve praise.

I hope I haven't come across as trying to look smarter.  My goal is not to prove anybody wrong, demean any work, nor look smarter.  My goal is only to have the best tutorials possible.

> **Wybiral said:**
> I'm aware of all the things you pointed out (except the "SDL.h" thing, but that wasn't really the topic of the tutorial). 
And, as far as everything else goes, I know how OpenGL's matrix stack works, I worded things the way I did because I didn't want to blow someones mind with matrix mathematics if they're just getting into 3d. I wanted this tutorial to be readable to people who understand very little math. I do intend to write more parts to this and I will clarify later on... But for now, people do NOT need to know all of that to use OpenGL and IMO, it would only confuse them at this point.


Again, please don't take anything I am about to say personally. I am only offering my advise to the tutorial, and you can do with it whatever you want to. If you want to ignore my advice fine, that is your right as the author of the guide. I do however stand by everything I wrote.

> I know how OpenGL's matrix stack worksFrom what you wrote you gave the impression that you didn't. What you wrote about glLoadIdentity was wrong, but more troubling was what you wrote here:
> 
                                                Here is an example...
      ```

             glTranslatef(0, 0, -10);

        glRotatef(45, 0, 0, 1);

        glBegin(GL_QUADS);
        glColor3f(1,0,0);
        glVertex3f(-1, 1, 0);
        glVertex3f( 1, 1, 0);
        glVertex3f( 1,-1, 0);
        glVertex3f(-1,-1, 0);
        glEnd(); 

```First, we pushed the coordinate system back so we can see, then we rotated the coordinate system 45 degree's on the Z axis.
This is wrong (as pointed out in my previous post) and is what led me to believe that you didn't understand how the matrix stack works.

It is my experience that if you don't want to cover a specific topic yet, then don't.  Just say it is magic, or that you will better explain it later.  The worse thing to do though is give half answers.  That only leads to more confusion down the road.  So my opinion is either explain something fully, or not at all.

> 
I didn't want to blow someones mind with matrix mathematics if they're just getting into 3d. I wanted this tutorial to be readable to people who understand very little math.
I have to disagree here.  I'm of the opinion that if you want to do graphics programming and advanced game programming then you better know the math.  You best know what matrices and vectors are, and hopefully some linear algebra.  Maybe the first tutorial should have been a review of matrix math, and some basic concepts from linear algebra that might be needed.

---

### Post by Mickeysofine1972 on 2006-12-06
Thats why we write these HOWTOS.

But we wouldn't be so unkind to snow our readers under with unnecessary and complex information.

In time we will build on the existing HOWTOS and built knowledge through a series of good experiences with these topics and not through a draconian do or die method of teaching. Our readers are not assumed to be academics but 'Human' which is in keeping with the spirit of Ubuntu if I remember correctly.

I reviewed this material before I post the information and as a experienced teacher of six years I feel that it accomplishes the goals of our long term plan to display helpful and encouraging learning materials to the community that we are part of.

Mike

---

### Post by Wybiral on 2006-12-06
> I have to disagree here. I'm of the opinion that if you want to do graphics programming and advanced game programming then you better know the math. You best know what matrices and vectors are, and hopefully some linear algebra. Maybe the first tutorial should have been a review of matrix math, and some basic concepts from linear algebra that might be needed.

And thats where you would have lost a lot of people. I started out with OpenGL WITHOUT knowing anything about matrices. For most simple games in OpenGL you do need to know vectors, but you do not need to understand matrices yet.

As far as the "we pushed the coordinate system back so we can see, then we rotated the coordinate system 45 degree's on the Z axis"...

What's not true about that? I was obscuring from that fact that we were using matrix multiplication (which I tried to maintain throughout the entire tutorial).

> WRONG! First the quad is rotated 45 degrees about the z-axis, followed by a translation of -10 units in the z direction. The translation operations happen from the bottom up.

WRONG! I was expressing everything in terms of the entire coordinate system, and following the order of operations, the entire coordinate gets "pushed back" and THEN it "rotates" around it's center. You are never "rotate" the quad.

---

### Post by hod139 on 2006-12-06
> **Mickeysofine1972 said:**
> Thats why we write these HOWTOS.

But we wouldn't be so unkind to snow our readers under with unnecessary and complex information.

In time we will build on the existing HOWTOS and built knowledge through a series of good experiences with these topics and not through a draconian do or die method of teaching. Our readers are not assumed to be academics but 'Human' which is in keeping with the spirit of Ubuntu if I remember correctly.

I reviewed this material before I post the information and as a experienced teacher of six years I feel that it accomplishes the goals of our long term plan to display helpful and encouraging learning materials to the community that we are part of.

Mike
Agreed.  I guess my expectations of what knowledge people reading the OpenGL tutorials should have is higher than yours.  This is why I think a "Math Review" would be useful before attempting the OpenGL tutorials, this way you wouldn't have to avoid these complex issues when writing the tutorials.

---

### Post by Wybiral on 2006-12-06
You have a good point too. BTW, I am not trying to be defensive or anything, just clarifying my decisions to do things the way I did. I am a big fan of open source and free education and I don't see any reason we shouldn't settle on the fact that we both view this from a different approach. My way is to get them using OpenGL and playing around with it before they have to learn all of the interior (imagine if you needed a degree in mechanics before you were allowed to take drivers-ed... That would suck) but I also see your point that if you want to learn 3d programming the professional way, you are going to need some knowledge in algebra, calculus, and trigonometry. Personally, I just believe that anyone can use OpenGL, even if they don't "understand" it, they will learn it intuitively.

---

### Post by hod139 on 2006-12-06
> **Wybiral said:**
> And thats where you would have lost a lot of people. I started out with OpenGL WITHOUT knowing anything about matrices. For most simple games in OpenGL you do need to know vectors, but you do not need to understand matrices yet.

Personally, and this is just my opinion, a strong base in matrix/vector math is needed for graphics programming.  Do you have to know what the gluPerspective function is doing to begin openGL programming: no.  But should know what a point, vector, or shape primitive is, and how to manipulate them: yes.  This requires basic matrix vector math abilities.  Again, this is just my opinion and I seem to be in the minority.  I'm not challenging your opinion, only when you write something that is incorrect (see below).

> 
As far as the "we pushed the coordinate system back so we can see, then we rotated the coordinate system 45 degree's on the Z axis"...

What's not true about that? I was obscuring from that fact that we were using matrix multiplication (which I tried to maintain throughout the entire tutorial).

WRONG! I was expressing everything in terms of the entire coordinate system, and following the order of operations, the entire coordinate gets "pushed back" and THEN it "rotates" around it's center. You are never "rotate" the quad.I'm not wrong, but maybe I'm not being clear.  To eliminate some of the confusion, the code in question is:
```

        glTranslatef(0, 0, -10);
        glRotatef(45, 0, 0, 1);

        glBegin(GL_QUADS);
        glColor3f(1,0,0);
        glVertex3f(-1, 1, 0);
        glVertex3f( 1, 1, 0);
        glVertex3f( 1,-1, 0);
        glVertex3f(-1,-1, 0);
        glEnd();

```and your explanation of what is going on is:
> 
First, we pushed the coordinate system back so we can see, then we rotated the coordinate system 45 degree's on the Z axis.
Your description of that code block is wrong, you have the ordering of the transformations backwards.  Even if I leave the matrices out, what is happening is this:

First a GL_QUAD is draw (in this case it is a red square), then it is rotated 45 degrees about the z-axis, lastly it is translated (pushed) -10 units along the z-axis.  The rotation happens first, followed by the translation.

---

### Post by Wybiral on 2006-12-06
That may be what is happening to the matrices inside the OpenGL machine... But, imagine if you will the 3d coordinate system. Use your hand as an example... First move your hand away from your face (back on the Z axis), then rotate it along it's Y axis. That should make perfect sense. HOWEVER, if you were to rotate the coordinate system first (so rotate your hand) and THEN move your hand back on it's "Z" axis, it would not be pointing straight back, the coordinate system has shifted, the Z axis is no longer perpendicular to the monitor. I hope this makes sense... I see what you are saying, but I believe the method I am using to describe it makes much more sense to someone knew to 3d programming.

---

### Post by hod139 on 2006-12-06
What you just described is known as a moving frame rotation.  While powerful in certain situations (e.g. articulated bodies, dynamics, etc), this is not what you wrote in the openGL code; but at least now I understand what you are thinking.  The reason it works for your code is the translation matrix does not alter the coordinate system axes.  Imagine though if you wanted to perform two rotations, 
```

glRotatef(45, 0, 0, 1);
glRotatef(90, 1, 0, 0);
// Draw something

```In this case, it is important to realize that the 90 degree rotation about the x-axis will happen before the 45 degree rotation about the z-axis.  The ordering of the matrices is important because rotations are not commutative, that is you will get different results for different orders of rotation.  R1*R2  != R2*R1

As for which representation is easier, that I don't know.  Some people find that it is easier to work with a fixed set of axis, while others like to attach the frame to the body.  I say, use the right frame for the right job.

**Edit:**  I should add, without proof, that 
M1 = R1*R2 (about world fixed frame)
M2 = R2*R1 (about body fixed frame)
M1 = M2

---

### Post by RiggenBlaque on 2006-12-06
First of all, great job with the howto, its very easy to follow.

Second, is it just me, or can libsdl-1.2debian-alsa and libsdl-1.2debian-oss not be installed at the same time?  You try and install one and it tells you it must uninstall the other.

Third, is there any difference between libsdl-1.2debian-alsa and libsdl1.2debian-alsa (minus the first hyphen), i can only find the 2nd one.

edit:
Also, your SDL test program compiles and works, but when trying to compile IOQuake3, i get 
```

build/release-linux-i386/client/sdl_glimp_smp.o: In function `IN_JoyMove'
sdl_glimp.c:(.text+0x6): multiple definition of `IN_JoyMove'
```


Any idea what thats all about

---

### Post by Mickeysofine1972 on 2006-12-07
> **RiggenBlaque said:**
> First of all, great job with the howto, its very easy to follow.

Second, is it just me, or can libsdl-1.2debian-alsa and libsdl-1.2debian-oss not be installed at the same time?  You try and install one and it tells you it must uninstall the other.

Third, is there any difference between libsdl-1.2debian-alsa and libsdl1.2debian-alsa (minus the first hyphen), i can only find the 2nd one.

edit:
Also, your SDL test program compiles and works, but when trying to compile IOQuake3, i get 
```

build/release-linux-i386/client/sdl_glimp_smp.o: In function `IN_JoyMove'
sdl_glimp.c:(.text+0x6): multiple definition of `IN_JoyMove'
```


Any idea what thats all about

Hi 

Unfortunately I have only seen SDL allow you to install one or the other in terms of audio support libraries so you could use either and that would be fine. You must remember though that if you compile binaries, the target system must have that sound system too.

Secondly, with regards to your IOQuake3 problem, It could be that you have the function written twice, a variable of the name name as your function or even that you have used the header file somewhere else and the definition has already been made before.

Mike

---

### Post by Shrooms on 2008-04-26
Just wanted to say: Thanks, dude! That's just what I was searching for! :)

---

### Post by Mickeysofine1972 on 2008-04-27
> **Shrooms said:**
> Just wanted to say: Thanks, dude! That's just what I was searching for! :)

Glad we could help and Kudos to wybiral who wrote it!

Mike

---


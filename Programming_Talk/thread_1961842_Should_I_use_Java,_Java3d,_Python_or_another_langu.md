---
title: "Should I use Java, Java3d, Python or another language"
date: 2012-04-19
forum: Programming Talk
---

### Post by schievelbein on 2012-04-19
I am starting my dissertation and need some advise. I have a massive amount of 3D spatial data in spreadsheets that could be put into a database if needed. This data is coordinated for vertices of 3d polyhedrons. I need to manipulate the data and see the results in real time.

A more detailed explanation is that I need a 3D State Model Engine. I need to be able to set the position of the objects in 3D space using the stored data, and as I change the state of one object, I need to know how it will affect the other objects. I then need to write this data back to the database/spreadsheet for analysis.

An example is that I have 3 dice in a row from left to right with different colored faces instead of numbers.  I need to be able to change the state of the left dice by rotating it for example on the x-axis and have dice #2 possible rotate according to a set of rules and if it does, I need dice #3 to possibly rotate.  I then need to expand this to 3 dimensions with 3 dices in each direction, and then expand it to 100 dice in each direction.  I need visual representation in order to do some state analysis that I do not believe current pattern recognition could accomplish.  The rotation of the initial dice should be able to be done with a mouse in a 3d environment or by changing a state value for example rotate((dice 14,23,77), z-axis, 90 degrees).

To go further with the example,  change the dice to 3 spheres sitting side by side with magnetic fields on each sphere. As I rotate any one sphere, it will cause the other spheres to rotate dependent on the field strengths. This is NOT a one-to-one like gears, but analog influence, different spheres have different affects on other spheres. To make matters worse, this is in 3D space. If I rotate along X-axis, it affects the surrounding objects in one way, Y-axis different objects, and Z-axis different objects.  These could also by polyhedrons with 100s of sides if need for the program.

The final problem is speed,  A similar example would be to start small with a 6 sided dice with number/color on each side.  I then want to be able to duplicate the shape, for example, have 10 6-sided dice in a row, by 10 dice deep by 10 dice high. I then want to be able to program some rules, such as if I move a dice from side '1' facing forward to side '4' facing forward, then the dice to the left rotates on the X axis, and the dice to the right rotates on the Y axis, etc. As each dice is moved, they all continue to move until they reach an equilibrium depending on the rules.  

I have different molecules that have different magnetic properties that I want to program the interactions with, and see how they react when I start having dozens of polyhedrons and the 100s of associated actions.

I have searched under '3D State Models' and 'Molecular Animations' and many similar things, but I must be missing it somewhere. I do not mind learning another programming language, I have learned many over the years., but do not want to spin my wheels and waste time.  I would like to know if there are any programs that can do what I need or if I should go back to Java and dive deeper into it.  Any and all suggestions are welcomed.  I really like Mint/Ubuntu, but would be willing to use Windows if somebody had a Windows only solution.

I am pretty sure that I am going to need to write this application from scratch, so I am wondering if Java, or Java3D or Python or another language would be the best option.  I have written Java many years ago, but have not kept up on the languages and 3D transformation classes enough to know what my best bet is nowdays.  Any and all thought and opinions are welcome.

---

### Post by PaulM1985 on 2012-04-20
This sounds something that Matlab would be able to manage well.  For your dissertation do you need to develop a standalone product or are the results from the simulations the important part?

If you only need the results and display/create graphical images, have a look into Matlab (or Octave, which is similar and free).

If I were to do this and create a standalone application I would probably use Java with OpenGL.

Paul

---

### Post by 11jmb on 2012-04-20
How much number crunching are we talking? it sounds like your project can get pretty computationally complex. Perhaps you can use C as your computation language, access it with jni or swig, and use java pr python to program graphics and access a database (if you need one). If you know java, c shouldn't be too hard to pick up.


If computation time should not be an issue, there's no need to use C. Python is usually my first choice for quick development when speed is not critical.

---

### Post by PaulM1985 on 2012-04-20
Just expanding a little from what I said earlier.
Matlab/Octave both handle matrix multiplication and transformation of vectors so there is no need to write extra classes to do this.  They also support other matrix operations such as inversing, transposing etc.  Graphical display is simple with these aswell since they have their own built in plot functions which will plot points, lines, surfaces etc in 3d.

If you want to use Java, there is JAMA: [http://math.nist.gov/javanumerics/jama/](http://math.nist.gov/javanumerics/jama/), a Java matrix library which should provide you with some of the classes that you need, saving you having to write them.

Paul

---

### Post by 11jmb on 2012-04-20
So i'm trying to wrap my head around your problem, and it seems like your computation time is going to be very high for sufficiently large spaces. C/C++ may be your best answer for the computation, and you can decide later if you want to keep the entire project in C or want to use an easier language for files/graphics.

What kind of computation will your code need to perform? In other words, do you think you'll need to use libraries for: linear algebra, fft, etc?

---

### Post by schievelbein on 2012-04-20
I really appreciate the help in the brainstorming.
The attached image 'multicube_10.png' is an example created using antiprism, and has a great beginning for what I need, but the creation of the image is not even close to being useful (10+ minutes).

To expand on what I need - an example:
I need be able to read the data for this matrix from a database and create the current 'state-image'.  I then need to be able to change the state of one of the cubes, lets say the very top left cube, by  using a command similar to (rotate.cube(0,0,0), z-axis, 270 degrees).  This would cause the cube to rotate on the z-axis clockwise 270 degrees.  This would cause a set of possible cascading actions depending on rules encapsulated in the each cube.  Depending on the rules, the cube right behind it might rotate CCW 180 degrees and the cube to the right of it might NOT rotate, but the cube below it might rotate on both the X and Y axis, 90 degrees each.  All of this is depending on the rules.  As each of these three cubes may or may not rotate, they will cause others to rotate if a turn based methodology based on the speed coefficient of the cube receptors.

As each one of these actions takes place, I want to see the cubes change on the screen, so that I can observe the impact certain changes to to the state model.  My dream of course it to someday be able to run millions of scenarios with all of the associate permutations and combinations, and let the computer do the trend analysis using pattern recognition of some kind to detect such as "changing a bottom row cube with a Z-axis CCW rotation, results in all cubes on the top row turn pink edge up".  This is an example, but gives you an idea of what I am looking for.

To give you an idea of the final model, I need 1000x1000x1000 cubes, which would result in minimum of 1,000,000,000 per cycle.  Similar to the old game of COMPUTER LIFE, these cascades could continue indefinitely along with the induction of new data at any cycle point.  

The more that I type and think about this, the more that I think I might want to take some of LIFE code and adapt it to 3D...... just thinking.....
This is all and engineering dream, but it is funny how games fit in.

Any and all suggestions or criticisms are welcome and encouraged.

---

### Post by PaulM1985 on 2012-04-20
As I mentioned earlier, Matlab is good, but from the sounds of it, it seems that speed is very important to you and you want to be able to see things in a very short period of time, rather than apply a change and come back in half an hour to see what it did.

If this is the case (ie time is more important than results) I would agree with 11jmb and say that maybe you should be looking at C++ rather than Java.

One other thing to be aware of, if you have 1,000,000,000 cubes, which are defined from 8 points of 3 doubles, you have to store 24,000,000,000 doubles just to represent your state.  Doubles are 8 bytes, so this equates to approximately 178.8GB.  So to model this you would have to be constantly reading/writing to hard disk, in which case whatever programming language you use is not going to matter since it is always going to be too slow to use.

Might be worth using Java because the IO to the database would be easier.

Paul

---

### Post by schievelbein on 2012-04-20
Thank you for pointing out some of my problems to me.
I only have 24GB or RAM on my dekstop, and I want to do as much of the work in memory, so I need to evaluate my data a little more bfore proceeding, thanks for the help.

---

### Post by juancarlospaco on 2012-04-20
You are describing Blender and/or FreeCad.
Both uses Python and are very powerful...

---

### Post by schievelbein on 2012-04-20
Am I missing something, but I understood that Blender and FreeCad we both drawing applications that could render the final outcomes for m, but they could not do real time visualisation of data from a data source using the methods I described.  Have they added capability that I am unaware of?

---

### Post by llanitedave on 2012-04-20
> **PaulM1985 said:**
> As I mentioned earlier, Matlab is good, but from the sounds of it, it seems that speed is very important to you and you want to be able to see things in a very short period of time, rather than apply a change and come back in half an hour to see what it did.

If this is the case (ie time is more important than results) I would agree with 11jmb and say that maybe you should be looking at C++ rather than Java.

One other thing to be aware of, if you have 1,000,000,000 cubes, which are defined from 8 points of 3 doubles, you have to store 24,000,000,000 doubles just to represent your state.  Doubles are 8 bytes, so this equates to approximately 178.8GB.  So to model this you would have to be constantly reading/writing to hard disk, in which case whatever programming language you use is not going to matter since it is always going to be too slow to use.

Might be worth using Java because the IO to the database would be easier.

Paul

Wouldn't Java with JIT compilation be fairly close to C++ performance anyway?

---

### Post by schievelbein on 2012-04-20
I have also received emails suggesting JOGL ([http://jogamp.org/jogl/www/](http://jogamp.org/jogl/www/)) and JMonkeyEngine, all which seem to be able to do the work, but I am at a loss as to which is the fastest and which will be able to do all of the things I described above.  I also received some emails stating that I should stay away from Java3d and JavaFX because they are on their way out and will not have the support I may need in the future.  I also had PROCESSING suggested to me, but it blew up on a simple 100x100x100 matrix and I need to go at least a magnitude larger (*1000), but I will continue to evaluate it, as it seems to have similar projects as large as mine, maybe I just messed it up....

Other comments and suggestions are welcome.

---


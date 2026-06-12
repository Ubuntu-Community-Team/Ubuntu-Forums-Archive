---
title: "What can I achieve with Python?"
date: 2010-06-21
forum: Programming Talk
---

### Post by RobinBrown on 2010-06-21
My sixth form is offering an "Extended Project Qualification", which is basically what it says on the tin: a project on a subject of your choosing, to do over the summer holidays. The guidelines say that it should take approximately 120 hours of work, including a diary/log. The project is weighted the same way as an AS level.

As I hope to be doing a degree in physics after my A-levels, I thought it may be useful to learn how to program, and this would be a good way to get some (UCAS) recognition. After trawling the forums, it appears that the best language to learn would be python. I have previously dabbled in c++, and so am not a total stranger to programming. Python seems to have a reputation for being easy to learn, so my question is this: What can I achieve in python in 120 hours? Or rather, how complex a program could I write with said knowledge and time?

Suggestions for a final program would be more than welcome. I need to have a rough and ready plan of action and title by Wednesday (23/6/10), so post quickly! :)

Thanks in advance!

Robin

---

### Post by Reiger on 2010-06-21
120 hours should be sufficient, assuming you have taken the Math, create a little application that can draw sketches suitable for Euclidean geometry type problems (in 2d). Think bisectors, perpendiculars, ellipses, parabolas, hyperbolas, polygons, that kind of work.

It's not physics, I know.

---

### Post by PaulM1985 on 2010-06-21
Hi

I have to admit I do not know much about Python but have had a look at some code.

If you have 120 hours, maybe you could look at some sort of basketball model where you have a player on the left and a net on the right.  The user chooses an angle for the player to throw at and a speed for the throw and you can use physics to work out if the ball would go through the net.  (Just working in 2d rather than 3d).

I don't think this would be overly ambitious and you get some physics in.

Paul

---

### Post by robots.jpg on 2010-06-21
With some basic programming experience, I wouldn't doubt that you could create a decent form-based application using Python with wxPython or PyQt in that time frame.  I would work through the official Python tutorial, and then move on to one for the GUI package of your choice.  

I had some background in C++ and Visual Basic before I learned Python, and it took me about to week to get to the point where I was comfortable enough with the language and built-in features to start designing applications.

If you're considering creating a visual simulation or something that uses a package like Pygame for more advanced graphics, you'll probably have at least twice as much learning to do on top of your application design.  I wouldn't do that unless you really want a challenge.


Expanding on the basketball idea, maybe a program where you could set up a number of environmental variables like wind speed and direction, atmospheric pressure, gravity, and then launch an object with variable size, shape, and mass at a specific angle, and measure the distance traveled, maximum height and velocity, etc.  I haven't used them personally, but I think both of the GUI packages I mentioned earlier have widgets for plotting and displaying simple 2D graphics if you want to use those tools.

---

### Post by soltanis on 2010-06-21
With 120 hours you can do quite a lot with python, certainly much more than something like C. If you do decide to do any physical simulation, it certainly won't be very fast (or as fast as it could be with C or FORTRAN) but it will most likely get done within your time frame.

---

### Post by PaulM1985 on 2010-06-21
I wouldn't go "head first" for graphics and user display.  The things I think you should probably consider/do are:

1) Is Python application exactly what you want to do as part of this very board course that you are about to undertake?  (Not trying to put you off, but there is plenty of scope for all sorts of things)
If so...
2) Decide what you intend to implement. (Just a general idea for the project, look for only a couple of requirements that you would like with a list of 2 or 3 more which you would like to include if you finish early.  Don't aim to finish all of these requirements, just do the main part and then extras if you have time.)
3) Learn Python - Good start :-)
4) Learn a bit about object oriented modelling.  Not just the language of python.  (Ie writing your own classes.  Using conceptual classes to model the real world.  Create software classes based on the conceptual classes.)
5) Look at what you have decided to implement.  Has it been too ambitious?  If so, just rescale the project to something managable.  Reduce some of the requirements of the project.  Also, learning Python would probably look good in your project log.
6) Design your project.
7) Implement the back end.  This bit needs to be good.  No point in a flashy user interface if the back end doesn't work.
8 ) Test the back end.  If you go for some sort of basketball modelling, work out some test cases where player and net are of a certain distance and some cases which you know will work, correct speed and angle, and some which you know will fail and test them.
9) Implement the GUI.
10) Test that works as expected.

This 10-step guide is not by any means ten 12 hour sections for you to spend time on just some sort of guide of what you might expect.  Some of the points are obviously more time consuming than others.

I hope you the best of luck.

Paul

---

### Post by nvteighen on 2010-06-22
IMHO, what someone does in a certain timeframe depends on the task, the tools but also the person and the approach he takes to solve the problem.

---

### Post by DanielWaterworth on 2010-06-22
I'd suggest writing a chain reaction program. i.e you set up a scene with different objects that all do something when activated (like activating other objects). This is a good project because you can make it as simple or complicated as you want and the idea of creating rube goldberg machines on your computer is quite appealing (to me at least [=).

---

### Post by towb on 2010-06-22
Two pieces of advice. Don't use huge libraries, like any of the GUI toolkits, as learning (to debug) those eats time like it was nothing. And do solve a problem you care about rather than some abstract task.

---

### Post by sf-it-services on 2010-06-22
I studied a Physics engine (ODE) for my degree,  all I will say is find a task that simple that you can expand on once you reach your goal.  Make the title impressive and then exceed your project brief. 
Think of an initial idea, place your brief ending at the minimum and work for the maximum

I hope that makes sense, 

ODE has python wrappers I do believe.

---

### Post by rrashkin on 2010-06-22
Perhaps a Linear Regression (Least Squares Fit) or even Polynomial Fit.

---

### Post by RobinBrown on 2010-06-22
Thank you very much for all your suggestions! I was totally clueless as to how high or low I should aim; now not so! I am thinking along the lines of making a simple 2D physical modelling system (to start with), and develop it into some sort of interactive game. This would sit nicely alongside A2 physics and maths. Does this sound feasible? And can you recommend the most sensible GUI package to learn?

Robin

---

### Post by PaulM1985 on 2010-06-22
I'd probably start with something command line based in the project brief and add a user interface afterwards if you have the time.

Paul

---

### Post by RobinBrown on 2010-06-22
That is what I intended, Paul - sorry I didn't make that clear :)

---

### Post by Admiral Yi on 2010-06-22
Take a look at Quickly. Its a Cantonical program that uses glade and PyGTK to build interfaces. The best bit is that it does all the basic code to get all the UI goign so you can focus on the real programming.

Also take a look at the Clutter libraries for animating. With Clutter and some decent python skills you should be able to create a physics simulator easily. Clutter isn't too difficult to learn, and there are some decent tutorials.

---

### Post by DanielWaterworth on 2010-06-23
Pygame! It's great for interactive applications and very easy to learn.

---

### Post by rrashkin on 2010-06-23
I like Tkinter on the PC (but I was already familiar with Tcl/Tk).  On my Linux PC I use GTK because it works well with Gnome.

---

### Post by Asday on 2010-06-23
Seconding PyGTK.

---


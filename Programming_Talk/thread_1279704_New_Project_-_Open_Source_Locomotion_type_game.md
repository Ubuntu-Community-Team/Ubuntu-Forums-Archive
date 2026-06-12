---
title: "New Project - Open Source Locomotion type game"
date: 2009-10-01
forum: Programming Talk
---

### Post by Tony Flury on 2009-10-01
I have an idea in my head about a new Open source project, and I would like to poll for people to be involved in the project in a number of different roles - see poll above.

The project is essentially a Transport simulator (a bit like Locomotion that was released on the PC a while back) with the following key features.

1 Realistic route finding, especially through junctions.
2 Signals per train based on pre-planned route (rather than a simplic signal per line regardless of route).
3 Different types of passengers, based on the locality of the stations/airports etc.
4 Multi trip passengers (so it makes sense to have a station next to an airport, as the feed off each other).
5 Ability to manage a schematic view of your transport routes.
6 Routes are managed idependently of the vehicles, so it is easier to add (or remove/upgrade vehicles).
7 Lots of industry, building types which attract (or maybe detract their own type of cargo/passengers).
8 Transport routes will expand the attraction of particular types of buildings - so for instance a cinema in one town will attract customers from another town (if a passenger transport exists).
9 Realistic travel times, and the ability to set (and be measured on) timetables, or run a free form (it leaves when it is full type service).
10 Ability to reserve land for future routes (at a smaller cost).
11 Ability to construct simple transfer points from vehicle types (so a raihead is not needed at every farm).
12 Map/Scenario editors
13 Goal based winning conditions (or free form sandbox play)

Would be nice to have : 
1 Completely customisable graphic models for buildings, vehicles etc.
2 full 3d implementation.
3 Camera view to track (or even ride on) individual vehicles.
4 realistic business model, reasonable negotiations with local councils (rather than just planting trees), advertising campaigns etc.
5 Multiplayer options

---

### Post by j7%&lt;RmUg on 2009-10-01
I like the idea, but i wouldnt mind seeing some evidence that you can write code, or what kind of experience you have with developing software, also i have a few other questions:

Are you using launchpad or some other code host?

Is it going to be developed to run natively on ubuntu? (If its for mac or windows then that rules me out.)

The reason that i am a little cautious about these things is because i dont just want to do all the work, i want to work with others and have some fun.

---

### Post by Tony Flury on 2009-10-01
nisshh,

You certainly would not be the only be writing the code - and to be honest, if I only get two takers on doing the development then I will shelve the idea. There are an awful lot of individual tasks here (I think that the route finding and signal management is probably the most complex one in terms of the algorithms required), but some of the others are not easy either.

As for me : 
I have 20 years of experience in various fields of writing in house software for one of Europes biggest Telecoms companies, although more recently i have been in a project management role, i keep my hand in on hobby projects at home - most recent significant one being a flickr application in Python/pyGtk, and that was only a few 1000 lines.
My main expertise (if I have one) on the project would be in the data processing sides (graphics is not my strong point). I would also plan to write up the specs for many of the libraries, to allow people just to develop bits (depending on their expertise).

Platform :
I would hope it would be developed using standard interfaces etc so it would be as cross platform as we could make it.

Hosting : 
If the project gets off the ground, then I would be open to suggestions on either launchpad or another project hosting systems - I have no experience on any of them.

---

### Post by j7%&lt;RmUg on 2009-10-01
Ok, well i trust that you are more experienced than me, i can offer mostly python and C++, i use launchpad for two projects and am involved in several others.

I highly recommend launchpad, its very good and is constantly improved.

I have next to no graphics programming knowledge, just a bit of OpenGL, SDL and GLUT. However i have used blender a little and also use GIMP regularly so could help with making models and textures, that sort of thing.

I have around 6 months experience with PyGTK and some experience creating basic deb packages.

Im going to keep an eye on this thread to see if anyone else is interested.

---

### Post by Tony Flury on 2009-10-01
Just realised i just missed off a fairly important feature - which probably should be top of the list : 

0 A decent Computer AI. For anyone who has played locomotion the AI for laying roads and rail tracks was rubbish - lines snaking all over the scenery with loads of curves (and therefore low travel times), where straight lines would work just as well (and be quicker). The Locomotion AI rarely used the shortest route, and often used innapropriate vehicles (trucks not trains for instance), and rarely used the lanscaping tools to find an easier route.

Another nice to have : 
6 Decent route laying tool set - to find the most efficient (in terms of cost/speed of travel etc, route, using existing track roads or air/water routes if neccessary, depending on the type of cargo to be carried, and taking into account landscaping possibilities.

---

### Post by hessiess on 2009-10-01
Good luck implementing that lot in any reasonable time frame;)

---

### Post by Tony Flury on 2009-10-02
The point of course is that a single person could not do it. With the right design and coding framework a decent sized team could do this - depends what you define as a reasonable time frame I guess.

---

### Post by Tony Flury on 2009-10-02
What might be interesting is to throw a few ideas into the hat for a "working title" for this project - for instance :  

PTA : Planes, trains and Automobiles

World in Motion

SimTransport

any other suggestions ?

---


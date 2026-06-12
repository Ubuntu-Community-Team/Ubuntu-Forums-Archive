---
title: "Reducing OSC (UDP) latency on localhost"
date: 2011-05-14
forum: Programming Talk
---

### Post by skullmunky on 2011-05-14
I'm using Open Sound Control to glue a couple of programs together, a common enough task, and running into a surprising amount of latency.  Both programs run on the same machine, so there's no actual network involved  - OSC is just there to get them to talk to each other.  Specifically, program A is a small Kinect app in C++ that gets the user's skeleton data from OpenNI/NITE and sends out the joint positions and orientations using LibLo.  Program B is a Python/Panda3D game that reads the data using pyliblo and uses it for the game interface.  

The lag problem manifests as a delay in the stream of data; motions that the tracker recognizes don't appear in the game engine for several seconds, and the lag increases the longer the apps are running.  

I've run into the same problem with OSC in other circumstances before, such as trying to use a Wiimote to control things in Blender.  I know OSC gets used for things all the time with much higher throughput in live performance scenarios, so there must be something we're not doing quite right in the way we're writing the networking code.  

Or is the overhead of OSC actually an issue?  Am I better off with another approach, like shared memory or something for an application like this?

---

### Post by serge11 on 2011-05-21
Hi,

I'm working on a game with Blender.

My project [http://wiki.labomedia.org/index.php/Kinect_dans_le_Blender_Game_Engine](http://wiki.labomedia.org/index.php/Kinect_dans_le_Blender_Game_Engine)

Open Atelier du 19 mai : [http://openatelier.labomedia.org/](http://openatelier.labomedia.org/)

I use Julian Oliver's pyKit to decode , and I receive datas with python socket.

The latency is the chain latency and the higher is the Kinect, as bad as the XBox.

How many is your latency ?

---

### Post by skullmunky on 2011-05-27
salut serge,

the latency for me with kinect+OSC can be around 3-5 seconds.  When I tried Blender + Wii it was also based on Julian Oliver's code, and the latency was similar.  I'm surprised I can't find more discussion of this since OSC is so popular - but I think it has to do with knowing how to tweak the underlying socket code properly.  

we looked at OSCeleton originally but in the end decided to just throw together our own code based on the OpenNI examples.  The OpenNI skeleton tracking code itself seems very fast - better response than on the Xbox, it seems to me - but the OSC thing seems to be a problem.  

your game looks cool!  I'd like to hear more about it and about Labomedia, it looks like you have some great things going on there

---

### Post by serge11 on 2011-06-10
Microsoft typical latency is 130 ms, see [http://www.microsoft.com/downloads/en/details.aspx?FamilyID=c915d916-478e-4667-b458-eaba34c3cedf](http://www.microsoft.com/downloads/en/details.aspx?FamilyID=c915d916-478e-4667-b458-eaba34c3cedf)
I got the same ! see [http://openatelier.labomedia.org/#11](http://openatelier.labomedia.org/#11)

OSC is only a content format used in real time software : [http://en.wikipedia.org/wiki/Open_Sound_Control](http://en.wikipedia.org/wiki/Open_Sound_Control)
check this: [http://opensoundcontrol.org/what-difference-between-osc-and-midi](http://opensoundcontrol.org/what-difference-between-osc-and-midi)

I will try to improve my game with predict gesture and some magic trick !

---


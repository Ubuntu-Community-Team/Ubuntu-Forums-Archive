---
title: "Open Source alternative to Terragen"
date: 2008-07-07
forum: Programming Talk
---

### Post by visualreactor on 2008-07-07
Hello,
I am computer engineering student and as part of our final year we have to do a project in a group. Our group has been discussing various ideas and one of the ideas is an **open source alternative to [Terragen]("http://www.planetside.co.uk/terragen")**. Firstly the main reasons for doing this project and posting about it here are -
[LIST]
[*]As far as my knowledge goes Linux does not have an equivalent to Terragen.
[*]Open Sourcing it will allow for the usual benefits of having good developers improving on it.
[/LIST]

One more important note is that we have **one year to complete ** the project and practically speaking I believe we spend 6 months coding. So what I would like to know is -
[LIST]
[*]How feasible is this project considering we have very little knowledge of graphics programming and a time frame of 1 year ?
[*]Considering we want our app to be cross platform what choices do we have in terms of programming languages ? I know wxwidgets is a good cross platform library/framework but will it help here ? And is Java too slow for something like this ?
[*]Considering the time limit - what sort of a code base or feature set would suffice to allow the project to move forward after the 1 year that we work on it ?
[*]Is this even a good idea ? I mean will this be very difficult - since nobody else seems to be doing it :confused: ...
[/LIST]

I know that for rendering the generated terrain we will have to use POV-Ray or YAFRAY. Any kind of advice or help will be greatly appreciated. :)

---

### Post by sonicb00m on 2008-07-07
Your project is very ambitious. The first thing I would be looking into is the complexity of the terrain generating, since this is the most difficult part. If you are doing your engine from scratch you probably want to be thinking about C++, but obviously don't use any libraries that are not cross platform compatibile. I would start by investigating the mathematics or engines you can use to create the terrain gen first.

For your GUI I would suggest GTK or Java. You can pretty much use any language to interface with GTK and GTK will work on Windows/Mac. I don't think speed is the biggest issue for your interface. I think either or of these two will provide decent cross platform compatibility.

There's no harm (at this stage) in doing a rudimentary command line version of your terrain generator and just building a GUI to interface with it. Might be quicker and easier to manage as a group.

I think 6 months is doable to get something working but if you reach anything as close as Terragen I would be very surprised.

---

### Post by techmarks on 2008-07-07
This sounds like it would be a great project.  
good luck with the project.

---

### Post by Can+~ on 2008-07-07
The idea is not that difficult, a basic version of terragen should consist on (in order of priority of development):

**a.** An interpreter of a [height map]("http://en.wikipedia.org/wiki/Heightmap") image. Basically, it's a 2d image that the color (or grayscale) represent the height of each point. So you end up looping through the image, using a certain algorithm to interpret the color into a number, and use that number with a certain multiplier into height. I guess that there are multiple projects about this.

**b.** Once that is done, you write down an application that lets the user adjust other things like the camera, and edit the heightmap, just like simplified version of gimp.

The workflow would be something like:
[COLOR="SeaGreen"]
User edits height map image in the GUI program[/COLOR] -> [COLOR="DarkRed"]GUI hands the imagemap to interpreter[/COLOR] -> Computes a 3d image into another image (or other format) displayed by the GUI

[http://lab.parkstudio.ru/terra/](http://lab.parkstudio.ru/terra/)

---

### Post by dernob on 2008-07-07
My advice is to do that not in Java or to divide the program in a GUI part (Java, Python or something else) and a calculating part (C/C++); as computer graphic algorithms are one example (there are not that much, at least all the Java people tell you so) which works a lot faster in C/C++. Displaying can be done in with a "real" Engine like Ogre, but terrain visualising is special stuff, which you should consider doing directly. Or ask a university (yours?) to give you material on it, you are not the first ;)

As I'm on the search for a program like yours I would be happy to hear some results, where can I abonnent your mailinglist? 

Recently I found and tried out: [http://www.bottlenose.demon.co.uk/share/fracplanet/index.htm](http://www.bottlenose.demon.co.uk/share/fracplanet/index.htm) 

Greetings

---

### Post by catchmeifyoutry on 2008-07-19
For terrain height map generation you should look into fractal terrains.
I used to play around and creating simple 3D fractal worlds with OpenGL long time ago, and I believe there are a lot more websites and approaches on the web nowadays if you google for it (keywords: "fractal terrain", "brownian motion perlin noise").
This is a simple introduction to the approach I followed (in fact, these are the exact same sites, good to look them up again :D )

[http://www.gameprogrammer.com/fractal.html](http://www.gameprogrammer.com/fractal.html)
[http://www.gamasutra.com/features/20010302/oneil_01.htm](http://www.gamasutra.com/features/20010302/oneil_01.htm)

again, research it, there's a lot more out there now ;)
At the same time, if you need some good and practical OpenGL tutorials:

[http://nehe.gamedev.net/](http://nehe.gamedev.net/)

OpenGL would be useful for simple visualization tools, placing cameras, previewing terrains, but not for the final high quality output. Indeed, use an existing ray tracer package.

In my experience, creating fractal landscapes (for real-time interactive environment purposes at least) is not that hard, although you'll need some tweaking to get realistic results.
Your problem starts when you want to add trees, grass , placing rivers, volumetric clouds, etc... 
Actually, simple cloud textures can actually be modeled with perlin noise maps too:

[http://freespace.virgin.net/hugo.elias/models/m_clouds.htm](http://freespace.virgin.net/hugo.elias/models/m_clouds.htm) 

Have fun and good luck!

---

### Post by Cope57 on 2008-07-19
"[**Terraform**]("http://terraform.sourceforge.net/") is an open source interactive height field generation and manipulation program, giving you the ability to generate random terrain and transform it. Terraform runs under Linux and other UNIX systems under the X11 Windowing system. It uses the GNOME desktop platform and thus has a (more or less) consistent graphical user interface which doesn't require use of the command line.

Terraform allows you to generate random terrain using a number of algorithms and then selectiveley change the terrain using a variety of transformations. Where possible, the transformations provide a real-time preview, giving you instant feedback on the effect of any parameter changes."

I found it on 
[The table of equivalents / replacements / analogs of Windows software in Linux.]("http://www.linuxrsp.ru/win-lin-soft/table-eng.html")

---

### Post by suprfish on 2008-07-19
> **visualreactor said:**
> 
[LIST]
[*]As far as my knowledge goes Linux does not have an equivalent to Terragen.
[/LIST]

Actually there is [VoxelWorld]("http://dmytry.pandromeda.com/voxelworld/"), which is written in Free Pascal, which is a big plus for your cross-platform efforts (if you decide to use it, or something (hint)).

Currently there are only Windows binaries available for download on the site. The developer had plans to release an open source version, but didn't have the time so the current code, while it works, isn't exactly polished. _He's currently looking for a maintainer/director (hint)_. I'd emailed him and he sent me the source archived, which is attached.

Dependencies: freepascal, opengl, glut

Building:
```
fpc -Mobjfpc -O3 vwscript.pas
```
and you'll get the command line binary.

```
fpc -Mobjfpc -O3 vwint_glut.pas
```
for interactive viewer using glut.

You'll notice, it really needs a maintainer (hint :)). I haven't had much time to play with it yet (therefore I can't provide much support), so I included these files that you should read 'readme', 'script' and 'copyright'.

Edit: removed attachment, PM

---

### Post by visualreactor on 2008-07-21
I apologize for the late reply but we are now very certain that we will pursue this project. A big thanks to everybody who has replied!

Regarding the cross platform nature of our terrain generator - which IDE should we use ? Considering that we are pretty confident that we shall use GTK+ for developing the GUI. I've found that Netbeans 6.0 and GTK+ work well together and plus Netbeans also supports C/C++ development. I haven't found anything fruitful regarding Eclipse.

Regarding the actual core - that is the terrain generation we have decided that C/C++ is the choice. However will a complete object oriented C++ core affect performance ? As in will an OO design slow it down in anyway ?

Also back to the cross platform - how will the work flow of development be like ? And about the core also being cross platform - what measures should we take to make it cross platform ? Will using the GCC compiler make sure that the c/c++ code runs on windows and linux without changes ? 

Thanks again for all the responses till now and as usual any further help regarding the above questions will be very helpful :)

---

### Post by Wybiral on 2008-07-21
> **visualreactor said:**
> I know that for rendering the generated terrain we will have to use POV-Ray or YAFRAY. Any kind of advice or help will be greatly appreciated. :)

I wouldn't implement rendering into the software. Are you trying to generate them, or render them? Instead, I would just have them output a blender-compatible model and let the users render in blender, which is much more robust and well-tested than anything you will end up writing. In fact, writing the entire thing as a blender plugin may not be a bad approach!

---

### Post by catchmeifyoutry on 2008-07-21
> **visualreactor said:**
> I apologize for the late reply but we are now very certain that we will pursue this project. A big thanks to everybody who has replied!

Regarding the cross platform nature of our terrain generator - which IDE should we use ? Considering that we are pretty confident that we shall use GTK+ for developing the GUI. I've found that Netbeans 6.0 and GTK+ work well together and plus Netbeans also supports C/C++ development. I haven't found anything fruitful regarding Eclipse.

Regarding the actual core - that is the terrain generation we have decided that C/C++ is the choice. However will a complete object oriented C++ core affect performance ? As in will an OO design slow it down in anyway ?

Also back to the cross platform - how will the work flow of development be like ? And about the core also being cross platform - what measures should we take to make it cross platform ? Will using the GCC compiler make sure that the c/c++ code runs on windows and linux without changes ? 

Thanks again for all the responses till now and as usual any further help regarding the above questions will be very helpful :)

The IDE is more a matter of personal preference, so better not ask which one is "better" because you might start a flamewar here ;).

On the core C++ features, I think you should realize that raytracing the image is going to be the bottleneck in terms of runtime. I like the idea of using blender for raytracing by the way (you might at least use it as a starting point, but it is of course your project).
Blah, what I wanted to say is that I don't think you should worry too much about overhead of using C++ over ANSI C, but choose option that will allow your team to develop fast, clean and readable code, especially since you'll be working together on the same software.
Do you know how to use templates, and especially the STL in C++?
I think you could benefit from object oriented design, if done properly.
But more important for now is the familiarity and understanding of the team with the language.

Look into using Cygwin on windows machine to compile with gcc on windows,
and write small test programs for external libraries (OpenGL, image I/O) to see if everything is setup correctly.

Cheers!

---

### Post by visualreactor on 2008-07-26
Hello,
After finding out more about the work flow of developing a cross platform application we have found that it could take considerable amounts of time. So we discussed about using Java for generating the terrains. Come to think of we will only be generating the terrains - the actual rendering will be done using POV RAY which runs natively on both Linux and Windows. So in reality there won't be much of a performance hit. I know this deviates from our ambitious plans in the beginning but I think this will be best for the project. What do you'll think ? 

Also I know this forum topic has dragged on for a long time now with no apparent end result. We have to submit our project synopsis next week and then we begin designing the architecture and so on. Also we don't know if we are allowed to take any direct help in terms of actually writing code - so we can't open source it during the initial development :( but at the end for sure. So we hope to build a good base.

As usual any kind of help is greatly appreciated :) - I don't think we would have gone forward with this project without all you're responses. :)

---

### Post by Wybiral on 2008-07-26
How much experience do you have manipulating 3d meshes?

---

### Post by catchmeifyoutry on 2008-07-26
> **visualreactor said:**
> Hello,
After finding out more about the work flow of developing a cross platform application we have found that it could take considerable amounts of time. So we discussed about using Java for generating the terrains. Come to think of we will only be generating the terrains - the actual rendering will be done using POV RAY which runs natively on both Linux and Windows. So in reality there won't be much of a performance hit. I know this deviates from our ambitious plans in the beginning but I think this will be best for the project. What do you'll think ? 


Sounds like a good plan.

> **visualreactor said:**
> 
Also I know this forum topic has dragged on for a long time now with no apparent end result. We have to submit our project synopsis next week and then we begin designing the architecture and so on. Also we don't know if we are allowed to take any direct help in terms of actually writing code - so we can't open source it during the initial development :( but at the end for sure. So we hope to build a good base.


Yes, you should write the program during the course yourself, it's your assignment and your grade ;).
But it will be very nice if the project can live on as Open Source after you finished the course. Many OSS projects start like this.
However, exchanging experience with others and investigating/discussing approaches are part of scientific research, so it should be no problem for you to post on your progress.

> **visualreactor said:**
> 
As usual any kind of help is greatly appreciated :) - I don't think we would have gone forward with this project without all you're responses. :)


cheers

---

### Post by andrewbaldwin on 2009-03-23
Hi,

Has anyone installed and run terraform on 8.10 ?

I seem to be caught in a dependency trap with it - both for the .deb  and when building from source  --  any advice on where to look for the packages it wants [and whether they'll cause problems if loaded] would be appreciated.

I did have it running nicely under Gentoo -- it's a good package 

Thanks

---

### Post by shatterblast on 2009-03-24
> **andrewbaldwin said:**
> Hi,

Has anyone installed and run terraform on 8.10 ?

I seem to be caught in a dependency trap with it - both for the .deb  and when building from source  --  any advice on where to look for the packages it wants [and whether they'll cause problems if loaded] would be appreciated.

I did have it running nicely under Gentoo -- it's a good package 

Thanks

In 8.10 Intrepid, you could go to System -> Administration -> Software Sources -> Third-Party Sources tab -> Add button -> then put:

deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy multiverse universe main restricted

You can search for Terraform, but you will need to force some of the software requisites individually since they exist as older versions of newer libraries.  I am unsure if Terraform will stay compatible with newer libraries.  Thus, the software may possibly not require the installs of the older libraries even if Synaptic claims such.

I got it to install from Sourceforge like 3 months ago, but it took me 2 weeks to figure out that I could just install a couple of dependencies and place a couple of compiled others into the Terraform folder.  I have since uninstalled it and the dependencies.

Modern alternatives derive from the 2.48a version of Blender in the scripts.  I can think of at least one open source graphics API that will do automatic terrain generation with a test case for nice-looking water.  It's Java-based how ever.  As far as Blender scripts, I don't believe I've seen water rendered well yet, but I like surprises.

---

### Post by andrewbaldwin on 2009-03-24
Thanks shatterblast :-)

-- I'll give it a try with the repository you suggest

---

### Post by Cerox Rex on 2010-05-03
Rebumbing this thread.

I'v been trying to get the fracplanet x64.deb package to install under lucid, but it complains that the libbost dependency is missing.

I'v installed libboost trough apt-get. Its installed to "/usr/include/boost" directory. its latest version 1.40 or somthing.

Still i get a dependency problem! Any way around this?

---

### Post by texaswriter on 2010-07-12
In case anybody cared still: 

[http://www.codeweavers.com/compatibility/browse/name/?app_id=7704;tips=1](http://www.codeweavers.com/compatibility/browse/name/?app_id=7704;tips=1)

I got the program working on Linux through Codeweaver's product: Crossover Games. The link above has the necessary prerequisites to get it working.

---


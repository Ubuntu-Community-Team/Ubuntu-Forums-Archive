---
title: "New 3D engine designed for game making under C/C++ using OpenGL/SDL in progress!"
date: 2007-01-13
forum: Programming Talk
---

### Post by DARKGuy on 2007-01-13
Greetings! ^_^

I'm new to the community and all, at least on the forums though, 'cause I've been in the IRC channel around every now and then :). 

Yeah, this is going to be my first post about the 3D engine I've been working on December 2006 and I could finally release a website and a pre-alpha version for you all to test and use. I got suggested by someone on the IRC channel to try to post here to see if I could catch some people to help with the project so here I am :P

I'm not sure about the "spam" policy but this isn't just advertising :/ I'd actually like to find people who might be interested in helping this project grow bigger and better, since the goal is to make a full OpenGL+SDL easy wrapper for complete newbies who want to get into game making under Linux (which I think is the weakest point in Linux...) as making games is a pain in the you-know-what unless you know C++/OpenGL/SDL/binary/trigonometry/etc back and forward and spend more time trying to make things work rather than focusing on the game's real development and not the engine.

The project url, if you want to check is this one: [http://gp3d.sourceforge.net](http://gp3d.sourceforge.net)

Thanks for reading ^_^;;

- DARKGuy

---

### Post by Wybiral on 2007-01-13
Sounds interesting...
So, this is a game engine?
You should probably put some more "gamey" screenshots up on the site.
I'm going to check it out here in a little (working on something else at the moment) but it sounds pretty cool.

---

### Post by slavik on 2007-01-13
I could probably help you out ...

---

### Post by Wybiral on 2007-01-13
Same here, I have some experience with 3d stuff, particle systems, terrains, model animation, calculating normals, and some special effects such as motion and radial blur.

The layout is pretty good (the code in your engine) but it would be a lot better if there were more tools geared towards game design (as opposed to just rendering/lighting tools).

---

### Post by Canute on 2007-01-13
This actually looks pretty sweet. All though I do not by any means have the skill to help with development, I am sure going to take a look now and then :)

---

### Post by DARKGuy on 2007-01-13
^^ thanks for the answers :)

Yeah, hardly there's any easy free 3D modeler out there for Linux (well, Blender, but it's a pain to learn it =/, just as much as any other programming language >.<) but a 3D modeler is a big, big project, bigger than this one, but who knows, maybe in the future.... ;)

As of GP3D, the screenshots show what I've done by myself following some tutorials and reading OpenGL help around in the internet. Since I haven't found ways to do stuff like model loading, camera with quarternions and such, I made the website and the pre-alpha version to see if I can get some help with that, and at the same time make it grow :), but for more "gamey" screenshots, the engine needs to be improved, and with my current knowledge I can't as much as I've done already xD.

Now for discussing the GP3D dev and such there's a forum for it too, I might post later a nice camera code I found on the net that I tried to adapt to GP3D and failed, maybe some of you could figure out what's wrong o.o but anyways, if any of you want to help just register on the forum and post, I check 'em regularly so answers shouldn't take too long ^^;;

---

### Post by Wybiral on 2007-01-13
Blenders not that hard... Anyway, I just registered on your forums (waiting for a response).

---

### Post by DARKGuy on 2007-01-13
Well, the interface is kinda orthodox :/ I'm more used to 3DSMax, Maya, Wings3D (which works on Linux!) and MS3D :P

Yay! welcome :) tell me i the email arrives, if it doesn't then I shall deactivate the email activation for phpBB, since I'm still not sure if sourceforge.net accepts phpBB sending email verifications ^^;;;

---

### Post by Wybiral on 2007-01-13
It's been a while and no Email, so unless it takes a long time to send it, then you might want to deactivate it.

I sent you a PM btw.

---

### Post by DARKGuy on 2007-01-13
Yeah, I went to WoW for a bit while I waited and no email arrived as of yet so I'm gonna reconfigure the forum, shouldn't take too much time and I'll post again just so you know.

*reads teh Inbox :D*

---

### Post by slavik on 2007-01-13
I wrote a C++ function to read in model information from a wavefront object. I will make it cleaner/better and make it into a real library (right now, it is a function written inside of a header which is not very 'clean'). Another thing that I have is some camera classes for easier manipulation of objects and such. I intend on cleaning those up and make them more optimised and packaged better.

There is also a collision detection library that I am fond of (coldet) which I haven't used, but it is simple, and fast. Maybe a re-code of it and such.

---

### Post by DARKGuy on 2007-01-13
Whoah, this forum is full with skilled people o_o;! the wavefront object function, the camera and the collision library shall prove really useful for future releases! :D please share them if you wish in the GP3D dev forum for (hopefully) implementing it in the 0.0.2 or 0.0.3 release after a big testing phase ^_^; I need to get SVN working too, but I've got to document myself about it since it's my first time too xD.

Also, you all can register in the forum now, I'm working on it at the moment but registration works without email activation, however you can post and all. Don't be afraid if new subforums start appearing as I had to redo the forum, but this is the first and last time it happens :).

---

### Post by Zdravko on 2007-01-14
[DARKGuy]("http://ubuntuforums.org/member.php?u=222466"), I just registered in your forum. There were no problems at all. I am proud of the fact, that I am the 2nd registered user there!. I wish you success with the project!


BTW, what are the required libs for Linux? I dunno whether I have these SDL installed :(

---

### Post by slavik on 2007-01-14
I am flying off to Israel for 10 days, so I won't be able to start contributing until 26th at the earliest.

---

### Post by DARKGuy on 2007-01-14
ZDravko: Well now that I'm in Linux I checked the libraries I have installed. The requeriments then should be:

libsdl1.2-dev
libsdl1.2debian
libsdl1.2debian-alsa (but I don't know if it really uses this one)
libsdl-image1.2
libsdl-image1.2-dev

And in the future, these two shall be used too:

libsdl-mixer1.2
libsdl-mixer1.2-dev

Slavik: That's okay, don't worry, have a good trip! :D

---

### Post by Zdravko on 2007-01-15
[DARKGuy]("http://ubuntuforums.org/member.php?u=222466"), thanks I managed it. I see that your library is still under development. Maybe it is too early to be used in a serious project.

---

### Post by DARKGuy on 2007-01-15
For now, yes, I admit it isn't even ready for a serious project. *however* Wybiral has been contributing a lot into creating a model loader (an awesome one by the way, with animation and all!) and we're thinking up stuff to see how can we load some basic level formats or make our own one (though, BSP looks good for a start I guess o.o; ). I've added a simple camera class I found on the net and fixed some minor issues... who knows. At this rate, maybe it'll be ready for small projects in 0.0.5 or 0.1.0 ^^;

Edit: Fixed a typo xD

---

### Post by Zdravko on 2007-01-15
[DARKGuy]("http://ubuntuforums.org/member.php?u=222466"), what do you mean under "loading a model"? What is a "model"?

---

### Post by DARKGuy on 2007-01-15
3D models, like MD2, 3DS, OBJ, X, MS3D... 3D model formats like that :P

---

### Post by Wybiral on 2007-01-15
Well, we've already got an MD2 loader (with animation & texture mapping) and a nice model class to load and render them (very easy to use too). MD2's are the models quake 2 uses, they store animation, texture's, texture mapping, and of course the mesh data (the 3d locations of the vertices's)

A model is a 3d object translated into data. Have you ever wondered how 3d video games are able to store the 3d shape of people/objects/monsters? Well, they use "models" for that.

I suggest playing around with blender. You can find it in synaptic, or check out [http://blender3d.org/cms/Home.2.0.html](http://blender3d.org/cms/Home.2.0.html)

BTW darkguy, I think you made a small typo in the post above...

> ...see how can we load some basic model formats or make our own one...

I just wanted to make it clear that model loading IS done, he meant to say level formats.

---

### Post by DARKGuy on 2007-01-15
> **Wybiral said:**
> BTW darkguy, I think you made a small typo in the post above...
I just wanted to make it clear that model loading IS done, he meant to say level formats.

Right xD I was a bit sleepy x)... thanks for noticing :P

Today I finished adding the camera class, added some more functions to the main header file and fixed minor issues. Hopefully 0.0.2 should be ready for this week or next one if one of us gets short on time somehow ^_^;

---

### Post by Zdravko on 2007-01-16
> **DARKGuy said:**
> 3D models, like MD2, 3DS, OBJ, X, MS3D... 3D model formats like that :P

I've never heard of these ](*,)

Yes, I've always wondered how do games like Heroes or SimCity work... It seems that art designers made the different animations, buildings and units. Then these models are exported to binary data (I guess they are stored into a file). Then programmers write software to load such files and render the model on the screen. Am I right?

---

### Post by Wybiral on 2007-01-16
> **Zdravko said:**
> I've never heard of these ](*,)

Yes, I've always wondered how do games like Heroes or SimCity work... It seems that art designers made the different animations, buildings and units. Then these models are exported to binary data (I guess they are stored into a file). Then programmers write software to load such files and render the model on the screen. Am I right?

Yes, basically. The "binary data" is really just a means of storing the vertices's of the model. A vertex (singular for vertices's) is usually just a point in 3d space, so it's a chunk of data with an x,y,z value which represents a point in 3d space.

Essentially, if you are interested, the basic structure of a "mesh" or model consists of two parts. Vertices's and faces. You now know that vertices's are 3d points representing points on the model. Faces represent the connection between the vertices's (kind of like one of those connect the dot pictures from when you were little). Faces (or polygons) are usually triangles, so the face is just three index's to the vertices's that make up the points on the triangle.

Put all of that together and you've got yourself a 3d model!

Animation works from either armature systems, where there is a sortof virtual bone structure that can be rotated to change the shape of the model, or they are done using keyframes. Keyframe animation is the easiest because it just stores the model in various poses, and then animates between them through interpolation.

---

### Post by hod139 on 2007-01-16
You guys might want to check out G3D ([http://g3d-cpp.sourceforge.net/](http://g3d-cpp.sourceforge.net/)) or ODE ([http://ode.org/)](http://ode.org/)).  Instead of starting from scratch you could contribute to these projects.  

If you don't care about existing projects and just want to try writing one yourselves for fun, then I wish you the best of luck.

---

### Post by Wybiral on 2007-01-16
Wheres the fun in that hod139?

One of the main reasons I'm interested in pitching in on a project like this is for the learning experience... You never get anywhere if you let someone else's game engine pull you around. It's much funner and more educational to try it yourself. And so far, it's going along nicely, and I've already learned quite a bit (mostly MD2 model format and BSP level format)

Besides, I think having a selection is a good thing... What if there were no linux and someone started writing it... And then someone else came along and said "Hey, what are you doing? Why don't you just work on windows..."

---

### Post by DARKGuy on 2007-01-16
> **hod139 said:**
> You guys might want to check out G3D ([http://g3d-cpp.sourceforge.net/](http://g3d-cpp.sourceforge.net/)) or ODE ([http://ode.org/)](http://ode.org/)).  Instead of starting from scratch you could contribute to these projects.  

If you don't care about existing projects and just want to try writing one yourselves for fun, then I wish you the best of luck.

Well, thanks :)

Hm, starting to program with another project is kinda hard. Wybiral got lucky since the project just started and the source code is not too much and is easy to read. When I look at other projects source code and see it's like, 3513251256125 .h/cpp files just for doing what we're doing here..... man, I think about it twice. The idea is to keep GP3D simple **both** in internal source code and easy to use and read for the programmer.

I'm not saying those engines or other 3D engines have messy source code. I've seen ones with easy-to-understand code and such, but once a project starts having its own shape, the source code does too, and it takes some time in getting the project's/source's shape right. 

Also, with the creation of this project we're all learning. For example, I've learned about raw OpenGL, SDL, porting the code to other platforms, geometry of 3D images, somewhat about vectors thanks to Wybiral's articles... and he's learning too (stuff like MD2, MDL, BSP...) so it's a knowledge rush between every member of the project.

Of course, if we use that analogy, then I could've just not started this and keep programming in Windows :P

---

### Post by DrMega on 2007-01-21
I work as a C# programmer in Windows, and am relatively new to Linux. I did some C/C++ a long time ago, and none of it was to do with 3D stuff, but it is something I am interested in.

I'm in no position to contribute yet (lack of 3d/Game programming) skill, but I wish you the best of luck getting this off the ground, and if I can help in the future, I certainly will.

---

### Post by DARKGuy on 2007-01-21
> **DrMega said:**
> I work as a C# programmer in Windows, and am relatively new to Linux. I did some C/C++ a long time ago, and none of it was to do with 3D stuff, but it is something I am interested in.

I'm in no position to contribute yet (lack of 3d/Game programming) skill, but I wish you the best of luck getting this off the ground, and if I can help in the future, I certainly will.

Ah, the joys of C#... :P I program in it too for some projects I have to do, it's not much different than C++ once you see the similarities between the two (kinda, at least syntax-wise) and the idea of GP3D is to initiate people in C/C++ while creating their own games. That's why we want to keep GP3D's syntax easy to read and understand the flow of it :)

Thanks hehe ^_^ hope to see you around in the GP3D forum too! :D

---

### Post by DrMega on 2007-01-22
I looked at your sample code, and I don't know if it will be a problem or not but I noticed that you define the colour depth to be 16bit. The propriety ATI drivers for Linux do not support 16bit natively, only 24bit (maybe OpenGL takes care of the translation, in which case probably no issue other possibly performance).

I reckon it would be dead easy to just change it to 24bit depth, but obviously people will generally pilfer working examples, and if it is an issue for ATI cards then it would be quite a show stopper.

EDIT: See [http://ati.de/products/catalyst/linux.html]("http://ati.de/products/catalyst/linux.html")

---

### Post by DARKGuy on 2007-01-22
> **DrMega said:**
> I looked at your sample code, and I don't know if it will be a problem or not but I noticed that you define the colour depth to be 16bit. The propriety ATI drivers for Linux do not support 16bit natively, only 24bit (maybe OpenGL takes care of the translation, in which case probably no issue other possibly performance).

I reckon it would be dead easy to just change it to 24bit depth, but obviously people will generally pilfer working examples, and if it is an issue for ATI cards then it would be quite a show stopper.

EDIT: See [http://ati.de/products/catalyst/linux.html]("http://ati.de/products/catalyst/linux.html")

Hm, that's interesting :shock: since all I have to test is my GeForce4 Ti 4200 and no ATI around to test with, I thought it was the same in ATI and just different GPU API. That's weird it doesn't support 16-bit, who the heck made those... ](*,) but eh, I'll take it into account, thanks for the heads up :)

---

### Post by DrMega on 2007-01-22
I've just downloaded the library, and tried to compile the Linux example. I'm afraid it fell over at the first hurdle because Windows.h doesn't exist. Is there a file missing from the download?

---

### Post by tpg on 2007-01-22
> **DrMega said:**
> I've just downloaded the library, and tried to compile the Linux example. I'm afraid it fell over at the first hurdle because Windows.h doesn't exist. Is there a file missing from the download?
Try just commenting out (or deleting) that line, then it should compile.:)

---

### Post by DrMega on 2007-01-23
> **tpg said:**
> Try just commenting out (or deleting) that line, then it should compile.:)

Did that last night, sorry I forgot to post up an update. Commenting out the include for windows.h solved the problem. Then it compiled nicely.

As for my other concern that I mentioned about ATI drivers not supporting 16bit colour (only 24bit), it looks like it will still work (need to try it on my other machine to be sure), but will just render everything in software. If that's the case then performance is the only potential issue in that respect.

All in all, its looking very promising.

---

### Post by studiesrule on 2007-01-23
Wow, this is an amazing project. In fact, just 3 days ago, I wanted to start learning about 3D engines, and making 3D visualization of data ('course this is a 3D engine, but I'm sure a lot of this stuff would be useful elsewhere). I was wondering if I could latch on to this project, and learn a lot (and help a bit).

The thing is I'm scared by the complexity of the matter. I know Wyr is a code guru , and I assume most of you are too. So, as an amateur, would I be able to understand whats going on before the project becomes too huge for my  limited skills. So, could you just give me a few pointers of what to watch out for and all?

---

### Post by DARKGuy on 2007-01-23
> **studiesrule said:**
> The thing is I'm scared by the complexity of the matter. I know Wyr is a code guru , and I assume most of you are too. So, as an amateur, would I be able to understand whats going on before the project becomes too huge for my  limited skills. So, could you just give me a few pointers of what to watch out for and all?

Well, Wybiral really is a guru :P he knows lots of 3D projection and math (in fact he made the MD2/BSP/OBJ loaders and most of the math functions, tpg has helped a lot too with his math functions and maybe not all of the collaborations to the project have been used yet, but they've been took in account and used as reference or even bits of 'em to improve the engine. There may be stuff that we might not add because of other reasons, though we don't want you to feel rejected if somehow we don't add something you contributed ^^;; my idea is, that if someone contributes with something and we don't add it to an official release, the code would remain as a "patch" for the engine itself, in case you still want to use that functionality :).

Anyways, I'd suggest to start learning how SDL and OpenGL work together. I've seen SDL+OpenGL tutorials on the net and NeHe's tutorials (the SDL+OpenGL converted versions of his tutorials) are a **good** way to learn: [http://nehe.gamedev.net](http://nehe.gamedev.net) :). 

Other than that, just basic C++ knowledge could help you to get into the project. Hell, anything that can help the engine make better games is helpful! file functions, sound functions, scripts... anything xD. We also have a forum on the site to discuss GP3D's development. There are few registered users :( but hopefully it'll increase with time! :D

And also, thanks for being interested in the project :biggrin:

---

### Post by DrMega on 2007-01-23
I've been having a bit of a dabble with the example, which gives a good starting point. The thing is, does anyone know how to get it to build in the Anjuta IDE rather from the compile script? Over the years I've grown lazy and like code completion and other nice features of an IDE.

Also, if like me you are a bit rusty with C++ or just a bit unfamiliar with the libraries you're using then code completion etc saves having to look stuff up manually all the time.

Or can anyone recommend a better IDE?

I am really interested in the GP3D project and it has motivated me to do something I've been promising myself for a while now, which is to brush up on my C++ skills, and have a good crack at games development. Also, when I'm a bit more confident I'd really like to contribute to GP3D.

---

### Post by DrMega on 2007-01-23
Ok, I found the answer re getting the example to compile in Anjuta. Also, I've tried to set everything up so my life is nice and easy when I want to work with gp3d. Here's what I've done:

-Initial Setup-
1. I create a new directory at /usr/include/gp3d
2. In there I put the GP3D source files (excluding the examples etc, ie just the headers)

-Modified the example-
3. Commented out the include for windows.h
4. Created a new Anjuta terminal project, and overwrote the generated code with the GP3D example.
5. Changed the relative path includes to the gp3d stuff from the format #INCLUDE "gp3dstuff.h" to the format #INCLUDE <gp3d/gp3dstuff.h> and put the image files in the project folder

-Persuaded Anjuta to compile everything, bringing in the SDL stuff and everything-
6. In Anjuta, go to Settings->Compiler and Linker settings. This brings up a dialog.
7. Go to the libraries tab, and type SDL in the text box and click Add.
8. Repeat step 7, but for SDL_image, GL and GLU
9. Do a Rebuild All (shift+F11) then execute (F3)
10. Job done, chill for a minute.

I'm sure for many people that are following this thread this is all basic stuff, but maybe there's someone who like me is a bit rusty and fairly new to Linux etc and just wants an easy life8-)

---

### Post by studiesrule on 2007-01-24
@DrMega: You should try CodeBlocks. Their IDE is pretty nice, and is quite feature rich (while still being very easy to use).

---

### Post by DARKGuy on 2007-01-24
Hey DrMega! that's a nice small HowTo you wrote there!, hehe ^^... actually, I use Kate XD, ish simple and nice :P but I'll check Anjuta (or CodeBlocks) now and follow your instructions, and hopefully include it in the documentation if you allow! ^^...

Wybiral got busy for the moment so he can't keep working on the engine for the next few days, so no MD2/BSP/OBJ until he really completes those loaders, but that means I'll release a next version soon without those model loaders, but the code change and the new improvements shall be noticed. Hopefully that'll be the final "look" of the engine's syntax (faster to type too, and namespaced!). Maybe skipping some numbers too, since the development greatly increased with his help. 

Also, I'll try set SVN up this week so you all can get the latest development version and help with it! ^^.

---

### Post by DrMega on 2007-01-24
> **DARKGuy said:**
> Hey DrMega! that's a nice small HowTo you wrote there!, hehe ^^... actually, I use Kate XD, ish simple and nice :P but I'll check Anjuta (or CodeBlocks) now and follow your instructions, and hopefully include it in the documentation if you allow! ^^...

It goes without saying that you can use my "HowTo". Many people on the forums have helped me out over the past few weeks so if I can help someone else in some way then that's only fair.

---

### Post by DARKGuy on 2007-02-20
Guess what...

[SIZE="4"]**GP3D 0.0.3 is released!!!**[/SIZE]

And MD2 is working nice and dandy thanks to Wybiral (and Psionic for the free 3D models):

[img]http://img380.imageshack.us/img380/6231/screen4yr6.jpg[/img]

[img]http://img503.imageshack.us/img503/9362/screenshot2007021923093lv9.jpg[/img]

I can't upload the website right now because SF.net's web updating services are down right now (I guess?) so I'll try to upload the website tomorrow or around this week, but for now you all can grab the files here: [https://sourceforge.net/project/showfiles.php?group_id=186694](https://sourceforge.net/project/showfiles.php?group_id=186694) (you can also get the SVN version too!).

YAY I'm so happy xD

---

### Post by Zdravko on 2007-02-20
Cool - I am excited!

---

### Post by Wybiral on 2007-02-20
Looks pretty cool. I'll try to make some time to optimize the loader/renderer, I shouldn't have used STL vectors... But hey, it's safe (no chance in memory leaks) and it works!

(The lights on that spaceship texture look very good, that should be a cool model to show off the engine)

---

### Post by DARKGuy on 2007-02-24
Well, I was able to update the website now, enjoy! :D

I've been having heavy days at work and such u_u;; ... this week's been hard and I expect the next one to be harder :/ so yeah, I don't think I'll be able to do any coding in GP3D until tomorrow if I get some free time and some nights after I come back home from work.... however, if I get my own computer at work, I might be able to install Linux in it (with dual-boot with Windows 'cause they use it there >.<) and program some GP3D in my free time :P

Yay ^^

---

### Post by Zdravko on 2007-03-13
How is the project going?

---

### Post by DARKGuy on 2007-03-28
It's back - back and rocking!

I made some new posts in the GP3D forums, gotta need more people browsing them... =/ I know I don't update the site very much (that's 'cause I was lazy and didn't bother to make a MySQL database for the news and making the site more dynamic) but the forum gets some people once in a while.

Someone else emailed me and sent me some kind of .X loader - too bad the code is for Windows (OpenGL initialization and such) so I'll try to adapt it to Linux and try it, else, the code will still be there (maybe in SVN) so there can be a .X loader based off it (hopefully... I'm anxious for using my .X models in it! :D).

I'm talking gibberish here anyways, I need to email the guy first to see if all this is possible and retake the project again.

Since I got my new job everything's been kinda hard, school+work+gym+weekends = no free time, but I'm doing everything possible to at least check up the code and add a thing or two between weeks, so there's some progress. I'm a bit more stable now, so I can make up some time for GP3D at nights or some mornings.

Anyhow, enough talk! check the forums and contribute! I'm working on converting the .X loader to Linux and trying to add "2D sprites" for at least showing a small logo and some 2D art in future example programs :)

---

### Post by blanky on 2007-03-28
Ey DARKguy! Te acuerdas de mi? Creo que estavamos en ##csharp un tiempo, yo soy el que hise 'musicaster'.

It's a small world man! Great job, this looks very interesting! :)

---

### Post by Dread Knight on 2007-06-16
This project looks interesting! You should update the link in the first post :P

Any news?

---

### Post by Tr0janV0dka on 2007-06-16
Man... I wanna make my own engine!

/starts reading about python

/starts reading about opengl

---

### Post by hockey97 on 2007-06-16
HI How do you make the game engine?? lol  is open gl or direct x a game engine or a 3d engine??

are game engine's  nothing but classes of functions??

Does it have to noch physic's.

How did you make it multi-platform engine??

How hard was it to make this game engine???

---

### Post by Mickeysofine1972 on 2007-06-16
Hey guys 

i just stumbled upon this thread and thought I would just tell you guys tht you are doing a great job!

It great to see really open teams working together as they should, and I am not at all suprised to see wybiral in the mix! lol dude you are a 3d guru and I salute you!

DarkGuy, dot let the other guys get you down, those who seem to think its ok to drop links to other projects that have already been done into the thread so you will appear not to be original. Those guys also said that the ubuntu games development wiki ([http://ubuntu-gamedev.wikispaces.com](http://ubuntu-gamedev.wikispaces.com)) was a waist of time. 

They never seem to offer any code or help though? strange that? maybe they are still too busy to contribute? maybe they just have no girlfriend? who knows? but the fact remains that anyone who says its a waist of time really has nothing to say other than that. Or else they would be giving answers and help like the rest of us.

Whilst i dont know if i can help on this 3d project of yours I am certainly gonna try with you 2d project and maybe get a great new game on the go!

Mike

---

### Post by maddog39 on 2007-06-16
Hmm... apparently the project doesnt exist anymore according to source forge. What happened?

---

### Post by ankursethi on 2007-06-17
See the "Gaming and Leisure" section and look for the topic "Making a GunBoud-like Game for Linux". DarkGuy is working on a 2D game now, called i-team.

---

### Post by DrMega on 2008-02-26
It's been a while since I last followed this project. Is it still going?

---


---
title: "Game engines"
date: 2010-06-09
forum: Programming Talk
---

### Post by Possum Films on 2010-06-09
Me and a couple of my friends are planning on making a horror FPS game (maybe similar to Doom 3, F.E.A.R) and I was wondering what would be the best 3d engine to use. 

So far I've looked at Irrlicht, Horde3d, Panda3d, Ogre and BlendELF

Irrlicht seems very good. There's a very large community, it's easy to use and it's very stable, although there are a lot of features it doesn't have that I would like such as post-process effects, specular mapping, bloom and realistic water that it doesn't have.

Panda3d also looks very nice. Since it is a full game engine, not just a 3d graphics engine it also includes everything else necessary for a game such as sound, physics, etc which means I wouldn't have to do any work trying to get multiple libraries to work together. It has support for a few things Irrlicht doesn't such as bloom, specular maps, gloss maps, and HDR rendering. The main thing I dislike about it is that there isn't very good documentation for the C++ binding and (at the moment) I don't know Python. 

Ogre looks very good. Of all the open source engines I've tried so far it is probably the prettiest looking in screenshots, although I don't want to just judge a book by its cover. I also noticed in the examples included with the engine there were a couple of very nice looking water simulations (realistic water is going to be important in our game).

Horde3d was very hard to set up, there's very poor documentation and the community is very small but I am still interested in it because it (supposedly) uses more modern/advanced rendering techniques than the others and it does have quite a nice range of features. 

BlendELF is a game engine I only came across a few days ago. It is very new and is still hasn't had a stable release yet but it is really easy to use, it's graphics look awesome, and it has lust about all the features I want except for realistic water and having multiple animations on the same model (not entirely necessary for me). 

I've also heard about a few other 3d engines like OpenSceneGraph and CrystalSpace (a game engine) but this is all I've had time to actually try out. 

Large portions of the game are going to be set in a sewer so realistic water rendering is absolutely necessary (most 3d engines support some kind of water rendering, with varying degrees of realism, I'm probably going to end up having to implement my own shader for water). Since the whole game is going to be set indoors the game engine doesn't need to be optimised for rendering large outdoor scenes. The game is going to need to run on both Linux and Windows since I run Linux and the other people I'm going to be developing the game with use Windows. 

So I was just wondering what other people's opinions on 3d engines are before I set out to develop a game.

---

### Post by DanielWaterworth on 2010-06-09
There was an open-project that used blender and crystal-space to make a game. You could copy there design flow if you're looking for a tried and tested method, the website for the project is [here.]("http://www.yofrankie.org")

---

### Post by Tahakki on 2010-06-09
OGRE is very well documented in C++, I think. I gave up on it because the python bindings were so difficult to install.

---

### Post by juancarlospaco on 2010-06-09
*Panda3d, if you know C++, you will learn Python on a Day.*

---

### Post by Possum Films on 2010-06-09
> **DanielWaterworth said:**
> There was an open-project that used blender and crystal-space to make a game. You could copy there design flow if you're looking for a tried and tested method, the website for the project is [here.]("http://www.yofrankie.org")
I tried the version of that game that was made using the Blender Game Engine and I didn't really like it. It always took at least a minute to load the level selection screen and about 3 mins to load a level, the video seemed a bit choppy (even on a computer that could handle Crysis without any problems) and also for some reason the gnome panels were still visible in full-screen mode. I might still try out the CrystalSpace version though, since apparently that's better quality.

---

### Post by DanielWaterworth on 2010-06-10
It'll always be slow in the blender game engine version and it's not meant for production. I'd definitely recommend the crystal version before dismissing it.

---


---
title: "Game Development"
date: 2008-02-09
forum: Programming Talk
---

### Post by Dev'olution on 2008-02-09
Hi,

I've recently completed my uni degree in Game Development, however, i am unsure as to the modelling & engine options that are offered by Ubuntu Linux, as I would like to develop games for it.

Any Help?

Cheers,
Kristian

---

### Post by slavik on 2008-02-09
Look into Unreal Tournament 2004, Doom3, Quake3, Torque.

The last is a game engine built commercially to be a game engine.

---

### Post by Dev'olution on 2008-02-09
> **slavik said:**
> Look into Unreal Tournament 2004, Doom3, Quake3, Torque.

The last is a game engine built commercially to be a game engine.
I was more looking into the likes of something i saw called 'crystal space'... Anything like that around?

---

### Post by pmasiar on 2008-02-09
which programming languages are you interested? Or there is only one true C++? Any special area of interest?

---

### Post by Dev'olution on 2008-02-09
> **pmasiar said:**
> which programming languages are you interested? Or there is only one true C++? Any special area of interest?
I'm trained in C and Assembly, but C is really only ever used in game development anyway, with assembly built in just to speed things up a little.

I'm happy to learn another language if it aids development on Ubuntu

---

### Post by drummingpariah on 2008-02-09
> **WestAussieUbu said:**
> I'm trained in C and Assembly, but C is really only ever used in game development anyway, with assembly built in just to speed things up a little.

I'm happy to learn another language if it aids development on Ubuntu

Wow.  C++ and C# are becoming increasingly popular for game development, and depending on the scale you're looking for, python may be perfect.

Check into different engines based on the Ogre rendering engine, including python-ogre (which is really just an engine framework, not a full-featured engine).  Assembly and C are becoming increasingly rare in the game development industry because of raw increases in hardware and development time costs (high-level coding saves massive amounts of time and money for the developer, and raises minimum system requirements for the end-user only slightly).

---

### Post by Dev'olution on 2008-02-09
> **drummingpariah said:**
> Wow.  C++ and C# are becoming increasingly popular for game development, and depending on the scale you're looking for, python may be perfect.

Check into different engines based on the Ogre rendering engine, including python-ogre (which is really just an engine framework, not a full-featured engine).  Assembly and C are becoming increasingly rare in the game development industry because of raw increases in hardware and development time costs (high-level coding saves massive amounts of time and money for the developer, and raises minimum system requirements for the end-user only slightly).
I hear that, but I also took a course in Operating Systems Basics, hence the reason I'm also developing victoryOS ;)

---

### Post by Lster on 2008-02-09
Hi!

I am also making a game engine under Ubuntu in C. You might want to look into libraries like OpenGL, OpenAL and SDL. I use all three and love them! You might also want to look at the site GameDev which I also find very helpful.

HTH,
Lster

---

### Post by kripkenstein on 2008-02-09
> **WestAussieUbu said:**
> I was more looking into the likes of something i saw called 'crystal space'... Anything like that around?

CrystalSpace and its assorted addons (Crystal Entity Layer, plugins, etc.) are one way to go. Should be in the Ubuntu repos, but might be better to get from svn.

The main alternative to CrystalSpace is Ogre3D. Also in the repos.

Both are C/C++, but should have bindings to python (wasn't easy to set them up, though, last I checked).

Aside from these 3D engines, there are various game frameworks, like PyGame and so forth. What specifically do you need?

---

### Post by pmasiar on 2008-02-09
> **WestAussieUbu said:**
> I'm happy to learn another language if it aids development on Ubuntu

Ubuntu uses Python for it's own development, and OLPC (One Laptop Per Child) too. With your strong programming background you can pick Python in a weekend. And with your C skills, you can convert any Python code to C library when you need speed.

You may want to check GameBaker project in my sig - it might be something you may be interested in.

---

### Post by mridkash on 2008-02-10
Linux has a 3d modeling application called Blender and it has a game engine too.
A game is being built using only open source apps, have a look [http://apricot.blender.org](http://apricot.blender.org)

---


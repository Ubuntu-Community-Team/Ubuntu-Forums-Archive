---
title: "Blender &amp; Python - Showing 3D objects"
date: 2015-12-01
forum: Programming Talk
---

### Post by scoutchorton on 2015-12-01
Hello Forums!

I am a somewhat new programmer, (only 14 and don't have a lot of experience) and I want to start getting into gaming programming. I am on Khan Academy, and have started on a few games there, but the basic JavaScript won't cut what I need to do.

I also have a little experience in Blender, and I know how [SIZE=2]to [/SIZE]make 3D objects. I love using Python 2(.10, .9, .7, whatever), and I would like it if I could use these 3D objects in a python game. I know about Pygame and a few other python modules, but I don't have much experience in it.

[SIZE=4]The big question is:
    How can I use exported objects from Blender with a Python module to make a cool game?

[SIZE=2]Like I said, I'm not too experienced, and don't have much advanced programming knowledge, but I am willing to learn and try.

[/SIZE]Thanks in advance, and good luck! [/SIZE]:D[SIZE=4]
[/SIZE]

---

### Post by T.J. on 2015-12-02
Hello Caleb! =)  

I'm very pleased to meet you. I am happy to see you interested in programming.  I started when I was close to your age, and hope you will have a long and varied interest in it.  I am a programmer also, and have been one for over 25 years.  It's a fine hobby that can become a satisfying career, but it can also be a lot of work.  As long as you are dedicated and willing to work hard, I have no doubts that you succeed in whatever language or type of game you decide to make.

To answer your question directly, anything is possible, including writing games using Python, but personally, I would not use it for that purpose. As a rule, I do not recommend Python for new programmers.  I'm not trying to discourage you from using it, only that it is not the best teaching tool. Python has many flaws.  In my opinion, Python promotes very sloppy programming habits that are hard to unlearn later as you move into the more commonly used languages for games. Professionally, the greater portion of games are written using C or C++, but those languages require experience to use properly.  Don't be discouraged! As a first language, something like Visual BASIC or C# can be used to create REALLY good games and might be more suitable if you plan to play them on Windows. 

You are quite correct in your insights.   JavaScript really will not do.  It is not designed for games.  It was designed for webpages, and little else.  Blender is a lovely tool and quite reasonable for beginning 3D work.  There are a number of tools for using your 3D images in constructing a game. Perhaps this may interest you: **[https://unity3d.com/](https://unity3d.com/)**

Please feel welcome to ask me anything you like!

Take care, 
T.J.

.

---

### Post by scoutchorton on 2015-12-02
T.J., thanks for the suggestions. The reason I want to use Python to make a game is because I feel that with modules that you can install, programming is really infinite. Although it already is, it is now double infinite.

But I was considering C or C# because I know if I want to get into mobile programming (I mean, make a skill a little bit of a profit ;), and there was a job possibility nearby that I would consider, and they needed C or C#), and I though because Python was build on C libraries and Apple programs are build on Objective C, it would be logical. But I didn't know where to go to learn it. Codecademy has EXCELENT courses for Python and HTML/CSS, but they don't have C/C#/C++/etc. I don't know where to learn it, and I need SOME basics before I can teach myself.

Unity I might consider. A friend of mine (I believe) got into Unity a little, so I might be able to convince him to go back and do that. And if I am correct, the GUI for Ubuntu is in Unity (or it is powered by Unity). I saw on the Unity 3D website that they have tutorials, so I might check it out.

So far, I know basics of ProcessingJS (from [khanacademy.org]("https://www.khanacademy.org/computing/computer-programming")), I completed the course for HTML/CSS and at 50% for Python on [Codecademy]("https://www.codecademy.com/"). I also do some spare things here and there like terminal for Ubuntu, a little terminal integration for Python (using os.system()), and that's about it. I will try Unity, and if I find a place to learn C or C#, I will eventually start on that.

Thanks for the help! :D

---

### Post by DaviesX on 2015-12-02
Yes, you will need python to export data from blender if want to have access to everything you created in blender. More specifically, you need to write python script using the APIs blender provides and gather the data and write them into your preferred file format, which you can load in to your game later on. The script add-on is installed through File=>User preferences=>Add-Ons. 

List of samples
[http://wiki.blender.org/index.php/Extensions:2.6/Py/Scripts](http://wiki.blender.org/index.php/Extensions:2.6/Py/Scripts)

python API
[http://www.blender.org/api/blender_python_api_2_70a_release/](http://www.blender.org/api/blender_python_api_2_70a_release/)

I have to say this is totally not trivial for new programmer.

But if you only need geometry data, there are plugins that bundle with the default blender installation. Just click on file=>export=>... then select whatever format you want to go with. You will then write a parser to read them into your game.

But yeah, it's unusual to use python to "build" video games, but it's common practice to use scripting language on top of a game engine. For example, Panda3D is a good choice if you really want to use python script([https://www.panda3d.org/](https://www.panda3d.org/)).

PS: Ubuntu Unity is not the same thing as Unity3D :)

---

### Post by T.J. on 2015-12-02
> But I was considering C or C# because I know if I want to get into mobile programming (I mean, make a skill a little bit of a profit ;), and there was a job possibility nearby that I would consider, and they needed C or C#), 

The reason I mentioned them is that they would give you a better understanding of programming than Python.  Python is what we call a "defacto" language.  It has no set standard for behavior, and different versions are incompatible.

> Python was build on C libraries 

Partly true.  Python is written in C. Most programming languages have the ability to use C libraries because virtually all operating systems are written or derived from C or C++.  C is like a "super language" - virtually every other language uses it as a basis.


> Apple programs are build on Objective C, it would be logical. But I didn't know where to go to learn it.

You would have to learn Objective C from a book. Objective C is a derivation of C. Apple is pretty much the only one who uses it, so it would not be high on my list.


> Codecademy has EXCELENT courses for Python and HTML/CSS, but they don't have C/C#/C++/etc. I don't know where to learn it, and I need SOME basics before I can teach myself.

Try a library.  I know it is a bit old fashioned but most programming books are published by companies such as Wiley or Addison/Westley. If you have a Kindle I'm sure you can find something.  There are plenty of free tutorials online.


> And if I am correct, the GUI for Ubuntu is in Unity (or it is powered by Unity).

No, it is not.  Ubuntu Unity has nothing to do with Unity 3D.  Ubuntu Unity is written in C.


> So far, I know basics of ProcessingJS (from [khanacademy.org]("https://www.khanacademy.org/computing/computer-programming")), I completed the course for HTML/CSS and at 50% for Python on [Codecademy]("https://www.codecademy.com/"). I also do some spare things here and there like terminal for Ubuntu, a little terminal integration for Python (using os.system()), and that's about it. I will try Unity, and if I find a place to learn C or C#, I will eventually start on that.

Take your time and don't rush, otherwise you may become frustrated.  Programming also requires some patience.

> Thanks for the help! :D

You're very welcome.

---

### Post by T.J. on 2015-12-02
[dup]

---

### Post by scoutchorton on 2015-12-02
> **DaviesX said:**
> But yeah, it's unusual to use python to "build" video games, but it's common practice to use scripting language on top of a game engine.

Yeah, I am really familiar with Python, and just want to try making a game with what I know? I just want to use what I have to try and make something.

Looking at the Blender Python API link you gave, it uses Python 3.x, which again, I don't know.

But the goal of my question was rather how I can use exported files from Blender and use them with a module like Pygame. I could just make a small video for character movement that is a close to perfect loop, but I don't know. I was wondering if there was some pyobj module or something to load those types of files.

But thanks for the response!!

> **T.J. said:**
> [COLOR=#000000]Try a library. I know it is a bit old fashioned but most programming books are published by companies such as Wiley or Addison/Westley. If you have a Kindle I'm sure you can find something. There are plenty of free tutorials online.[/COLOR][COLOR=#000000]

[/COLOR]I guess I'll give it a look. I like (and prefer) the kind of style Codecademy and khanacademy use, where it is like a few variable at a time, then practice, then repeat. I'm not sure if books have that sort of thing, but I will check it out (on iBooks).

> **T.J. said:**
> [COLOR=#000000] Ubuntu Unity has nothing to do with Unity 3D. Ubuntu Unity is written in C.[/COLOR][COLOR=#000000]

[/COLOR]Another reason to do C? ;)

> **T.J. said:**
> [COLOR=#000000]Take your time and don't rush, otherwise you may become frustrated. Programming also requires some patience.[/COLOR][COLOR=#000000]

[/COLOR]Don't think of it as "rush," but think about it as "itchy feet."

Thank you both for the help. I will consider C, and see what I can do about a .obj (or similar format) displayer Python Module.

Remember, may the code be with you! :D

---

### Post by DaviesX on 2015-12-03
No, pygame doesn't handle 3D geometries. You need other libraries to do that. You may take a look at Panda3D engine. It covers most aspects for game logic/rendering/kinematics/animation. 

I guess you want to use obj format to store geometries. You can write a parser to extract data from the file which are then used to construct geometries in Panda3D. obj format is pretty straightforward. It's just a text file. It contains lists of vertex data and polygon faces.

obj file specification:
[http://www.martinreddy.net/gfx/3d/OBJ.spec](http://www.martinreddy.net/gfx/3d/OBJ.spec)

There are only two data blocks you need to look into ([COLOR=#000000]Vertex data and [/COLOR][COLOR=#000000]Elements section)[/COLOR].

---


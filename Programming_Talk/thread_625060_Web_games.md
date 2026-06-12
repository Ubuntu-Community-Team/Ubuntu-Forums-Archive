---
title: "Web games"
date: 2007-11-27
forum: Programming Talk
---

### Post by hockey97 on 2007-11-27
Hi I  have a question  on  making web games.   

My questions is  what programming language is best for  a major 3d web game that is played online. Also what would be the best way on doing this, meaning  have the game being played using the web browser  or having it separate , something like todays pc video games with have their own interfaces and networking .

I am planning to start some online game but don't know what would be the best professional way to go abouts making a web game. I am at a stage to decide what way's would be best to lower lagging problems.

I was told before from people that already have made a web game they suggested to me  to just make an pc game with multi-player capacities, and was told that java is the best lang to make web games but can't make good 3d nore real 3d games, just 2d and  faking 3d games could be made.

I know c++, python,  c-script, html, and php , I mostly know c++ compared to the rest my strength is c++.

I have  made a game but never created any games with networking or multi-player.

---

### Post by CptPicard on 2007-11-27
> **hockey97 said:**
> Hi I  have a question  on  making web games.

I'm such an old fart already that for me, the "web" specifically means the World Wide Web, that is, a game that works embedded in a browser, in this case. Let's assume you mean a broader definition, a game that just works over the network but that can be a standalone application as well...

> My questions is  what programming language is best for  a major 3d web game that is played online.

For standalone application, engine in C, C++. Possible scripting with any scripting language of your preference.

For something that runs in browser, Flash or Java applets.

> Also what would be the best way on doing this, meaning  have the game being played using the web browser  or having it separate , something like todays pc video games with have their own interfaces and networking

Depends on how heavy-duty you want it to be. Generally, for anything approaching "today's pc video games", it certainly won't be in the browser, but as a (very complex) standalone application.

> I am planning to start some online game but don't know what would be the best professional way to go abouts making a web game.

Become a very proficient programmer first. That goes a long way. And learn to salt your hashes ;)

> I am at a stage to decide what way's would be best to lower lagging problems.

Premature optimization is the root of all evil. Are you sure your application's issues are in network lag? Interestingly, maintaining a distributed gameworld consistency is a very tough topic.

> was told that java is the best lang to make web games but can't make good 3d nore real 3d games, just 2d and  faking 3d games could be made.

If you want something in an applet (think Wolfenstein 3D, an oldie from the early 90s, or even Doom), yes you do have a 3D API there in Java. Nothing stops you from writing your own renderer of course, if you've got the competence. Lots of material out there on the net on writing a rudimentary 3D engine.

But yes, applets are a lame platform for anything more intensive.

There is this some Python game writing toolkit you might want to look at, with the understanding that you're not writing the next Half-Life any time soon... PyGame, was it?

---

### Post by Wybiral on 2007-11-27
If you want it to work in the browser, you really only have flash or Java to choose from. But 3d games don't work very well in the browser because it has terrible protocols for the kind of networking you'll need.

For none browser... If you're writing it from scratch I would go with: Python using PyGame+OpenGL+Twisted. You can always use C++ and a good networking library. And, of course, you can always look around at the existing games and game engines. For Python, Soya3D would be worth looking into for any larger 3d games. Since you know C++, you might think about modding the [cube engine]("http://cubeengine.com/"). It's open source and pretty simple of an engine. I've played around with the code myself and it's very easy to jump into and start changing things. It also has a built-in level editor and networking code.

---

### Post by hockey97 on 2007-11-27
Thanks for the replies.  
I figured out  that problem I was having with salting and hashing, I was salting the password 2 times one when the user registers and one when I was comparing the input,  I  generated random numbers and used those to salt the  password then hash it so basicly  I was comparing  a hash in the database with a new hash which would never match.

 The web game I am going to make I want to make sure that I can have legal rights over it, since I am using  other peoples libraries and engines  so I don't get sued for anything.

I made a website in php and will buy a domain later after I finish this web game I plan to do that.

the  game I want to make was to have something to attract people to my website.

since we are talking about the web game what do you guy's use to create sound effects or songs, music? 
I would like to  make my own so I don't have to  pay alot of $$$ for a few songs ect.

---

### Post by Wybiral on 2007-11-27
> **hockey97 said:**
> Thanks for the replies.  
I figured out  that problem I was having with salting and hashing, I was salting the password 2 times one when the user registers and one when I was comparing the input,  I  generated random numbers and used those to salt the  password then hash it so basicly  I was comparing  a hash in the database with a new hash which would never match.

 The web game I am going to make I want to make sure that I can have legal rights over it, since I am using  other peoples libraries and engines  so I don't get sued for anything.

I made a website in php and will buy a domain later after I finish this web game I plan to do that.

the  game I want to make was to have something to attract people to my website.

since we are talking about the web game what do you guy's use to create sound effects or songs, music? 
I would like to  make my own so I don't have to  pay alot of $$$ for a few songs ect.

You'd be surprised how much content you can get away with if you just ask the author. Look for loosely licensed textures/models/sounds around the net and just email the author and talk them into giving you permission.

I believe the cube engine is licensed under zlib, but not all of the media included. But, like I said, if you use any of their media, you can probably just contact the authors and ask them for the right to use it in your game.

---

### Post by hockey97 on 2007-11-27
Thanks for the replies/help , I decided to go with just making a pc game in c++   and  grabbing a network lib, and  I might just get a graphic engine, not sure.

---

### Post by pmasiar on 2007-11-29
C++ is obviously fast client for graphics, but most of your time delay will be on web traffic. Eve Online is MMO game in Python. Python uses exactly the same libraries for graphics.

---


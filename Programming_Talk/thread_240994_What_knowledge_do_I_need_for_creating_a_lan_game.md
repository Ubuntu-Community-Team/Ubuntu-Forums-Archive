---
title: "What knowledge do I need for creating a lan game?"
date: 2006-08-21
forum: Programming Talk
---

### Post by harisund on 2006-08-21
Ok, first off, the game is merely chess. It's not something that involves mind bending graphics. 

So, I wanted to play Chess with my friend over the LAN, and found that there was practically no software that we could use. Of course, we could go online, but the point was we didn't have internet, all we had was a cross over cable. 

So what should I know? Sockets? 

I know to code decently .. just thought this would be a nice thing to get my hands dirty with :)

---

### Post by tribaal on 2006-08-21
Well it all depends on what language you intend to implement your game in...

I guess most high-level programming languages have toolkits for networking that would take care of the socket level for you (Python, Java...). You should probably start by picking up a language you like / would like to learn / are familiar with and spend some time reading about the network APIs available.

Then you should also look into the GUI part... For example I'm pretty confident with swing in Java, but my head hurts when I have to design a GUI in Python...

Does that help?

- trib'

---

### Post by harisund on 2006-08-22
Hmmm...thanks for that information. It didn't strike me that most high level languages will have the necessary API for network related stuff. I was worried I will have to get down to the level of sockets or something myself. 

GUI I was primarily thinking about Glade. Perhaps GTKmm (C++) or pyGTK (python) to interface with Glade. 

Thanks for that! It sure helps!

---

### Post by LordHunter317 on 2006-08-22
The necessary API is sockets or some wrapper around them.  However, that wrapper can make them far eaiser to use; Python does some stuff so you can use IP addresses as strings directly, for example.  Far less painful than doing conversions.

But you will need to know BSD sockets, ultimately.

---

### Post by Endwin on 2006-08-22
If you decide to go the C++ route this is a good place to learn the basics of network programing.

[http://beej.us/guide/bgnet/output/htmlsingle/bgnet.html]("http://beej.us/guide/bgnet/output/htmlsingle/bgnet.html")

---

### Post by harisund on 2006-08-22
Hmmm.. thanks LordHunter317 for that info. I will have a further look. 

I will eventually be learning about sockets at my univ. classes, so I guess I might as well get started :)

And thanks for the link. I was about to start googling myself, and you got me off to a good start !

---

### Post by Flubs4u on 2006-08-22
I was on a team that did a network game very similar to bingo for a school project.  We used sockets with C# and it was a total pain in the butt.  We didn't learn about networking APIs untill we already had it working ](*,)

---

### Post by harisund on 2006-08-22
C# I see... now that's not something I see frequently, atleast not at my ACM meetings and in general on my campus :) How did you find the project in general?

---

### Post by LordHunter317 on 2006-08-22
I suspect their issue was more not knowing networking APIs and how to deal with common networking issues than the C#.  What little C# networking stuff I've done has been OK.  NOt great, but no worse than Java or WinSock stuff.

---

### Post by Flubs4u on 2006-08-22
> **LordHunter317 said:**
> I suspect their issue was more not knowing networking APIs and how to deal with common networking issues than the C#.  What little C# networking stuff I've done has been OK.  NOt great, but no worse than Java or WinSock stuff.

Yeah, we definately didn't have a really good understanding of network programming at all at the time...actually that was our first attempt at it.  C# was similar enough to C++ that the rest of it wasn't really a problem.

---

### Post by kwalo on 2006-08-23
For a simple chess game, I suggest, you should use python. Read tutorial and reference manual, from the official web site. There you'll find everything about network/sockets.

For gui part: Tkinter (TCL binding) and pygtk python modules might interest you.

About sockets:
Good source of information is:```
man 2 socket
```and all stuff, that's in SEE ALSO section. You must have **manpages-dev** package installed.

If you're familiar with C, check out the source code of wget.```
apt-get source wget
```In file connect.c You'll see a real-life example of using socket API.

---

### Post by peabody on 2006-08-27
Does anyone know off hand if SDL or pygame has a networking framework?  I thought they did.  I would think that would be the most straight forward way to go about it especially for a game.

---

### Post by LordHunter317 on 2006-08-27
It's terribly inadequate for several kinds of games.  It may be adequate for chess, but it still will require some understanding of BSD sockets.

---


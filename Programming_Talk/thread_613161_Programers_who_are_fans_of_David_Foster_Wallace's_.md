---
title: "Programers who are fans of David Foster Wallace's &quot;Infinite Jest&quot;"
date: 2007-11-14
forum: Programming Talk
---

### Post by employeeno5 on 2007-11-14
Hi there. 

I'm 25 and have just started to attempt to teach myself Python and Java Script. Back between the ages of 10 and 14, I screwed around a lot with QBasic and HTML, but was never serious about them and haven't written any code since. I've always believed programming to be an amazing creative tool, but my interests and education headed down a fine arts road did not include coding. 
My creative interests recently have turned more and more to computers and I'm really taken with the open source software movement and am excited to learn more about programming.

Now, anyone who has read David Foster Wallace's masterpiece "Infinite Jest" will have no problem remembering the game "Eschaton".
For those who are unfamiliar, in the book, Eschaton is a real-time strategy game that was designed and played by teenagers at a tennis academy. The game involves using a grid a 4 tennis courts as a surrogate for a large map of the world. Teams representing Cold War Super-Powers are stationed in positions around the courts that would correspond to their geographic locations on a map. Each team's territory has items placed on the ground representing major strategic and population centers. Each team has various resources, military economic and otherwise, assigned to them in some general accordance with reality (at least during the cold war.) One of these resources is nuclear war heads. These are represented by tennis balls, which the teams (in accordance with an invented geo-political scenario leading to nuclear war) proceed to lob at each others major military and population targets. The closer to a target that a tennis ball lands, the more direct a hit. 
During all this there is a score-keeper of sorts who keeps track of everyone's depleting resources with a computer program (written for the game) that has all the important resource variables for each team previously entered. So, if a tennis ball makes a direct hit a hit very close to NYC (on the court) than the loss of population is calculated, as well as the situation with any resources like food and water,fall-out levels, near by military installations, etc. 
This information is relayed to the teams' commanders so they can continue to try to make strategic decisions throughout the apocalyptic madness.

I want to (eventually) write a program that would reasonably facilitate actually playing this game. I know a large number of people who have a strong interest in playing this game but no one with the knowledge to write the program that handles all the calculations. 

I'm wondering if anyone has ever heard of anyone ever trying to do something like this.

If you've read the book and are familiar with the game, do you know of any programs out there that already do similar calculations for some other real-world real-time strategy game? 

I'm  mostly looking to hear from anyone who programs and has actually read the book. I'd like to know if  someone who knows a thing or two about programming and Eschaton (in concept), thinks that this project is something reasonable for an amateur hobbyist to try to accomplish, or if it would really require some very advanced stuff that I shouldn't expect to master unless I've spent many many years programming. I'm not expecting to accomplish this anytime soon, I've just started learning, but I'm hoping my ambition isn't crazy.

Forgive me if this is too weird to be on topic for this forum, but I wasn't sure where else I could get some input on this idea, or see if perhaps something like this has even been done before.

---

### Post by wolfbone on 2007-11-14
I haven't read the book but it sounds a bit War Games-ish - like defcon:

[http://en.wikipedia.org/wiki/DEFCON_(computer_game](http://en.wikipedia.org/wiki/DEFCON_(computer_game))

If you want to write something of your own, though there aren't any direct FOSS equivalents AFAIK, I'd imagine the basic principles - the calculations you speak of - are similar in any RTS.

---

### Post by pmasiar on 2007-11-14
pygame is simplified way to write games in Python. but you need to learn first plain text/commandline Python - wiki in my sig has links to many training tasks.

Is is good you are aware it will take you long time - because it will.
Also, you may  consider plain-text, turn-based version as an advanced training task.

---

### Post by employeeno5 on 2007-11-15
Ah cool. Thanks for the resources. I'll have to check out defcon more in depth later. Yes, the mechanics of the game play are pretty much that of any RTS. 
I was hoping their might even be some open source programs already out there designed to keep track of and calculate certain stats for game that is mostly played outside of a virtual settings such as calculators for  traditional role playing games, or those neat games people play with figurines on miniature landscapes. 
I have just learning after all so perhaps I'm jumping the gun, but I was hoping the peruse the code of something like that to give me a general idea of how a program like that may sometimes be built.
Many thanks for the thoughts.

---

### Post by smartbei on 2007-11-15
Creating a text-based program where:
[list]
[*]You would start it up
[*]It would request all the startup information (or perhaps read it from a file) 
[*]It would update that information every time someone enters the landing place of a tennis ball
[*]Finally, the program would display the results after every turn
[/list]
Should not be very difficult, if this is what you are talking about. This could easily be, as pmasiar suggested, a decent training task for when you already know the language basics. Later still you may want to add a gui to it or remake it into a graphic game that can be played on the computer (using pygame for instance).

---


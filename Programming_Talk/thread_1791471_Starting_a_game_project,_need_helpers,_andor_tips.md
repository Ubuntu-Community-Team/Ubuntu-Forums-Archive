---
title: "Starting a game project, need helpers, and/or tips"
date: 2011-06-26
forum: Programming Talk
---

### Post by Pierrick584 on 2011-06-26
Greetings, I'm starting a game project, and, gotta say, i got a decent C++ knowledge, in theory.. but not much pratice, and i'm using that as a learning, and i were wondering if anyone have some experience that could be avaible when i have questions, much more like, "how can the stats loading should work" or things like that, currently i'm reading other games sources as an example, i'm not looking for someone who would do the work for me.

I would also be interested to team up with anyone interested to participate, but be warned that, even though i like to listen to other's idea (about the game design) i kinda know what i want and the project will heavily folow it. Yet, every help will be apreciated, C++ programming, 3d artist, or whatever else.

You can contact me by private message, reply or idealy by email at [email]pierrick584@linux.com[/email]

---

### Post by cgroza on 2011-06-26
You really don't want your email posted like that on a forum. It will be picked up by spiders and spammers.

---

### Post by Thewhistlingwind on 2011-06-27
> **cgroza said:**
> You really don't want your email posted like that on a forum. It will be picked up by spiders and spammers.

This

Besides that, if you want help you should tell us more about the game, obviously not the whole spec doc, but at least a general summary of what your trying to achieve.

---

### Post by Pierrick584 on 2011-06-27
Lol, couldnt care less of spam, you know, spam filter exist for a reason.

And, as for the game project.. to make it short..

Genre: MMORPG
Engine: Panda3D (realy, looking for something else beacause of poor C++ documentation / comunity)
Graphic: 3D
Aimed Platform: Linux, Mac, Windows, (i wish i could get an engine that could support Wii too... even if it dont support Mac)
Why?: Mostly beacause i do need a project, and i dont have much ideas about something else


Am i missing something? just ask

---

### Post by simeon87 on 2011-06-27
MMORPG are among the hardest projects to create (for one person..) and it takes a lot of persistence and knowledge to do it. I think it's easier to post your questions in these forums, when you have them, rather than asking for one person as mentor. After all, more people know more than one usually.

---

### Post by PaulM1985 on 2011-06-27
If you are about to start a serious game project, you are going to need to do alot of planning.  Define the scope of your game, what things are going to exist in it, how are these things going to interact, etc.

It would be useful for you to do a bit of research on game design, game coding, etc. (Sorry if you already have and this stuff is already very obvious to you).

As far as game engines are concerned, I have heard good things about SDL (I haven't used it myself though) and there seem to be quite a few big name games that use it: [http://en.wikipedia.org/wiki/List_of_games_using_SDL](http://en.wikipedia.org/wiki/List_of_games_using_SDL)

Paul

---

### Post by nvteighen on 2011-06-27
Setup a Github, Google Code or Launchpad project (no, not Sourceforge please), as soon as you've got some code and a more or less definite idea of what you're doing (not exactly how). That's the way to start: making it public and giving people the possibility to contribute.

Of course, you'll have to have some "marketing" strategy in order to get people interested in your project.

Launchpad (uses Bazaar): [https://launchpad.net](https://launchpad.net)
Github (uses Git): [https://github.com/](https://github.com/)
Google code (uses Subversion, but it may allow other VCSs, i.e. Version Control Systems): [http://code.google.com/hosting/](http://code.google.com/hosting/)

---

### Post by DangerOnTheRanger on 2011-06-27
> **Pierrick584 said:**
> Lol, couldnt care less of spam, you know, spam filter exist for a reason.

And, as for the game project.. to make it short..

Genre: MMORPG
Engine: Panda3D (realy, looking for something else beacause of poor C++ documentation / comunity)
Graphic: 3D
Aimed Platform: Linux, Mac, Windows, (i wish i could get an engine that could support Wii too... even if it dont support Mac)
Why?: Mostly beacause i do need a project, and i dont have much ideas about something else


Am i missing something? just ask

I think you are missing something. Panda3D's intended development language is Python, so the documentation is *much* better on it's manual's Python side. Plus, it comes with a (free and open-source) built-in MMO server and client, so you're good to go in that aspect.

I can personally attest to Panda3D's power and simplicity (at least in conjunction with Python), as I use it myself in my gaming project.

---

### Post by Pierrick584 on 2011-06-27
Well, that is definitively a good tip, yet, aint sure i want it that wide open, even though that'll definitively make it harder to have more people working on it.  on a side note, got any closed suggestion of source control software?

---

### Post by Pierrick584 on 2011-06-27
> **DangerOnTheRanger said:**
> I think you are missing something. Panda3D's intended development language is Python, so the documentation is *much* better on it's manual's Python side. Plus, it comes with a (free and open-source) built-in MMO server and client, so you're good to go in that aspect.

I can personally attest to Panda3D's power and simplicity (at least in conjunction with Python), as I use it myself in my gaming project.

I know that python is the main focus, but i dont want to get stuck with performance issue right away, on top of that, i dont know python, and on top of that again, working in C++ is more important that the project itself, its just lame that people dont give a **** about C++ part of panda3d. but yeah, to answer to you, not, i'm not missing that part

---

### Post by JupiterV2 on 2011-06-27
> **Pierrick584 said:**
> Well, that is definitively a good tip, yet, aint sure i want it that wide open, even though that'll definitively make it harder to have more people working on it.  on a side note, got any closed suggestion of source control software?

Git, Bazaar and Mercurial can all be used locally. Alternatively, if all you want is version control then maybe CVS or SVN might be more to your liking.

---

### Post by DangerOnTheRanger on 2011-06-27
> **Pierrick584 said:**
> I know that python is the main focus, but i dont want to get stuck with performance issue right away, on top of that, i dont know python

Slightly off-topic, Python won't give you a noticeable performance hit, due to the fact Panda3D itself is written in C++, *not* Python. And since Panda3D is what the CPU will be executing %99 of the time...

Getting back on topic, I'd suggest looking at one of the games written in C++ and Panda3D that's available on their forums. [http://www.panda3d.org/manual/index.php/Starting_Panda3D](http://www.panda3d.org/manual/index.php/Starting_Panda3D) might also be useful.

---

### Post by Pierrick584 on 2011-06-27
> **DangerOnTheRanger said:**
> Slightly off-topic, Python won't give you a noticeable performance hit, due to the fact Panda3D itself is written in C++, *not* Python. And since Panda3D is what the CPU will be executing %99 of the time...

Getting back on topic, I'd suggest looking at one of the games written in C++ and Panda3D that's available on their forums. [http://www.panda3d.org/manual/index.php/Starting_Panda3D](http://www.panda3d.org/manual/index.php/Starting_Panda3D) might also be useful.


Yeah, i know that the performance is not THAT bad, yet, some people did benchmark of panda3d to compare both language, there is a big number difference, prolly not noticeable by normal operation, but i do want to code it in C++ anyway, And, yeah thats kinda what i'm doing arleady, yet, thanks for the good tip.

---

### Post by PaulM1985 on 2011-06-27
I have just started reading this book: [http://www.amazon.co.uk/Game-Coding-Complete-Mike-McShaffry/dp/1584506806/ref=sr_1_1?ie=UTF8&qid=1309204870&sr=8-1](http://www.amazon.co.uk/Game-Coding-Complete-Mike-McShaffry/dp/1584506806/ref=sr_1_1?ie=UTF8&qid=1309204870&sr=8-1)

I am enjoying it so far, the author's writing style is quite nice, and although I am only part way through the introduction, I have flicked through the openings of some of the chapters and it looks as though it is going to cover plenty of things that I am going to come up against with my projects.  Although it has a Windows bias I am sure the concepts should be transferable.  I am reading it with a Java background hoping to transfer the ideas to that.  Might be worth a read.

Paul

---

### Post by Simian Man on 2011-06-27
An MMORPG is an incredibly hard piece of software to create.  Since you don't even have much programming experience, I'd start with something just a bit simpler.  Like Pong.

---

### Post by Pierrick584 on 2011-06-27
> **Simian Man said:**
> An MMORPG is an incredibly hard piece of software to create.  Since you don't even have much programming experience, I'd start with something just a bit simpler.  Like Pong.


Dont worry, i do know what i'm getting into, thats just how i am, going at first in the hard part, and learn that way, i'm definitively not the kind to start things beign uninformed about it.

> I have just started reading this book: [http://www.amazon.co.uk/Game-Coding-...9204870&sr=8-1]("http://www.amazon.co.uk/Game-Coding-Complete-Mike-McShaffry/dp/1584506806/ref=sr_1_1?ie=UTF8&qid=1309204870&sr=8-1")

I am enjoying it so far, the author's writing style is quite nice, and  although I am only part way through the introduction, I have flicked  through the openings of some of the chapters and it looks as though it  is going to cover plenty of things that I am going to come up against  with my projects.  Although it has a Windows bias I am sure the concepts  should be transferable.  I am reading it with a Java background hoping  to transfer the ideas to that.  Might be worth a read.


Thanks for the suggestion, i tend to avoid windows-only based books, but still apreciate the suggestion

---

### Post by PaulM1985 on 2011-06-28
Still a great book, that link allows you to read the first few chapters.  At least have a look at it before you dismiss it.  The concepts are the important part, not the code samples.  If a programming author had to make everything they did platform independent (meaning not just Windows, Linux, but also including Mac, PS3, Xbox360, Wii in the case of game programming) they would spend more time compiling code to make sure it works than writing a book.

Paul

---

### Post by GenBattle on 2011-06-28
> **Pierrick584 said:**
> Dont worry, i do know what i'm getting into, thats just how i am, going at first in the hard part, and learn that way, i'm definitively not the kind to start things beign uninformed about it.



Thanks for the suggestion, i tend to avoid windows-only based books, but still apreciate the suggestion

I don't think you do know what you're getting into. Have you ever made a game before? Have you done 3D graphics before? Any experience with network systems coding? Any experience with AI? any experience with 3D modelling and texture painting? Most game designers spend years just trying to become an expert in one of these areas, and you haven't mentioned what your specific skill set is.

Do you have any plans for particulars of the game, or just a general idea of what you want to produce?

I'm not trying to be mean about it, I just see this sort of project idea/post fairly often, usually by people who are ok programmers but have absolutely no experience producing games. Like everything, you really have to start small, and you have to plan meticulously.

MMOs are huge, not just because of the programmatic complexity, but because of the sheer volume of content (models, textures, sounds, text) required to fill them.

I'm not saying such a game is impossible to create; games like Minecraft prove that. It just takes a combination of skill, experience, time, perseverance and a great idea.

---

### Post by Pierrick584 on 2011-06-28
Yes, as i said, i know what i'm getting into, i know that i wont do all by myself, i know i will probably not even have anyone on the project, i know i'm a freaking shitty artist so i wont do anything more than rectangle and sphere character as filler to test the code, and i know that an mmo is close to impossible to do alone, and you know what? i dont expect to finish it alone, yet, i dont do something to have a result, but for the fun of it, and i dont care less about it beign a game, realy, i'd have just as much fun coding anything else, but i dont have any better idea, and thats definitively interesting, mainly beacause of the complexity, giving me a wide range of things to do, now, please stop poluting the thread with "you cant do it" post, they're pointless, i dont expect any specific result, yet, if i ever get people involved, maybe a result will happend, we'll see, either way i dont care.

---

### Post by PaulM1985 on 2011-06-28
> **Pierrick584 said:**
> Yes, as i said, i know what i'm getting into, i know that i wont do all by myself, i know i will probably not even have anyone on the project, i know i'm a freaking shitty artist so i wont do anything more than rectangle and sphere character as filler to test the code, and i know that an mmo is close to impossible to do alone, and you know what? i dont expect to finish it alone, yet, i dont do something to have a result, but for the fun of it, and i dont care less about it beign a game, realy, i'd have just as much fun coding anything else, but i dont have any better idea, and thats definitively interesting, mainly beacause of the complexity, giving me a wide range of things to do, now, please stop poluting the thread with "you cant do it" post, they're pointless, i dont expect any specific result, yet, if i ever get people involved, maybe a result will happend, we'll see, either way i dont care.

I know what you mean.  I have had this before (not here, just in general life).  I have been told by lots of people that I will never do X, Y and Z and have proved them wrong.

You prove everyone else wrong.

I think alot of people are quite negative because as GenBattle says, people saying they are going to make something extremely complicated happens all the time on this forum and the projects come to nothing.  It would be nice to see one of them actually come to something.

Keep determined, don't be afraid to ask questions and be open minded to suggestions that other people make.

Good luck.

Paul

---

### Post by GenBattle on 2011-07-01
> **Pierrick584 said:**
> Yes, as i said, i know what i'm getting into, i know that i wont do all by myself, i know i will probably not even have anyone on the project, i know i'm a freaking shitty artist so i wont do anything more than rectangle and sphere character as filler to test the code, and i know that an mmo is close to impossible to do alone, and you know what? i dont expect to finish it alone, yet, i dont do something to have a result, but for the fun of it, and i dont care less about it beign a game, realy, i'd have just as much fun coding anything else, but i dont have any better idea, and thats definitively interesting, mainly beacause of the complexity, giving me a wide range of things to do, now, please stop poluting the thread with "you cant do it" post, they're pointless, i dont expect any specific result, yet, if i ever get people involved, maybe a result will happend, we'll see, either way i dont care.

As I said, i'm not trying to be mean. My advice is to just remember to keep it small and focused, and it sounds like you already have that in mind when planning your game.

I would love for you to prove my doubts wrong, but as PaulM says, i'm somewhat cynical because of the frequency with which I hear people launch themselves on an epic quest to create something really ambitious. I'm not trying to tell you it can't be done.

---

### Post by skullmunky on 2011-09-03
hey, not sure if this thread's still active but here are some tips:

decide if you're making the game because you really want to see the game exist, or if you just want to learn C++, in which case any fun and challenging programming project would be equivalent.

if (a), start by reading Jesse Schell's Art of Game Design

do think seriously about learning a little python if you want to use Panda - there is much more documentation, and prototyping will be much, much faster than in C++ in general. if you want a C++ engine, my other fave besides Panda is OGRE.

prototype, iterate, and be agile.  figure out some of the core mechanics and do quick and dirty prototypes, determine if they're fun, iterate them and/or throw them out as needed.

panda has good networking built in so that's not as hard to do as one might think. scalability is where it gets hard, as well as determining the right target latency and managing sync with non-deterministic sim elements.  you'll figure that out through prototyping.  

get something that functions, even if it's only spheres questing vs cubes.  if you want additional coders to get onboard they'll be more interested if you've got something proven already.  same with artists: if you have a functioning game in the abstract, and a spec of what the different things should be, you can go over to e.g. deviantart and try and recruit.

last: sure, dream large, go for the mmorpg, and if along the way the thing turns into something completely different with a totally different scope, be open to that option.  have fun!

---

### Post by BcRich on 2012-07-09
Nicely Put skullmunky!
I hope your project is still active and I wish you all the best with what you are doing :)

---


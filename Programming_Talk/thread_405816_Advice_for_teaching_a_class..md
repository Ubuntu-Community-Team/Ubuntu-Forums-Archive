---
title: "Advice for teaching a class."
date: 2007-04-10
forum: Programming Talk
---

### Post by caffienefree on 2007-04-10
I'm teaching computing classes this summer to children from grades ranging from 3-6 (Ages 8-11 approximately). The machines I have are mostly low end, anywhere from 16 to 32 MB (There's one machine with a blazing 128MB), all running Win 98. My goal is to give them a foundation in programming concepts using BASIC, however, I don't think that'll be able to hold their attention for very long unless I start off with something a little more interactive, like LOGO. I also think that if I spend too much time with LOGO, it'll lose their interest as well. I have a clear idea of what I'd like to accomplish with this class, but a murky on how to get there.

I taught myself the principles of BASIC when I was young. It gave me a foundation for not only computing, but general logic. However, these kids are growing up in a world where the only command line they've seen is in the Matrix, and the most computers can do for them is play games. I'd like to change this for them, but it's going to be hard. I only see the kids twice per week, separated for a few days, for 45 minutes. Teaching them will be hard enough, getting the kids to retain it will be even more of a challenge. Does anyone have any advice, suggestions, comments? Thanks in advance.

---

### Post by &lt;mawe&gt; on 2007-04-10
Hi!

One of our members of the [german Python-Forum](http://www.python-forum.de) is teaching Python to kids. They made some videos for ShowMeDo, which you can find [here](http://www.showmedo.com/videos/series?name=pythonJensFromKidsSeries).
The wiki page is [here](http://wiki.showmedo.com/index.php/PythonJensFromKidsSeries), you can also find his email adress there.
Maybe he can give you some advice ;)

---

### Post by pmasiar on 2007-04-10
> **caffienefree said:**
> I'm teaching computing classes this summer to children (...)machines running Win 98. (...)
(...) I only see the kids twice per week, separated for a few days, for 45 minutes. Teaching them will be hard enough, getting the kids to retain it will be even more of a challenge.

As you realized, you have couple hard challenges:
1) your computers are total crap. No chance running anything recent and visual on them. If you are lucky, you can use them as terminals for edubuntu - you need one good server for that, or Xubuntu. Did you tried that? 
If not possible, i would look into some memory-miser distro, like Damn Small Linux. Possibly you will not able to get X runing - you may want to ask experts.

So if no GUI, you need to explain children that althogh computers are obsolete, we can get them to use in commandline. Another option could be to get some really old early version of Logo or Python. If you can dig out somewhere old Windows 3.11 or DRDOS, IIRC they came with BASIC.

2) You do not have much time to teach and retain knowledge. Maybe it would be possible to let children access computers unsupervised, and try stuff by themselves? Here is a [Hole in the Wall](http://www.pbs.org/frontlineworld/stories/india/thestory.html) project from India where children learned using PC by themselves, with no teacher at all. It works.

3) Excellent tools for learning programming is [http://en.wikipedia.org/wiki/Game_maker](http://en.wikipedia.org/wiki/Game_maker) - free, windows-only GUI-based game designer. Excellent drag-n-drop objects optimized to create games, no coding needed. Event handlers also by lego-like statements, really no coding. Possibly old version might run on your best machine.

4) Best language for intro to programming is Python, but I am not sure if any decent version runs on trash you have. [LiveWires](http://www.livewires.org.uk/python/) is intro course (with books, worksheets, tasks etc).

If everything else fails, you can teach them basics of Python in terminal, using [this intro](http://www.livewires.org.uk/python/inexp.html).

IMHO with the crappy hardware you have, don't put children's (and yours) expectations too high. Running edubuntu with decent server would eliminate hardware problem.

Good luck, and let us know!

---

### Post by rplantz on 2007-04-11
I taught CS at a university for 21 years, so my "kids" were a bit older. But I think I learned some things that might apply here.

First, get software that runs well on the hardware you have. Since it's old stuff, the software should be cheap. You can probably find somebody who will donate it.

Next, write the code and run it yourself before having your kids try it. You don't have enough time, and it's generally very boring to students to be debugging lab setups. When you're trying something out, don't forget that it will take the students three or four times as long to do it as it takes you. I think you will be amazed at how fast 45 minutes goes by.

All my programming classes included three-hour labs, which I taught. (No teaching assistants at my university. Labs are taught by the professors.) One of the more successful activities for me was to get my class to work together as a group. For example, one of my exercises was to have the students work together in groups of two or three on one function of the program. I would give them a while. Then each group submitted their solution to me, and I would project the code and we would debug the program as a class. I typically started with my main function and added one student function at a time. If the submitted function was too far gone, I always had my solutions that I could slip in, then move on to the next function.

I don't know if you would have time for this sort of activity. And it would probably require a projector. But most students seem to enjoy the light-hearted "competition." I always kept some humor in the exercise so we could concentrate on learning instead of trying to "win."

---


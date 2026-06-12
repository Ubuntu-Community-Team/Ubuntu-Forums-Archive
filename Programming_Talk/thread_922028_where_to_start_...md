---
title: "where to start .."
date: 2008-09-16
forum: Programming Talk
---

### Post by shift_00 on 2008-09-16
well i would like to share with a bit background for all to see where i'm coming from, i'm a graduate computer science student, a developer by nature, has been working on scientific research for a while, and was a part time game developer for almost two years, languages that i use, c++, c#, java and matlab, but basically visual studio.net was my ide of choice, mainly because i wasn't exposed to the ideology or the philosophy of the open source community, and now that i'm in love with it, and having my ubuntu up and running, i have to ask my fellow programmers where to go and what to do .. in order to become an efficient member of this society (ie writing useful applications under linux ) 

i've came to gather that it's constructed as such "python" "C" then some "perl" is a must .. but i keep hearing all these languages which are new to me, "vim" "scheme" etc .. 

so basically my journey stats, i want to learn about linux administration "the structure of the OS and how to do simple troubleshooting without googling everything " and to become hopefully a linux/openSource efficient developer .. 

your input would be of great value everyone .. :KS

---

### Post by LaRoza on 2008-09-16
> **shift_00 said:**
> 
i've came to gather that it's constructed as such "python" "C" then some "perl" is a must .. but i keep hearing all these languages which are new to me, "vim" "scheme" etc .. 

so basically my journey stats, i want to learn about linux administration "the structure of the OS and how to do simple troubleshooting without googling everything " and to become hopefully a linux/openSource efficient developer .. 


System Administration: Shell and Unix tools (see my wiki under "shell"), [http://laroza77.wikidot.com/linux](http://laroza77.wikidot.com/linux)

Kernel hacking: C, Assembly

General Purpose: Python, Ruby (I prefer Python, but in this case I think it is largely up to what you know first. Python has more I think and is faster)

Vim is a text editor. The best text editor.

Scheme is a Lisp dialect that is very simple. It is great for writing other languages and for learning computer science. My wiki has Python, C, Scheme, and Assembly on it.

I recommend learning in that order usualy, but if you have experience, do whatever you feel like. My Learn to Program site (link in sig) has a language selector which you could try out. Might be useful.

---

### Post by shift_00 on 2008-09-16
and here we go, another great personal effort :D well i'm sure you are not short of them fellow programmers, but i'm offering you my time and effort, in my areas of experties, i would love to be a part of your wiki if needed ... :D 

again thanks for those great pages ..

---

### Post by LaRoza on 2008-09-16
> **shift_00 said:**
> and here we go, another great personal effort :D well i'm sure you are not short of them fellow programmers, but i'm offering you my time and effort, in my areas of experties, i would love to be a part of your wiki if needed ... :D 

again thanks for those great pages ..

Well, that wiki is my own personal wiki. For community efforts: [http://ubuntuprogramming.wikidot.com/](http://ubuntuprogramming.wikidot.com/)

---

### Post by nvteighen on 2008-09-17
> **shift_00 said:**
> well i would like to share with a bit background for all to see where i'm coming from, i'm a graduate computer science student, a developer by nature, has been working on scientific research for a while, and was a part time game developer for almost two years, languages that i use, c++, c#, java and matlab, but basically visual studio.net was my ide of choice, mainly because i wasn't exposed to the ideology or the philosophy of the open source community, and now that i'm in love with it, and having my ubuntu up and running, i have to ask my fellow programmers where to go and what to do .. in order to become an efficient member of this society (ie writing useful applications under linux ) 

Welcome! You'll enjoy your stay :)

> i've came to gather that it's constructed as such "python" "C" then some "perl" is a must .. but i keep hearing all these languages which are new to me, "vim" "scheme" etc ..

If you just want to have a "feel" of Scheme, look at this project of mine (it isn't usable in the end-user sense, but some library functions are working): [https://launchpad.net/freetruco/](https://launchpad.net/freetruco/)

And for a Common Lisp project (by our beloved Lisp-überhacker in the exile), look at this: [http://groups.google.com/group/symbolicweb](http://groups.google.com/group/symbolicweb)

> so basically my journey stats, i want to learn about linux administration "the structure of the OS and how to do simple troubleshooting without googling everything " and to become hopefully a linux/openSource efficient developer .. 

your input would be of great value everyone .. :KS

I'd start learning Python, as it's very popular at least in the Ubuntu world and increasingly in other distros. As you have programming experience, you'll need just a weekend. Check [http://diveintopython.org/](http://diveintopython.org/) (great tutorial for experienced programmers) and [http://python.org/doc/](http://python.org/doc/) (Python's official docs, also for experienced people... and a must).

Then, join a Free Software project which you like... it's amazing: you just come in and send out some code. And if it's good, the project managers will accept it; if not, well, there's always another chance.

---

### Post by shift_00 on 2008-09-17
Great :D i'm already starting my python through "thinking in python" for i have read the c++ 2 volumes and the java version of the book and for it is more inclined to design patterns but i'll give "dive into python" a read, but i wanted to ask of the mechanism of joining a free software .. i mean sourceforge is overewhelming for the untrained eye if you would agree .. :P

---

### Post by nvteighen on 2008-09-17
> **shift_00 said:**
> Great :D i'm already starting my python through "thinking in python" for i have read the c++ 2 volumes and the java version of the book and for it is more inclined to design patterns but i'll give "dive into python" a read, but i wanted to ask of the mechanism of joining a free software .. i mean sourceforge is overewhelming for the untrained eye if you would agree .. :P

Well, though Sourceforge seems to be the most popular choice, it has some slightly disturbing [TOS]("http://alexandria.wiki.sourceforge.net/Terms+of+Use") (see Section 6, Title "Your rights") that forces you to grant a proprietary license of your project to Sourceforge drivers so they can use your code however they want, in parallel to the Free License you use for the general public.

Ubuntu uses Launchpad ([https://launchpad.net](https://launchpad.net)), which is very easy to setup and also allows you to contribute in an easy way. 

For you to know, some people here (including myself) are developing a Free Software project in Launchpad ([https://launchpad.net/sysres](https://launchpad.net/sysres)). If you like it, join us! (As "mailing list", we're using this thread: [http://ubuntuforums.org/showthread.php?t=678665](http://ubuntuforums.org/showthread.php?t=678665))

Other services I know about are Google Code ([http://code.google.com](http://code.google.com)) or the GNU-sponsored Savannah ([http://savannah.gnu.org](http://savannah.gnu.org)).

---

### Post by LaRoza on 2008-09-17
> **nvteighen said:**
> 
For you to know, some people here (including myself) are developing a Free Software project in Launchpad ([https://launchpad.net/sysres](https://launchpad.net/sysres)). If you like it, join us! (As "mailing list", we're using this thread: [http://ubuntuforums.org/showthread.php?t=678665](http://ubuntuforums.org/showthread.php?t=678665))

Spam! :-)

Right now, we could use testers of 1.0 and trunk (don't judge the interfaces of trunk...they are probably broken) and we could use other help besides actual coding in case anyone doesn't feel they are ready to work with code.

To get the code, install bzr:

```

sudo aptitude install bzr

```

And take a branch:

For the latest code:
```

bzr branch lp:sysres sysres-trunk

```

For working on the next release (which needs testing):

```

bzr branch lp:sysres/1.0 sysres-1.0

```

(This will make a local branch for you, in the directories sysres-trunk or sysres-1.0)

---

### Post by pmasiar on 2008-09-17
> **shift_00 said:**
> in order to become an efficient member of this society (ie writing useful applications under linux ) 

i've came to gather that it's constructed as such "python" "C" then some "perl" is a must .. but i keep hearing all these languages which are new to me, "vim" "scheme" etc .. 

so basically my journey stats, i want to learn about linux administration "the structure of the OS and how to do simple troubleshooting without googling everything " and to become hopefully a linux/openSource efficient developer .. 

Vim and Emacs are two religions disguised as editors :-) it may take you weeks to learn either, so you may consider to start with some simpler editor: I prefer SciTE for almost anything, and works exactly  same on Windows too.

You may be tempted to become expert administrator, but it is not necessary to be certified sysadmin to be developer - just the opposite :-) With some tools, you will be surprised how little sysadmin knowledge you need to just squeak by. My universal tool of choice is Midnight Commander, I used it for 20 years and it allows you to do with kinda GUI interface 99% of the operations what experts do in commandline, without learning the commandline 8-) and it is character-based, and ssh tunnels even mouseclicks. 

Of course you need to learn how to install new programs - debian has about 19000 to chose from... :-)

Languages: Linux has embarrassment of riches: many interesting languages and projects, fiercely competing for attention of developers and stealing good ideas from other projects. As Linus Torvads said, it is evolution (survival of the fittest) not intelligent design 8-) 

You should try some dynamically typed language to see how programming can be 10 times more productive (and 100 times more fun) than C++, C# or Java. Perl is the classic, but Python is slowly overcoming Perl as 'standard' (it's oxymoron of course, there is nobody with authority to make any language 'standard' in world of Free Software). Ruby is another nice one, it's popularity based on excellent web app framework Rails (which ideas Python stole for Django and Turbogears 8-) )

Learn at least one dynamic language (learning others will be easy - ideas are almost the same, only quirks are different). Learn Lisp or Scheme to get some brain muscles if you want (irrelevant to any project), and then pick any project you want to add some feature, and dive in, using whatever language they use. Any project will be glad to have new developer on board - you may even try GameBaker in my sig :-)

---

### Post by LaRoza on 2008-09-17
> **pmasiar said:**
> Vim and Emacs are two religions disguised as editors :-) 

Vim is a cult; e**** is a religion.

> 
Languages: Linux has embarrassment of riches: many interesting languages and projects, fiercely competing for attention of developers and stealing good ideas from other projects. As Linus Torvads said, it is evolution (survival of the fittest) not intelligent design 8-) 

The only place it works because in biology it is survival of the luckiest (unless you wish to say that the 99.99 percent of all species who have ever existed who are now extinct are somehow inferior to what exists now)

---

### Post by CptPicard on 2008-09-17
> **LaRoza said:**
> (unless you wish to say that the 99.99 percent of all species who have ever existed who are now extinct are somehow inferior to what exists now)

-1, basic evolution misunderstanding. Fittest == "superior" only in terms of being more statistically likely to cause certain genes become more prevalent in some given environment. There is no progression from some objective, absolute inferiority to superiority implied.

---

### Post by LaRoza on 2008-09-17
> **CptPicard said:**
> -1, basic evolution misunderstanding. Fittest == "superior" only in terms of being more statistically likely to cause certain genes become more prevalent in some given environment. There is no progression from some objective, absolute inferiority to superiority implied.

Then why do they draw the diagrams with the less complex organisms at the bottom and the most at the top?

evolution is a very general concept with no specific theory. There are many theories and studies, but none of them form the basis for evolution as a concept. Evolution is so accepted because it must be true. How it works doesn't matter.

Of course, this is a discussion for another thread. It wouldn't get far anyway, because I focus on the individual theories whereas most people focus on the concept itself.

---

### Post by nvteighen on 2008-09-17
> **LaRoza said:**
> Spam! :-)

C'mon, the whole System Restore thread is spam...!

> **pmasiar said:**
> 
Learn Lisp or Scheme to get some brain muscles if you want (irrelevant to any project)

You're wrong. Lisp can be used for projects and Lars, and a bunch of projects are showing that.
[list]
[*]Savannah Common Lisp: [https://savannah.gnu.org/search/?words=Common+Lisp&type_of_search=soft&Search=Search&exact=1#options](https://savannah.gnu.org/search/?words=Common+Lisp&type_of_search=soft&Search=Search&exact=1#options)
Scheme: [https://savannah.gnu.org/search/?Search=Search&words=Scheme&type_of_search=soft&exact=1&max_rows=25&type=#options](https://savannah.gnu.org/search/?Search=Search&words=Scheme&type_of_search=soft&exact=1&max_rows=25&type=#options)
[*]Google Code Common Lisp: [http://code.google.com/hosting/search?q=%22Common+Lisp%22&projectsearch=Search+Projects](http://code.google.com/hosting/search?q=%22Common+Lisp%22&projectsearch=Search+Projects)
Scheme: [http://code.google.com/hosting/search?q=Scheme&projectsearch=Search+Projects](http://code.google.com/hosting/search?q=Scheme&projectsearch=Search+Projects)
[*]SF Common Lisp: [http://sourceforge.net/search/?words=Common+Lisp&type_of_search=soft&pmode=0&words=%22Common+Lisp%22&Search=Search](http://sourceforge.net/search/?words=Common+Lisp&type_of_search=soft&pmode=0&words=%22Common+Lisp%22&Search=Search)
Scheme: [http://sourceforge.net/search/?words=%22Common+Lisp%22&type_of_search=soft&pmode=0&words=%22Scheme%22&Search=Search](http://sourceforge.net/search/?words=%22Common+Lisp%22&type_of_search=soft&pmode=0&words=%22Scheme%22&Search=Search)
[*]Launchpad Common Lisp: [https://code.launchpad.net/projects/?text=Common+Lisp](https://code.launchpad.net/projects/?text=Common+Lisp)
Scheme: [https://code.launchpad.net/projects/+index?text=Scheme](https://code.launchpad.net/projects/+index?text=Scheme)
[/LIST]
Sure, it's not as popular as other languages, but they are there and I see no reason for considering not suitable for real work.

Unless I have misunderstood and you meant that "brain muscles" are irrelevant to projects (maybe because projects are written in Java?).

Please, could you clarify me your opinion?

---

### Post by LaRoza on 2008-09-17
> 
You're wrong. Lisp can be used for projects and Lars, and a bunch of projects are showing that.

Unless I have misunderstood and you meant that "brain muscles" are irrelevant to projects (maybe because projects are written in Java?).

Please, could you clarify me your opinion?

It sounds like a similiar thing to:
[quote=ESR]
Lisp is worth learning for the profound enlightenment experience you will have when you finally get it; that experience will make you a better programmer for the rest of your days, even if you never actually use Lisp itself a lot.
[/quote]

---

### Post by pmasiar on 2008-09-17
> **LaRoza said:**
> Then why do they draw the diagrams with the less complex organisms at the bottom and the most at the top?

For many species, becoming more complex improves chances to pass genes - in latest National Geographic is fascinating article about Neanderthals, who rules Europe for 200K years, and lost to Homo Sapiens because they were specialized to hunt big animals (women and children hunted too), while in H. sapiens tribes, women were gatherers - had different diversified strategy of survival by not hunting, which also induced more complex social relationships and language.

Of course other species have strategy to become simpler - like bacteria are substantially different and simpler than Eucaryots (animals and plants, human and banana, are close to each other, when compared with differences between bacteria species).

---

### Post by pmasiar on 2008-09-17
> **nvteighen said:**
> You're wrong. Lisp can be used for projects ...
Sure, it's not as popular as other languages, but they are there and I see no reason for considering not suitable for real work.

You are right, sorry, I should qualify that Lisp is good to know for "brain expanding" power, even if 99.9999% of projects uses other languages. My hunch is that emacs/xemacs are the biggest Lisp projects :-)

Lisp **can** be used for projects, but almost never is :-)

---

### Post by nvteighen on 2008-09-18
> **pmasiar said:**
> You are right, sorry, I should qualify that Lisp is good to know for "brain expanding" power, even if 99.9999% of projects uses other languages. My hunch is that emacs/xemacs are the biggest Lisp projects :-)

Lisp **can** be used for projects, but almost never is :-)

Then, we agree and it was just that I misunderstood what you meant.

I find it sad that only a few people out there use Lisp for the sake of innovation by research. I mean: I'm sure Lisp can be used for lots of projects, you just need to experiment on how to do it (and the spirit of the language, or better "Lisp-languages", allows you to play a lot with it).

---

### Post by shift_00 on 2008-09-18
well i "think" i familiarized myself with python but it's all theoratical .. 

let me propose something to this respectful community concerning newcomers of the developers ... i as a personal point of view can't possibly learn a language without putting a project as a goal to accomplish, a more practical way to get into a new language, well my proposal is for the well aquented ones with linux-related languages to post assignments, as a thread, i don't know if there is one already, but i think it will be a good thing to do .. 

assignments to be supervised in different categories, begginning the language "basics", scientific, web based, game development, shell programming and so and so forth ..

---

### Post by shift_00 on 2008-09-18
coz throught my readings i came to understand that python is good for anything a computer is good for .. and that's just too much .. and as a newcomer i'm looking for a more specific targets and a better way to search for projects ..

---

### Post by shift_00 on 2008-09-18
i mean count if you can, python, lua, ruby, perl. lisp, scheme, awk, shell, ncurses, assembly, C, and we know the list goes on and on .. 

what i'm proposing, is for someone to take few minutes, to draw a kinda of a plan with clear end results, and draw them walking through languages, and with assignments it would be assured of the expected outcome, and not too long into the process, and you will have linux programmers for all kinds of applications .. which is i think is what we need, but i feel a kind of intimidation which is good because it's not something easy to become, but as the zen states "find a master, follow the master, become the master" .. 

we need those to come out and give us wisdom, not just technical, but as of paths are concerned ..

---

### Post by pmasiar on 2008-09-19
did you bothered to read my wiki? It has exactly what you want.

---


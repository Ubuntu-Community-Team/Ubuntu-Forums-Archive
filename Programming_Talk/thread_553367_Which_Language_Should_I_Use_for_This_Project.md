---
title: "Which Language Should I Use for This Project?"
date: 2007-09-17
forum: Programming Talk
---

### Post by rendered_one on 2007-09-17
Hey everyone,

I'm looking at starting a programming project sometime this year and I am looking for some advice on where to start. Right now, specifically which language to start with. My idea is a church presentation software suite.

The main app I'm looking to develop is a media presentation app similar to that of EasyWorship or Media Shout. Obviously for Linux. I'm also looking into integrating OOo support for docs and presentations and gnome-sword for bible-study tasks. I'm looking at enhancing the capabilities of gnome-sword's means of message preparation and integrating that into the software, Synchronization of notes/service order/etc to a PDA. And some other minor features.

I have dabbled in C very lightly and have a bit to learn before I am going to take on this task, any help in getting started would be greatly appreciated.

Thanks and God bless,
-r1

---

### Post by Wybiral on 2007-09-17
Sounds like you'd benefit from a dynamic language with lots of standard libraries for all the media related content you'll be handling. I'd recommend Python.

---

### Post by rendered_one on 2007-09-17
Cool, thanks for the suggestion. Is Python an Object Oriented language?

---

### Post by yaustar on 2007-09-17
Yes, Python is OO. I would be tempted to try Mono with C# for an application like that.

---

### Post by rendered_one on 2007-09-17
Alright, I've heard of that as well, and I was looking at it a while ago. I'll have to keep that in mind too.

---

### Post by Nekiruhs on 2007-09-17
> **rendered_one said:**
> Cool, thanks for the suggestion. Is Python an Object Oriented language?
Python is really really cool in that aspect. Its a multi-paradigm language. It can be linear (BASIC), Functional (C), Object Oriented (C++), or a combination of them. I can have some linear code, followed by a class definition and some functional code. But its not Object Obsessed like Java where everything has to be an object and a method.

---

### Post by CptPicard on 2007-09-17
> **Nekiruhs said:**
> It can be linear (BASIC), Functional (C), ...

Slight correction, C is not a [functional programming language]("http://en.wikipedia.org/wiki/Functional_programming_language"). Lisp and Haskell are, for example.

I think the idea you're after is [structured programming]("http://en.wikipedia.org/wiki/Structured_programming"). C-style languages were a great improvement over BASIC in the more general field of [imperative programming]("http://en.wikipedia.org/wiki/Imperative_programming").

I would also like to refer the OP to my brand new CptPicard's Law that I have formulated tonight in response to a lot of recent threads. :) Your project looks a bit big for someone who has to ask for help in language choice :)

(joke warning)

And there is no divine intervention constant in the formula ;) ;)

---

### Post by Nekiruhs on 2007-09-17
> **CptPicard said:**
> Slight correction, C is not a [functional programming language]("http://en.wikipedia.org/wiki/Functional_programming_language"). Lisp and Haskell are, for example.

I think the idea you're after is [structured programming]("http://en.wikipedia.org/wiki/Structured_programming"). C-style languages were a great improvement over BASIC in the more general field of [imperative programming]("http://en.wikipedia.org/wiki/Imperative_programming").

I would also like to refer the OP to my brand new CptPicard's Law that I have formulated tonight in response to a lot of recent threads. :) Your project looks a bit big for someone who has to ask for help in language choice :)

(joke warning)

And there is no divine intervention constant in the formula ;) ;)
Thanks. I knew I had botched the wording. I thank you for correcting me.

---

### Post by rendered_one on 2007-09-17
> **CptPicard said:**
> Slight correction, C is not a [functional programming language]("http://en.wikipedia.org/wiki/Functional_programming_language"). Lisp and Haskell are, for example.

I think the idea you're after is [structured programming]("http://en.wikipedia.org/wiki/Structured_programming"). C-style languages were a great improvement over BASIC in the more general field of [imperative programming]("http://en.wikipedia.org/wiki/Imperative_programming").

I would also like to refer the OP to my brand new CptPicard's Law that I have formulated tonight in response to a lot of recent threads. :) Your project looks a bit big for someone who has to ask for help in language choice :)

(joke warning)

And there is no divine intervention constant in the formula ;) ;)

Oh I certainly agree, that is my hope for the program as a whole over a very long period of time. Every project has to start somewhere and I'm definitely not planning on building Rome in a day. ;) Actually, I'm hoping to start by creating the presentation app with the help of some friends of mine, one of which has created such an app for windoze. I hope to eventually turn it into a full fledged community project once I have gotten enough steam under it to realize the full potential of it.

But for now, I will simply read and code until I'm ready to start the project. :P Thanks for the 'joke warning' tho. :P
-r1

---

### Post by slavik on 2007-09-17
what type of presentation is this? Can you just create a Presentation in OO and use that?

---

### Post by mssever on 2007-09-18
I've been thinking about starting a similar project for some time, now. Unfortunately, other things keep taking priority. I do have some suggestions, though: There is at least one such Linux project out there already, [Lyricue]("http://www.adebenham.com/lyricue/"). It might do what you want. It's written in Perl (which is a huge drawback).

If I start such a project, I'll write it in either Ruby or Python. My preference is Ruby.

Here's what my idea is (we might be able to collaborate):[LIST]
[*]The core work is done by a server process that exposes a well-defined API and communicates via pipes and or the network. The key yere is strong encapsulation; that way it would be simple to attach varying front ends as desired. Plus, it's just better program structure.
[*]A GUI control program that connects to the server. The control program cannot change anything directly. It must talk to the server. This makes it possible to throw together a quick control program for development purposes, and refine it (or even replace or supplement it) later.
[*]The display program would initially be a CGI script that would use a web browser in full screen mode to display the lyrics. Opera would work for this out of the box, and Firefox would work with an appropriate extension. Of course, because of the modularity, it would be easy to add a different display program later.
[*]Because of the client/server architecture, it would be easy to distribute the system across multiple computers. Of course, you could just as easily do everything on a single machine.
[*]Also, because of the multiple processes, it would be easy to tailor the language to the function. (In fact, the browser display would require a fair amount of Javascript.) So if one component was easiest to write in Ruby, and another was better in Python, why not use both languages?
[*]The program(s) would be written in an OS-independent way, using the wxWidgets toolkit, so that our Windows and Mac friends could also benefit.[/LIST]These are just my ideas for what such a project would look like if I started it. Feel free to accept or reject them.

---

### Post by pmasiar on 2007-09-18
++ for slavik, and msserver: first reasonable suggestions: "what **exactly** do you want to do" and "looked around first" !

If your project fills some common need (at it looks it does), chances are very high that you are **not** the first developer having this exact problem. In fact, being first is as rare as for a biologist to find a new species :-)

So, decide what you want: 
- 100% web-based app? It will limit you GUI to what HTML does, and for more interactivity you need AJAX. But: you don;t have distribution problem.
- 100% desktop app? Do you need central server? Offline is good enough?
- mixed: custom desktop client communicating with central server?

For each option, Python is a very good choice, has frameworks and libraries to get you there, faster. But if existing project in Perl does 90% of what you want, you would be fool (or adventurer) to do it in Python. It also depends on project community: it it active and can help you to get last 10% (or even do it for you), or is it moribund and project is left to die or abandoned? If abandoned, where community moved to?

Of course, you can ask on original project if there are any forks/reimplements in Python. There might be someone silently working on it, and you can join. You will get battle-tested API and data design, opportunity not to be discarded lightly.

To give you valid advice, we need more info. "try C#" looks like advice from someone who uses C# or hammer for everything (like I use Python for almost everything :p )

---


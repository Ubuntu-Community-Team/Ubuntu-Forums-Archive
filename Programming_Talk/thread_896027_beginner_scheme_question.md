---
title: "beginner scheme question"
date: 2008-08-20
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-08-20
so im trying to look at basic scheme for the experience...only thing is i cant find out how to compile it...the only thing i have learned via google is that it uses something called a "listener"...how do i get one of these?

---

### Post by Kadrus on 2008-08-21
Check [Schemers.org]("http://www.schemers.org"),the [Scheme Wiki]("http://community.schemewiki.org/")..Read [SICP]("http://mitpress.mit.edu/sicp/").
> only thing is i cant find out how to compile it
What are you using? Check [PLT Scheme]("http://plt-scheme.org/") and read the documentation as well.
For questions,head to the scheme channel on freenode,and ask for help,you will get answered,either sooner or later..I'm on it as well.

---

### Post by jimi_hendrix on 2008-08-21
im not using anything...thats the problem...i googled how to compile scheme and got nothing so i thought i might as well ask here

---

### Post by Kadrus on 2008-08-21
Well Check the PLT scheme I gave you..and the wiki,you'll get your answers.

---

### Post by Jessehk on 2008-08-21
Look for Dr. Scheme. It's sole purpose is a learning environment for Scheme and it goes hand-in-hand with [this](http://www.htdp.org/) free book on Scheme.

I'm relatively sure there's a package for Dr. Scheme in the Ubuntu/Debian repositories.

---

### Post by Kadrus on 2008-08-21
Yeah,as Jessehk said,Dr.Scheme is included in PLT-Scheme.

"*It includes the DrScheme programming environment, a virtual machine with a just-in-time compiler, tools for creating stand-alone executables, the PLT Scheme web server, extensive libraries, documentation for both beginners and experts, and more*."

---

### Post by Tim Sharitt on 2008-08-21
> **Kadrus said:**
> Check [Schemers.org]("http://www.schemers.org"),the [Scheme Wiki]("http://community.schemewiki.org/")..Read [SICP]("http://mitpress.mit.edu/sicp/").

What are you using? Check [PLT Scheme]("http://plt-scheme.org/") and read the documentation as well.
For questions,head to the scheme channel on freenode,and ask for help,you will get answered,either sooner or later..I'm on it as well.

Good advise. The DrScheme environment at plt-scheme.org is also in the repos.

---

### Post by jimi_hendrix on 2008-08-21
stupid question that might be in the wiki: ive noticed DrScheme uses something kinda like the python interactive enviroment thing...is there a way i can type all of my commands in a text file and just have it read them and then do it like i would in C++?

---

### Post by CptPicard on 2008-08-21
It's the REPL... Read Eval Print Loop.

In DrScheme you have a text editor that doesn't evaluate immediately, you can then load code from that into the REPL.

Usually you can edit in any editor and then load the code into the environment using (load) or whatever. You should keep in mind that in lisps the REPL and the runtime environment is much more important and much more fun than in Python... you really *want* to be editing and executing snippets of code within the context of your existing other code that has been executed and produced results... it's a different development style.

---

### Post by jimi_hendrix on 2008-08-21
ahh im used to type, build, debug, make IDE stop screaming at me, look at what i did, change, repeat

---

### Post by nvteighen on 2008-08-21
Some sparse ideas.

1) Scheme is standardized (currently R5RS), but there are several implementations and each one adds their own extensions. As you come from C#, that might confuse you a bit... It's rather similar to what happens on C, where you have the standard but then each compiler gives you some extra features.

2) DrScheme is PLT Scheme, a very popular and usable implementation. Don't confuse the IDE with the implementation! DrScheme runs on top of MzScheme, a text-based listener you can use to run any Scheme file you created elsewhere.

3) DrScheme + MzScheme can be installed from the "drscheme" package in Ubuntu repos. You can also just install MzScheme alone ("mzscheme" package) if you want.

4) Usually Scheme is compiled to bytecode, not native binary. It's all you need. Scheme's (Lisp's?) beauty is on experimenting on-the-fly, IMHO, so compiling is just waste of time... Lisp is about executable data, your program is data that's evaluated to give a result. If you want a new result, change the data!

---

### Post by jimi_hendrix on 2008-08-21
ok cool...i probably wont understand the data thing for a while but when i do ill probably like it

---


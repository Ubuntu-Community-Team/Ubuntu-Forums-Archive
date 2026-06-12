---
title: "Scheme program in many files"
date: 2010-03-22
forum: Programming Talk
---

### Post by NovaAesa on 2010-03-22
Hi all,

Just as a heads-up warning, yes this is related to homework. I don't think the questions that I ask will get me into any trouble though, because the content isn't really about the homework itself...


I'm writing a project using scheme, but I'm having trouble trying to work out how to divide it into different files. I have done a little bit of scheme before, but it has only involved either typing into an interpreter directly, or tying into a text document and then pasting that into the interpreter.

Now, I'm thinking surely that isn't the way things should be done. There should be a way of grouping different procedures into different files right? But how to I actually then run them? I can run one of the files by typing "ypsilon filename.scm" into the terminal, but is there some kind of import that I can use to import procedures from other files?

---

### Post by CptPicard on 2010-03-22
> **NovaAesa said:**
> 
I'm writing a project using scheme, but I'm having trouble trying to work out how to divide it into different files.

Look up "include" and "require".

> 
 I have done a little bit of scheme before, but it has only involved either typing into an interpreter directly, or tying into a text document and then pasting that into the interpreter.

Gah... at least "load", or better yet, set up a proper "live" environment. Lisp really shouldn't be coded like that...

---

### Post by soltanis on 2010-03-22
Trollololol, Lisp development shouldn't be done with Scheme IMHO.

Yeah, "load" and "require" are probably what you're looking for to load scheme files into your current context.

---

### Post by NovaAesa on 2010-03-24
> **CptPicard said:**
> Look up "include" and "require".



Gah... at least "load", or better yet, set up a proper "live" environment. Lisp really shouldn't be coded like that...

I had a look into export and import (which I found in the standard), but I couldn't work out how to use them. I had a look at require and provide as well, but they seem to be plt-scheme specific (so I didn't look much further - I'd rather stick to the standard for now).

So I'm using the simple load at the moment, and it's doing what I want for now. I'll probably look into export/import or require/provide once I have finished this project (I don't have much spare time at the moment!). I'm liking scheme so much after doing half of this project that I might make it my language of choice in the future :P

What did you mean by "live" environment? I didn't turn anything up when I googled around... Feel free to give me some alternate search terms if that's easier than explaining what it means.

---

### Post by CptPicard on 2010-03-24
> **NovaAesa said:**
> I'd rather stick to the standard for now.

There's nothing evil in actually using the implementation you've got -- the Scheme standard defines so little stuff as a matter of principle that you're bound to have to resort to implementation-defined things. You can't really code "standard" Scheme. :)

> 
What did you mean by "live" environment? I didn't turn anything up when I googled around... Feel free to give me some alternate search terms if that's easier than explaining what it means.

I just made that up because I don't really have a better term for it. A lot of people code Scheme strangely because they assume it to work like other "compilers". At worst, they instantiate a new Scheme image ("session") every load and run cycle!

The idea is of course that you have a constantly "live" (for lack of better term) Scheme environment running, and preferably have a good editor hooked up to it so that you can have text buffers easily flushable into it and a better REPL than you get out of the box... that is the way it's intended to be used, and is quite different from anything else.

You may want to eventually look into Common Lisp, mind you... macros is where Lisp is at for real, and Scheme's macros are a bit of a mess according to many smart people... I haven't played with them nearly as much as I have CL macros so I don't really have an opinion of my own.

---


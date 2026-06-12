---
title: "Linux Native Development"
date: 2010-05-14
forum: Programming Talk
---

### Post by mwildam on 2010-05-14
As a discussion started in the launchpad bug #1 about number of developers for Linux should increase and good tools are missing, my question:

What is/are your choice(s) or recommendations to use for native Linux development?

Especially interesting would be the most easy language and tools (e.g. IDE) that could even a non-programmer give an easy way to find into programming world.

---

### Post by BoneKracker on 2010-05-14
As far as an IDE, I personally like to use Eclipse.  It is complete without being exceedingly bloated (it's what I'd call reluctantly bloated), it integrates most of the linux-native tools fairly well (debugger, GNU build system, alternative build systems, cross-compiling, etc.), it's a reasonably good editor, it supports most of the languages I like to work with, and it is truly a Bazaar (not Cathedral) project.

It's better to learn "native" Linux development at the command line, to truly gain an appreciation of each tool's power and alternatives that may not be offered by a given IDE.  One must first have mastered the shell.  This approach requires more mental visualization, rather than relying upon the visual cues of a graphical IDE, but it's really no more difficult, and it's frequently easier and almost always faster.

---

### Post by era86 on 2010-05-14
I use Eclipse for my work, but I hardly use any tools it provides.

My personal choice for development in Linux is to use the barest of tools: Gedit (with plugins), Terminal, Web Browser (with debug plugin).  This is assuming web development of course.

---

### Post by km0r3 on 2010-05-14
> **mwildam said:**
> As a discussion started in the launchpad bug #1 about number of developers for Linux should increase and good tools are missing, my question:

What is/are your choice(s) or recommendations to use for native Linux development?

Especially interesting would be the most easy language and tools (e.g. IDE) that could even a non-programmer give an easy way to find into programming world.

Could you please detail out what you mean with "Linux Native Development"? Talking about hacking the Kernel or Software Development *in* Linux in general?

---

### Post by splicerr on 2010-05-14
> **mwildam said:**
> As a discussion started in the launchpad bug #1 about number of developers for Linux should increase and good tools are missing, my question:

What is/are your choice(s) or recommendations to use for native Linux development?

Especially interesting would be the most easy language and tools (e.g. IDE) that could even a non-programmer give an easy way to find into programming world.

Good tools are missing? Ha! This must be a joke. I've found Linux with its rich choice of development tools and languages to be a far more friendlier development environment than Windows. Yes it's true there's no Visual Basic for Linux. But personally I think that's a good thing.  Do we really need these clowns?

---

### Post by foxmulder881 on 2010-05-14
Agreed with above. Who on earth told you it was short of dev tools? That's nuts! It's full of them.

Personally, I use Anjuta and Geany. Pretty much covers all my dev needs for work.

---

### Post by (&amp;*4h*)#$ on 2010-05-14
There are actually lots of tools for native Linux development. The particularly fun part of it is that there are many tools catering to many different types of developers.

The IDEs that I know of are Anjuta, Geany, KDevelop, Eclipse and Code::Blocks. I have tried them all at least ones. Some of them take a while to load, but if you're going to work on your project using these IDEs extensively, then working with these are good options.

There are also other developers (like me) who would prefer to work with the terminal and a simple text editor with syntax highlighting (gedit). I compile code using the command line, simply because a lot more options are exposed. Also, when I want to start coding, I don't have to wait for the IDE to load. Besides, I also get a lot more control over the files, since what I'm dealing with on the terminal is the actual organization of the files, not a fake layer of organization like some IDEs do.

In the end, it is still 'whatever floats your boat.' But I would not say that there is a lack of options.

---

### Post by foxmulder881 on 2010-05-15
> **Canis Major said:**
> The IDEs that I know of are Anjuta, Geany, KDevelop, Eclipse and Code::Blocks. I have tried them all at least ones. Some of them take a while to load, <snip> Also, when I want to start coding, I don't have to wait for the IDE to load.

What's with this comment?

On my system, Celeron D 3.06GHz 512 DDR ram:

Geany -- less than 2 secs
Anjuta -- 3 secs
Code::Blocks -- 6 secs

Hardly a long time to boot, even on a rather old system that I run.

---

### Post by (&amp;*4h*)#$ on 2010-05-16
> **foxmulder881 said:**
> What's with this comment?

On my system, Celeron D 3.06GHz 512 DDR ram:

Geany -- less than 2 secs
Anjuta -- 3 secs
Code::Blocks -- 6 secs

Hardly a long time to boot, even on a rather old system that I run.
I think I was referring to Eclipse and Netbeans on this one. Besides, based on your specifications, mine is a lot slower: I am on a 2Ghz computer with 1Gb RAM.

And as I have mentioned earlier, which might be much more important to me, is that I do not want to have to make another project, and have all the base code shoved up to me and have it organize my files when they aren't really organized that way on the directory structure.

In general, I enjoy not having an IDE because of the amount of transparency and control that I have. Of course I would not recommend this for rapid application development, for which it is understandable to use IDEs.

---


---
title: "Examples of your usage for various cmds"
date: 2012-02-20
forum: Programming Talk
---

### Post by satsujinka on 2012-02-20
Just because I can, I decided to see if I could finish off the goblin project.The goblin project is a re-implementation of the plan 9 user land in Go (awk, cat, echo, etc.)

I suppose I could do a straight translation from C to Go, but that's kind of boring and I am doing this for fun. (Plus if I write the code myself I can hand it out as public domain, which is how I prefer code to be.)

So the issue I have is this: I don't use most of the commands and thus have no idea how to use them (which means I have no conception of what it is I'm accomplishing by writing the command.) I do plenty of command line work, but I use only a handful of commands (I have also never felt the need to learn shell scripting, but that's besides the point.)

In particular, I want to know how you use (if you use them) the following commands:
awk
bc
dc
(probably sed too and anything else that uses patterns or is essentially a language all on it's own.)

So if you could provide me with examples (or scripts, though they'd have to be well documented since I never do shell scripting) I'd appreciate it.

---

### Post by Arndt on 2012-02-20
> **satsujinka said:**
> Just because I can, I decided to see if I could finish off the goblin project.The goblin project is a re-implementation of the plan 9 user land in Go (awk, cat, echo, etc.)

I suppose I could do a straight translation from C to Go, but that's kind of boring and I am doing this for fun. (Plus if I write the code myself I can hand it out as public domain, which is how I prefer code to be.)

So the issue I have is this: I don't use most of the commands and thus have no idea how to use them (which means I have no conception of what it is I'm accomplishing by writing the command.) I do plenty of command line work, but I use only a handful of commands (I have also never felt the need to learn shell scripting, but that's besides the point.)

In particular, I want to know how you use (if you use them) the following commands:
awk
bc
dc
(probably sed too and anything else that uses patterns or is essentially a language all on it's own.)

So if you could provide me with examples (or scripts, though they'd have to be well documented since I never do shell scripting) I'd appreciate it.

You want to implement awk and bc and dc but not look at the documentation for any of them? I must be misunderstanding something.

---

### Post by satsujinka on 2012-02-20
Not without docs, without code. I don't want to look at the code to do it, but looking an man pages or other docs are fine.

The problem I have is that a.) the docs are a little sparse on usage and b.) I don't truly understand what the goal of the commands are.

For example, cat has a very straight forward goal, concatenate files. echo also is very straight forward. 

awk, however, is much more general and I don't quite understand why you'd use it or for what. I want to clarify my understanding of the what and why so that the how follows naturally. 

bc and dc seem to mostly be useless in light of other means of calculating numbers, but if people still have uses for them then I'll be much happier when I write them.

---

### Post by Tony Flury on 2012-02-21
Awk is a very powerful text processing tool.

It general use case would be - you have an input file/stream and you want to process that file in some way. Assuming you can identify which lines you want to process - and can code how to process them, then you probably can write the processing in awk - and do it pretty succinctly too in many cases.

A good example of Awk usage is to transform output from one command into the suitable input of another. I used awk once to automagically take the output of a compiler and dop me into an editor with the first syntax error highlighted - and with suitable editor customisations I could step to the next error and so on. Awk allowed me to get the file name, line number etc from the compiler error message.

---

### Post by satsujinka on 2012-02-21
@Tony Flury
Thanks for the description. Could you give me the command(s) you used for that? Invocation is a pretty important part, so I want to understand that too.

@anyone
I guess what I'm really looking for is motivation, especially for dc and bc. If people are still using them then that makes their recreation all that much more important to me.

---


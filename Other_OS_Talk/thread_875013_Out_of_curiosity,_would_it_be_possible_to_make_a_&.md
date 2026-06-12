---
title: "Out of curiosity, would it be possible to make a &quot;multi-OS&quot;?"
date: 2008-07-30
forum: Other OS Talk
---

### Post by Fzang on 2008-07-30
Like, if you had the code and whatnot from windows, mac and linux, would it then be possible to create an OS that would be able to run all 3 types of software? :o

---

### Post by MaxIBoy on 2008-07-30
Fiendishly difficult, but theoretically possible. A better strategy would be to have only one OS but add compatibility layers (like WINE.)

---

### Post by cardinals_fan on 2008-07-30
As fairly powerful computers become common, you could probably virtualize two of the OSs seamlessly on top of the third...

---

### Post by Fzang on 2008-07-30
Hmmm... or OS X + VMware fusion?

...Is easily explained why it's going to be "fiendlishly hard"? I don't know much about creating OSs

---

### Post by knightcoder on 2008-07-30
Have to create layers for each type of OS since apps would still want the same interface they had with their appropriate OSes.

---

### Post by MaxIBoy on 2008-07-30
It would be fiendishly difficult to have three kernels in one for two reasons, in order of difficulty:
[LIST=1]
[*]Automatically detecting which kernel should be used to run a given program. This could be accomplished with MIME types.
[*]Multitasking. Allocating instruction space seamlessly to processes of different types. For instance, two OSs probably store programs (instructions) in RAM in different ways, with different types of metadata. I get a headache just thinking about it. This is especially true when you consider the way in which one OS might be mostly monolithic, while another might be mostly microkernel, and a third is some form of hybrid. Imagine this "multi-os" is a microkernal. Loading Windows programs requires adding extra code to use IPC, or fooling the Windows program into thinking that drivers and so forth are actually in the kernel. You could have three different protocols of IPC for three different OSs, each pretending to be communicating to a kernel instead of with other programs. However, this is basically just a compatibility layer anyway. So in order to create a *true* "multi-os," you need to add extra code to a program at runtime (ugh.) It's simpler just to port the code once, in a higher-level language.
[/LIST]

I hope that I don't sound *too* full of crap, I'm no expert at this either.

---

### Post by SunnyRabbiera on 2008-07-30
well its possible but would be very hard to do.
So far its possible to run a windows compatibility layer like wine but so far there is nothing that can run OSX software in linux.

---

### Post by maybeway36 on 2008-07-31
You can compile almost any app that runs on Linux to run on OSX (which is actually official UNIX as of Leopard.)

---

### Post by K.Mandla on 2008-07-31
It's apparently already possible to do that, in part.

[http://www.andlinux.org/](http://www.andlinux.org/)

Why anyone would want to is [beyond me]("http://kmandla.wordpress.com/2008/02/28/i-have-the-choice-and-i-still-dont-use-windows/"). :|

---


---
title: "Programs like OllyDBG in Linux?"
date: 2007-11-09
forum: Programming Talk
---

### Post by happysmileman on 2007-11-09
I'm interested in reverse engineering programs, and I tried several "challenges" on Windows with Olly (as in, here's a file, it'll ask you for a password and if you get it it'll say "Congratulations" or something pointless, but fun IMO, like that)

Are there any debuggers like Olly for Linux, I'd prefer GUI, being able to look through the full assembled program and make small changes, look through the stack and data and see what's in the registers, as well as obviously making breakpoints and going through instruction by instruction.

So I'm looking for a program that will allow me to do these things. I'm NOT looking for key-gens, cracks, warez or anything like that.

---

### Post by NathanB on 2007-11-09
Some of your options:

Linux Debug
[http://modest-proposals.com/Furball.htm](http://modest-proposals.com/Furball.htm)

Assembly Language Debugger (ALD)
[http://ald.sourceforge.net/](http://ald.sourceforge.net/)

Insight
[http://sources.redhat.com/insight/](http://sources.redhat.com/insight/)

Data Display Debugger (ddd)
[http://www.gnu.org/software/ddd](http://www.gnu.org/software/ddd)

KDbg (a KDE interface for dbg)
[http://www.kdbg.org/](http://www.kdbg.org/)

AsmBug (part of the AsmIde project)
[http://members.save-net.com/jko@save-net.com/asm/asmbug.htm](http://members.save-net.com/jko@save-net.com/asm/asmbug.htm)

Evan's Debugger
[http://freshmeat.net/projects/edebugger/](http://freshmeat.net/projects/edebugger/)

---

### Post by NathanB on 2007-11-09
> **happysmileman said:**
> I'm interested in reverse engineering programs, and I tried several "challenges" on Windows with Olly (as in, here's a file, it'll ask you for a password and if you get it it'll say "Congratulations" or something pointless, but fun IMO, like that)


Your mission, should you choose to accept it, is to "defuse" this nasty "binary bomb" planted on your machine by the Evil Interweb:

[http://www.pacificsites.com/~ccrayne/clax86/demobomb](http://www.pacificsites.com/~ccrayne/clax86/demobomb)

Threads talking about these and more examples are available here:

[http://groups.google.com/group/comp.lang.asm.x86/browse_frm/thread/335d21fc74d45701/](http://groups.google.com/group/comp.lang.asm.x86/browse_frm/thread/335d21fc74d45701/)

[http://groups.google.com/group/alt.lang.asm/browse_frm/thread/e49504764a4179a5/](http://groups.google.com/group/alt.lang.asm/browse_frm/thread/e49504764a4179a5/)

---

### Post by happysmileman on 2007-11-09
Thanks, I'll have to try some Sunday I think, any suggestions as to which of the above programs might be best suited?

---

### Post by NathanB on 2007-11-09
Well, the first listed is my favorite (it isn't graphical), but since "bombs" are typically written in C, you can sort-of "cheat" by building this monster:

UPS Debugger
[http://sourceforge.net/projects/ups/](http://sourceforge.net/projects/ups/)

Don't let its snotty X.org interface keep you up at night.  :)

---

### Post by happysmileman on 2007-11-10
Ok got Evans Debugger, seems pretty good, better in some ways to Olly, worse in others etc...

The bomb you gave me, was I supposed to figure out the password to get it not to explode? Or just change around some jumps?
I managed to do it by just entering in anything and changing 2 "JZ"s to "JNZ"s but I doubt that's what I was supposed to do.

Also any good tutorials for stuff like this anyone knows of?

EDIT: Also found out the way to get the strings anyway, I did manage to figure out that it took two numbers seperated by spaces but forgot all about it when i decided to change the jumps

---

### Post by NathanB on 2007-11-11
> **happysmileman said:**
> 
The bomb you gave me, was I supposed to figure out the password to get it not to explode?
Yes.
> 
Or just change around some jumps?

No.

I am sorry, but your original post...
> 
I'm interested in reverse engineering programs, and I tried several "challenges" on Windows with Olly (as in, here's a file, it'll ask you for a password and if you get it it'll say "Congratulations" or something pointless, but fun IMO, like that)

...gave me the impression that you already understand what these "bombs" are for and how to "defuse" them.

> 
Also any good tutorials for stuff like this anyone knows of?


You shouldn't need one (if you stand by your claims in your original post).  However, there are instructions here:

[http://www.cs.rpi.edu/~hollingd/comporg.2003/hw/hw3.html](http://www.cs.rpi.edu/~hollingd/comporg.2003/hw/hw3.html)

And others to be found via a carefully-worded Google search and there may also be more links available in those threads I posted earlier.

Hope I've helped.

---


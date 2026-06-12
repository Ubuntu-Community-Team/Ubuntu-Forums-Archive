---
title: "Code::Blocks -- What am I doing wrong?"
date: 2011-03-10
forum: Programming Talk
---

### Post by ve4cib on 2011-03-10
So I've just installed Code::Blocks on my Ubuntu 10.10-amd64 laptop and it's giving me nothing but headaches.  When idle it uses 60% of my CPU power, and it crashes when I...
- try to close it
- close a document within it
- edit code with it

I'm using C::B 10.05 off the Ubuntu repos.

After all the glowing reviews it seems to get from most everybody who uses it I'm convinced that the problem is with me or with my computer.  I've tried enabling/disabling all the various plugins with no success.  The end result is the same.

Anyone else ever run into these sorts of performance/usability issues with it?  If so, how did you fix it?

---

### Post by fct on 2011-03-11
Use the nightlies:

[http://apt.jenslody.de/](http://apt.jenslody.de/)

Last lines are the ones for sources.list.

---

### Post by TheBuzzSaw on 2011-03-11
That is indeed strange. Mine does not idle at such high usage. The only scenario that pops out in my mind would be that you are using a really old/slow processor, so 60% to you would be virtually nothing to everyone else. That assumption aside, there is definitely something wrong.

I use the nightlies, and they are great. Follow the link that fct posted.

---

### Post by ve4cib on 2011-03-11
My computer has a dual-core 1.6GHz processor so it's not exactly under-powered to run something like an IDE.

I've tried installing the nightlies and I'm still getting the same issues.  It hangs when trying to quit, and it's eating 60-61% of the CPU.  So the problem must be with something else on my machine.  Maybe I'll try reinstalling Fluxbox and running it under that to see if it's an issue with Gnome and/or Compiz.


EDIT:

Fluxbox install done.  Code::Blocks seems to be running much more smoothly now.  So obviously there's a panel applet or compiz plugin that's causing C::B to act so strangely.  Very peculiar.

---


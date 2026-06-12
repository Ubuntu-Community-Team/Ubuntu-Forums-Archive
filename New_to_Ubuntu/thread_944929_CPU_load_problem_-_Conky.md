---
title: "CPU load problem - Conky"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by NotLikingIt on 2008-10-11
Hi again
I have found this really cool reminder tool called "remind"

and I decided to make another conky for it to do nothing except 
${exec remind} so I can see it constantly

however, the problem also came with more fancy stuff I wanted to do with my linux

and the problem is

as soon as I loaded up my remind conky
the CPU load skyrocketed to 100% and it never dropped
even when I close firefox

then I looked at the processes shown on my other conky screen

Xorg was taking almost 60% of the CPU load to process my reminder conky (I know because as soon as I killed that conky process Xorg cpu& dropped to less than 10%)

is it because of something I'm doing in my conky?
Or is it because I'm using exec? Any suggestion as to what I can do to keep this reminder window ( that was the whole purpose of me getting remind 0.o...well, other than it feels cool with a text based tool like that)

I know I can always just open up another transparent (or semi transparent) terminal that only displays remind stuff

but I already used my apps file (I'm using fluxbox btw) to remember the position of my gnome terminal (as you can see the bottom right one) and xfce terminal on my desktop

Is there a way for me to do this without interfering what I already have?

Any help is appreciated thanks in advance

---

### Post by kerry_s on 2008-10-11
use "pre_exec" instead of "exec" for something that doesn't need to be checked constantly, use "execi" if you want it checked after a period of time.

example:
${pre_exec remind}
or
${execi 30 remind}

---


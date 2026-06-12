---
title: "ASCII history question on {} () []"
date: 2011-04-12
forum: Programming Talk
---

### Post by Jonas thomas on 2011-04-12
I'm working on this homework problem to balance out the 
curly braces, {};
parenthesis, ();
square brackets,[];
using the stl stack container.

I wanted to get Gucci and  save a few lines of code by adding +1 to find the opposite character. When I checked out the [ASCII codes]("http://en.wikipedia.org/wiki/ASCII") I found the following relationship.

'{'-'}'==-2
'['-']'==-2
'('-')'==-1

It seems most strange that the standard wouldn't have had a uniform difference in the values.  (personally I would a have made them all -1 if I were king)  Is there a reason that I'm not seeing why they did this?

I googled a bit but I found a bunch of ascii art (interesting yes, [but no answer]) ;(

---

### Post by krazyd on 2011-04-12
The short answer is that ASCII codes are an arbitrary historical artefact based on much standards-committee politics.

The long (33-page) answer is here:
[http://www.transbay.net/~enf/ascii/ascii.pdf](http://www.transbay.net/~enf/ascii/ascii.pdf)

---

### Post by Jonas thomas on 2011-04-13
> **krazyd said:**
> The short answer is that ASCII codes are an arbitrary historical artefact based on much standards-committee politics.

The long (33-page) answer is here:
[http://www.transbay.net/~enf/ascii/ascii.pdf](http://www.transbay.net/~enf/ascii/ascii.pdf)

Wow... that's a link... Everything you wanted to know about ASCII but where afraid to ask...  Looks like fun bedtime reading.
Thanks for the link.

---


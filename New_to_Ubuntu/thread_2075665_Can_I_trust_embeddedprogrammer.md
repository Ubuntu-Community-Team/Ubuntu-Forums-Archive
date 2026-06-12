---
title: "Can I trust embeddedprogrammer?"
date: 2012-10-24
forum: New to Ubuntu
---

### Post by OldNovice on 2012-10-24
My question is whether I can trust this source:

[http://embeddedprogrammer.blogspot.ie/2012/06/ubuntu-tip-02-octave-361-in-ubuntu-1204.html](http://embeddedprogrammer.blogspot.ie/2012/06/ubuntu-tip-02-octave-361-in-ubuntu-1204.html)

This appears to provide a solution to a problem
I have, and I would just like some reassurance from
the ubuntu community before downloading it.


I posted the question 4 weeks ago, but I guess I put
it in the wrong place on the Forum, or phrased the 
question wrongly.  A hundred or so
people looked at it, but no-one answered.
Here is a copy of
my original post:

I hope this is the right place to ask this.
 I'm using Ubuntu 12.04 LTS for the past week or so.
 I installed Octave using
 sudo apt-get install octave
 and it seems fine. It's version 3.2.4
 I also installed the GUI QtOctave, using the 
 software GUI at the top left, and it works, too,
 (although I just saw a post on another board that
 says its developer has dropped it and it's dead).

 The problem is that I want to use a package of functions
 from Octave-Forge, called Statistics. When I
 download this, and try to install it by running Octave
 and giving the command line
 pkg install statistics-1.1.3.tar.gz
 it complains that I haven't installed io
 When I download io from Octave-Forge and try
 to install it the same way, it complains that I need
 a more recent version of Octave, at least 3.4.

 This brings us to the nub. I seem to need either
 1) a (simple, safe) way to install Octave 3.4.1 or better
 (current version seems to be around 3.6.x)
 or
 2) a version of the statistics package (or maybe even the io 
 package) that will
 work with Octave 3.2.4

 Any suggestions would be most appreciated.

 Added:
 The following looks like a solution:
[http://embeddedprogrammer.blogspot.i...untu-1204.html](http://embeddedprogrammer.blogspot.i...untu-1204.html)
 But can I trust this PPA thing? 
 (Obviously, I'm grateful to any person who does this kind of work,
 and I'm not imputing anything to embeddedprogrammer,
 but I don't want my box to become a host for various horrors, so some
 reassurance from the community would be nice.)

---

### Post by danielbauwens on 2012-10-24
Yes, this is safe to use :)

EDIT: How do I know this? I tried it myself before.

---

### Post by OldNovice on 2012-10-27
Thanks, danielbauwens. 
I'll try it.

---


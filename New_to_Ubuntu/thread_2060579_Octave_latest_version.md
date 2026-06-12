---
title: "Octave latest version"
date: 2012-09-20
forum: New to Ubuntu
---

### Post by OldNovice on 2012-09-20
I hope this is the right place to ask this.
I'm using Ubuntu 12.04 LTS for the past week or so.
I installed Octave using
sudo apt-get install octave
and it seems fine.  It's version 3.2.4
I also installed the GUI QtOctave, using the 
software GUI at the top left, and it works, too,
(although I just saw a post on another board that
says its developer has dropped it and it's dead).

The problem is that I want to use a package of functions
from Octave-Forge, called Statistics.  When I
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
[http://embeddedprogrammer.blogspot.ie/2012/06/ubuntu-tip-02-octave-361-in-ubuntu-1204.html](http://embeddedprogrammer.blogspot.ie/2012/06/ubuntu-tip-02-octave-361-in-ubuntu-1204.html)
But can I trust this PPA thing?  
(Obviously, I'm grateful to any person who does this kind of work,
and I'm not imputing anything to embeddedprogrammer,
but I don't want my box to become a host for various horrors, so some
reassurance from the community would be nice.)

---

### Post by OldNovice on 2012-10-27
I posted the question elsewhere on the Forum and got an answer, so I'm marking it solved.
I installed the PPA and it seems fine.

---

### Post by newb85 on 2012-10-27
You're referring to this thread.
[http://ubuntuforums.org/showthread.php?p=12320803&highlight=octave#post12320803]("http://ubuntuforums.org/showthread.php?p=12320803&highlight=octave#post12320803")

You framed the question differently in the other thread, but it was still the same issue, so you should have kept the posts in one thread.

---

### Post by monkeybrain2012 on 2012-10-27
The octave package in the repository is hopelessly outdated. The current version is 3.6.X and we are still getting 3.2.X in the repo (and it will be that for the next 5 years if you use LTS) this is simply ridiculous if you are an octave user. Fortunately it is very easy to compile from source (see the octave site's instruction) qtoctave is dead and it won't work with later versions of octave. If you want a gui you can compile octave 3.7 from git, there is a gui coming with it, see attached screenshot (and the octave forge statistics package installs just fine)

---

### Post by OldNovice on 2012-10-27
Thanks for giving the link. I thought there would be some other way to cross-reference,
but this is the obvious way.
I apologise for splitting the topic across several threads.  I did it because there had been
no reponse for four weeks to my original query, and I supposed that I'd put it in the wrong
place.

---

### Post by OldNovice on 2012-10-27
Very good. Many thanks for this, mpnkeybrain.

---


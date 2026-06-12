---
title: "Accessing PHP::Serialization in perl"
date: 2008-01-23
forum: Programming Talk
---

### Post by Peter Howard on 2008-01-23
(Note: This is occuring on Gutsy)

A program I'm trying to build/use has a requirement for PHP::Serialization in some of its perl scripts.  A bit of searching turned up libdata-serializer-perl which seemed to have what I wanted.

However   . . .

It contains Data::Serializer::PHP::Serialization, rather than the PHP::Serialization being looked for.  If I produce a test script with a single line:

use Data::Serializer::PHP::Serialization;

It too complains about not being able to find PHP::Serialization (it wants to include it on /usr/share/perl5/Data/Serializer/PHP/Serialization.pm line 6)

So can anyone tell me what's going on?  For a package PHP::Serialization I'd expect to see something like /usr/share/perl5/PHP/Serialization.pm - which isn't there.  The man page for Data::Serializer refers to a man page for PHP::Serialization - which isn't there.

Is there another package which should be installed?

TIA

PJH

---

### Post by supirman on 2008-01-23
Here's an example of somebody using a few different serializers in perl: [Example]("http://www.ohmpie.com/serialization").

---

### Post by Peter Howard on 2008-01-23
> **supirman said:**
> Here's an example of somebody using a few different serializers in perl: [Example]("http://www.ohmpie.com/serialization").

The above link has an example which illustrates the problem.  If you go down the the heading "Serializing TestClass", it would fail on the "use PHP::Serialization;"

So back to the question - which package (given it ***isn't*** libdata-serializer-perl) puts in PHP::Serialization ?

PJH

---

### Post by supirman on 2008-01-24
You can install it via cpan:

```
sudo cpan install PHP::Serialization
```

---

### Post by Peter Howard on 2008-01-24
> **supirman said:**
> You can install it via cpan:

```
sudo cpan install PHP::Serialization
```

Sorry, I should have made something clear.  I want to have PHP::serialization installed via package.  I'd also like to understand why libdata-serializer-perl seemingly installs a not-fully-setup serialization library.

I'm trying to package up a new version of Zoneminder which now uses PHP::Serialization.  Hence the dependency needs to be satisfied by package.  So I should probably put this in the "Packaging and Compiling" forum as well.

---

### Post by The_night on 2008-04-10
Dunno if you ever got this answered but here is the package.

```
sudo apt-get install libdata-serializer-perl
```

---

### Post by jetole on 2008-08-19
Perhaps in 7.10 it was but in 8.04 it exists in libphp-serialization-perl

---

### Post by napster2500 on 2009-08-03
jetole is right, the package for versions above 8.04 is libphp-serialization-perl. (i'm using 9.04)
thank you for helping me "make" my zoneminder! :D

---


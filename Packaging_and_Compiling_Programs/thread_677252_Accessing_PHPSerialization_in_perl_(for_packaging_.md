---
title: "Accessing PHP::Serialization in perl (for packaging Zoneminder)"
date: 2008-01-24
forum: Packaging and Compiling Programs
---

### Post by Peter Howard on 2008-01-24
(Note: This is occuring on Gutsy)

I maintain the Zoneminder package.  The newest version (1.23) now uses PHP::Serialization in some of its perl scripts. A bit of searching turned up libdata-serializer-perl which seemed to contain it.

However . . .

It contains Data::Serializer::PHP::Serialization, rather than the PHP::Serialization being looked for. If I produce a test script with a single line:

use Data::Serializer::PHP::Serialization;

It too complains about not being able to find PHP::Serialization (it wants to include it on /usr/share/perl5/Data/Serializer/PHP/Serialization .pm line 6)

So can anyone tell me what's going on? For a package PHP::Serialization I'd expect to see something like /usr/share/perl5/PHP/Serialization.pm - which isn't there. The man page for Data::Serializer refers to a man page for PHP::Serialization - which isn't there.

Is there another package provides PHP::Serialization?

TIA

PJH

---

### Post by istergiou on 2008-02-03
Run:
perl -MCPAN -e 'install PHP::Serialization'
and answer the zillion questions.

---


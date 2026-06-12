---
title: "Porting program from LEDA-3.x and G++-2.8"
date: 2008-10-09
forum: Programming Talk
---

### Post by gholling on 2008-10-09
I have been trying to compile a graph decomposition utility from 1998 (tdecomp-0.9). 

[http://hein.roehrig.name/dipl/](http://hein.roehrig.name/dipl/)

The code is in C++ and was originally compiled with G++-2.8 and LEDA-3.x.  I have been trying to port the code to G++-4.2.3 and LEDA-6, and I have run into the following problem.

The code tries to do:

class result : public array<set<node> >
{
public:
  typedef array<set<node> > super;
...

It then uses the super keyword to refer to the base class.

I get the following error from the compiler:

pdc.h:226: error: ‘void leda::array<E>::set(int, const E&) [with E = leda::set<leda::node_struct*, leda::avl_tree>]’ cannot appear in a constant-expression
pdc.h:226: error: template argument 1 is invalid
pdc.h:226: error: expected unqualified-id before ‘>’ token

The compiler accepts this construct for base classes like array<int>.  Does anyone know a way around this?

Thank you for any help.

---


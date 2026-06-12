---
title: "Clueless geocacher looking for fortran compiler"
date: 2012-01-08
forum: New to Ubuntu
---

### Post by hyperheidi on 2012-01-08
Hi,
I'm not a programmer nor do I even know squat about fortran but was was given a geocaching puzzle to solve that requires fortran knowledge.  I have no idea what I'm looking at or how to trace my way through it.  I started my hunt looking for fortran compilers but I've gotten so lost I'm not sure its the right way to go.  I was looking for something like a "bablefish" online translator  or perhaps something small to download where I could cut and paste the code and it would provide me output.  Can someone plz direct me?  Thanks

Output should be a series of numbers vaguely like: 40 deg 45.123 min 111 deg 50.123 min

Here is one of my code snippets:

CHARACTER*22 C / 'Mary Had a Little Lamb' /
INTEGER N (15), M ( 3, 5 )
EQUIVALENCE ( M , N )
DATA ( ( M ( I , J ), J =1, 5 ), I = 1, 3) / 3,13,16,4,13,8,3,4,3,18,3,8,17,22,3 /

DO 1 J1 = 1, 15
K1 = N ( J1 )
M1 = ICHAR ( C ( K1:K1 ) )
1 N ( J1) = M1 - M1 / 10 * 10

WRITE ( *, 101 ) ( N ( I ) , I = 1 , 15)
101 FORMAT ( 1X, 2I1, ' Deg', 2X, 2I1, ' . ', 3I1, ' Min', 3X, ' - ', 3I1, ' Deg', 2X, 2I1, ' . ', 3I1, ' Min' )
STOP
END

---

### Post by lechien73 on 2012-01-08
Hi & welcome to the forums,

Ok...that's a bit of an odd request - even for here! I can't help you with an online "babelfish"-type translator for code, but the open source gfortran compiler is available for download from here: [http://gcc.gnu.org/wiki/GFortranBinaries](http://gcc.gnu.org/wiki/GFortranBinaries)

There's plenty of info in the wiki to get you started as well.

---

### Post by gsocker on 2012-01-08
GCC includes a fortran compiler. I'm not sure it's included in build-essential, though. Try searching for fortran in software center. The actual executable name is 'gfortran'.

Aside from that, I can't help as I'm not familiar with Fotran.

---


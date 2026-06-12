---
title: "use C++ test framework to test C?"
date: 2010-01-14
forum: Programming Talk
---

### Post by MadCow108 on 2010-01-14
I need to implement a testsuite to refactor some legacy C software.
And now I'm looking for a way which makes the least possible work.
Obviously I'm going to use a already existing unit test framework.

I was think about using a C++ framework and link it with g++ to the C code because C++ is just so much faster to write than C.
But is it a bad idea to use a C++ framework and link it with C code?
can this somehow produce an unreliable testsuite because of the different linker from the production code?
the compiler used will be gcc 3.4 with libraries from around that time.

Anyhow recommendations about which framework (C or C++) I should use are very welcome.
google test would be my first choice so far but it seems that the build dependencies of it are to new for the outdated build machine. I'll have to look into backporting it.
boost test has a lot of dependencies but should work. The documentation seems quite complicated, is it worth the time needed to learn it?
cppunit seems very verbose which I don't like, does it features make up for it?

of the C frameworks I have only looked at check. Looks quite nice but does not seem to have a lot of features and first tests made problems with valgrind. Any opinions on this one?

---


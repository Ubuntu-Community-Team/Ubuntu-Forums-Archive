---
title: "Makefile says always up to date"
date: 2009-06-17
forum: Programming Talk
---

### Post by kjohansen on 2009-06-17
I have this makefile 

```

legion.o: 
	g++ LEGION.h legion_glut.cpp -lglut -o legion.o
clean:
	rm legion.o

```

If I make a change to any of the files it still says legion.o is up to date...

---

### Post by Zugzwang on 2009-06-17
> **kjohansen said:**
> If I make a change to any of the files it still says legion.o is up to date...

Sure it does. You did not make the dependencies explicit:

```

legion.o: LEGION.h legion_glut.cpp
	g++ LEGION.h legion_glut.cpp -lglut -o legion.o
clean:
	rm legion.o

```

---

### Post by dwhitney67 on 2009-06-17
> **kjohansen said:**
> I have this makefile 

```

legion.o: 
	g++ LEGION.h legion_glut.cpp -lglut -o legion.o
clean:
	rm legion.o

```

If I make a change to any of the files it still says legion.o is up to date...

Zugzwang is correct; you need to list the dependencies.  There are cleaner ways to do this, but perhaps a little too advanced to discuss at this juncture.

One thing that needs to be cleaned up in the Makefile above is the proper specification of the CXXFLAGS, and the removal of the library 'glut' when compiling (it is not used).

Your Makefile (snippet) should look like:
```

CXXFLAGS = -Wall -pedantic -ansi -c

...

legion_glut.o: LEGION.h legion_glut.cpp
	$(CXX) $(CXXFLAGS) legion_glut.cpp

clean:
	$(RM) legion_glut.o

```
Notice that above I corrected the legion.o to be legion_glut.o, and also added the -c option so that the object file is generated.  Also, I replaced g++ and rm with pre-defined vars already known to make.

---

### Post by dwhitney67 on 2009-06-17
kjohansen -

You may want to take a look at this [post]("http://ubuntuforums.org/showpost.php?p=7472835&postcount=11") I just made in another thread.

---


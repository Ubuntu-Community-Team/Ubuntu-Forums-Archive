---
title: "iostream"
date: 2006-09-25
forum: Programming Talk
---

### Post by Dutchie90 on 2006-09-25
im using ubuntu for a few days now and i want to learn c++... im using the tutorial from [www.cplusplus.com](www.cplusplus.com) but i have a problem with that. when i compile an example from there my file doesn't start. i dont get any errors...

i tried this code
```

#include <iostream>
using namespace std;

int main ()
{
  cout << "Hello World!";
  return 0;
}

```

and i use this makefile
```

CPP = g++

all:
	$(CPP) cpp.cpp -o example $(OPTS)

clean:
	rm example

```

i also tried some examples from the irrlicht engine, and i saw that i could only start apps wich don't use iostream.
is there a solution for this?

---

### Post by Angry on 2006-09-25
> **Dutchie90 said:**
> 
```

<snip>
all:
	$(CPP) cpp.cpp -o example $(OPTS)
      ./example # refer to executable

</snip>

```


you'll need to tell the makefile to execute your program (see new line added to your "all").

(caveat: I am pretty new to makefiles myself, and I am also at work so I cannot double check my claim, but the provided line should work)

---

### Post by po0f on 2006-09-25
How are you trying to run your program?  And what are the error messages you are getting?

---

### Post by Dutchie90 on 2006-09-26
@angry -> that doesn't have to.. the thing compiles and just doesn't start...

@po0f -> im trying to run the program by double click the example executeable that the compiler makes. and i don't get any error, it just doesnt start

and what strange is, when i want to start an example of the irrlicht engine wich doesn't use iostream... it works, but the examples withouth dont work

---

### Post by thumper on 2006-09-26
See my post to your duplicate post :-)

In a nutshell, use the command line to run it.

---

### Post by Dutchie90 on 2006-09-26
if i type ./example it works :)
but how can i make it that it also works if i double click it?

---

### Post by moma on 2006-09-26
Your code is a console program. It has no GUI (user interface).
When you double click on the program name (eg. in Nautilus) it just runs quickly and exits. You will hardly notice it run.

It may be easier if you use an IDE (integrated Development Environment). My recommendations are:

Code::Blocks 
[http://codeblocks.org](http://codeblocks.org)  (+ [http://wxwidgets.org](http://wxwidgets.org) toolkit)

Anjuta (if you run GNOME)
[http://anjuta.org/](http://anjuta.org/)

KDevelop (if you run KDE)
[http://www.kdevelop.org/](http://www.kdevelop.org/)

These IDEs have ready-made templates for console (text mode) programs and many popular GUI toolkits.
-------------------------------------------------------

[http://cppreference.com/index.html](http://cppreference.com/index.html)
+
2 short c++ samples
[test-std1.cpp]("http://home.online.no/~osmoma//tmp/test-std1.cpp")
[test-std2.cpp]("http://home.online.no/~osmoma//tmp/test-std2.cpp")

---

### Post by Dutchie90 on 2006-09-26
thanks for those stuff :) it really helps :)

---


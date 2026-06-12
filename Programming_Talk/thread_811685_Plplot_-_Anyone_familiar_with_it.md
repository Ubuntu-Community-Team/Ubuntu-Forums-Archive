---
title: "Plplot - Anyone familiar with it?"
date: 2008-05-29
forum: Programming Talk
---

### Post by bernoulli on 2008-05-29
Hi. I've been trying to get to know Plplot ([http://plplot.sourceforge.net/](http://plplot.sourceforge.net/)) with C++, but I just can't seem to get my head around it. I can't see any help in the documentation.

Does anyone here have any experience with plplot with C++. Could you write a simple test program that draws a simple graph (or something).

---

### Post by bernoulli on 2008-05-29
I've tried this program:

```
#include <iostream>
#include "plplot/plplot.h"
#include "plplot/plstream.h"


using namespace std;

// g++ `pkg-config --cflags --libs plplotd` prog.cpp -o prog

int main(){

	// Make a simple function, y(x) = x^2
	int N = 100;
	double xmax = 5.0;
	double dx = xmax/(double)N;
	double x[N], y[N];
	x[0] = -xmax/2.0; y[0] = x[0]*x[0];
	for(int i=1; i<N; i++){
		x[i] = x[i-1] + dx;
		y[i] = x[i]*x[i];
	}
	
	// Try to draw the function
	plstream p = plstream();
	p.init();
	p.env(x[0],x[N-1],y[0],y[N-1],1, 0);
	p.line(N,x,y);
	p.end();
}

```

but it gets a problem with plstream. I get:
```
/usr/include/plplot/plstream.h:95: error: ‘plstream::plstream(const plstream&)’ is private

```

Now, I'm not even sure I'm on the right track here... Any suggestions?

---

### Post by Killercam on 2010-02-21
Yo Bernouli,
 
Dude, I am now also trying to get Plplot working and am having the same problems as you had. Did you manage to get it working? If so is there any way you could send me some information about how to compile your own simple program using C++, and perhaps a piece of example code - it is alway difficult without a basic initial e.g.!
 
All the best,
 
Nick

---

### Post by gmargo on 2010-02-21
Did you look at the examples in the **plplot** distribution?  I installed the **libplplot-dev** package, and in the directory **/usr/share/doc/libplplot9/examples**, there are 31 example programs each written in six different languages.

---

### Post by gmargo on 2010-02-21
I got your example to work by copying a bit from the first C++ example file (x01cc.cc) to add some "class":):

```

#include <iostream>
#include "plplot/plplot.h"
#include "plplot/plstream.h"

using namespace std;

// g++ `pkg-config --cflags --libs plplotd` prog.cpp -o prog

class x01cc
{
public:
   x01cc(int, char**);
   void plot1();

private:
   plstream *pls;
};

void x01cc::plot1()
{
        // Make a simple function, y(x) = x^2
        int N = 100;
        double xmax = 5.0;
        double dx = xmax/(double)N;
        double x[N], y[N];
        x[0] = -xmax/2.0; y[0] = x[0]*x[0];
        for(int i=1; i<N; i++){
                x[i] = x[i-1] + dx;
                y[i] = x[i]*x[i];
        }

        // Try to draw the function
        // plstream p = plstream();
        // pls->init();
        pls->env(x[0],x[N-1],y[0],y[N-1],1, 0);
        pls->line(N,x,y);
        // pls->end();
}

x01cc::x01cc( int argc, char **argv )
{
   pls = new plstream();
   
   // Parse and process command line arguments.
   pls->parseopts( &argc, argv, PL_PARSE_FULL );

   // Initialize plplot.
   pls->init();
   plot1();
   delete pls;
}

int main( int argc, char **argv )
{
   x01cc *x = new x01cc( argc, argv );
   delete x;
}


```

---

### Post by Choragos on 2010-04-08
Could you discuss a little about your compiler options please?  It's the stuff in quotes that confuses me.


Basically I cut and pasted your code and used your commented compiler directive in a makefile.  I'm trying to re-learn C++ (coming back from Fortran), so please be gentle on me...

Without the compiler directives in quotes, I get the following error while trying to compile your example:

```

mkass@munchen:~/Documents/development/plplottest$ make test
g++ test2.cpp -o test
test2.cpp: In constructor ‘x01cc::x01cc(int, char**)’:
test2.cpp:78: error: invalid conversion from ‘char**’ to ‘const char**’
test2.cpp:78: error:   initializing argument 2 of ‘int plstream::parseopts(int*, const char**, PLINT)’
make: *** [test] Error 1

```and with:
```

mkass@munchen:~/Documents/development/plplottest$ make test
g++ 'pkg-config --cflags --libs plplotd' test2.cpp -o test
g++: pkg-config --cflags --libs plplotd: No such file or directory
test2.cpp: In constructor ‘x01cc::x01cc(int, char**)’:
test2.cpp:78: error: invalid conversion from ‘char**’ to ‘const char**’
test2.cpp:78: error:   initializing argument 2 of ‘int plstream::parseopts(int*, const char**, PLINT)’
make: *** [test] Error 1

```Any thoughts?  The plplot tutorial online is ok, but it says nothing about what header files to include or how to appropriately compile...doesn't help that I'm an idiot.

Thanks a bunch!

---

### Post by gmargo on 2010-04-08
Those are not single quotes - they are backticks.  So that the output of the pkg-config command is placed on the g++ command line.

So where it says:
```

g++ `pkg-config --cflags --libs plplotd` prog.cpp -o prog

```After the expression in backticks, this becomes:
```

g++ -I/usr/include/plplot  -lplplotd -lltdl -ldl -lm -lcsirocsa -lcsironn -lqhull -lfreetype 
prog.cpp -o prog

```

---

### Post by Choragos on 2010-04-08
Ah, I see now.  So with a bit of modification, I could successfully compile and run x01.  I am still, however getting those errors I posted.  Any ideas where they are cropping up from?  The "violating" code is

```

  pls->parseopts( &argc, argv, PL_PARSE_FULL );

```

Since you said this worked for you and since I have no idea how PLPlot works I wanted to be cautious in how I mucked with your code.

I [we] appreciate the help.  Sorry for the pseudo-hijack, but I figured it was of general interest.  Once I get this figured out I'll put together a complete idiot's tutorial (who better to write that than a complete idiot?!).

The example x04 for C++ seems to be the simplest, just fyi.  It's at least the easiest to follow.

Thanks!

---

### Post by gmargo on 2010-04-08
The signature of the parseopts function is different for 9.10 Karmic, and there was an error in the pkg-config command line, so make sure you pick that up.  Here is code that compiles for Karmic.  I just tweaked a couple of "char **" to "const char **" and fixed the pkg-config line.

```

#include <iostream>
#include "plplot/plplot.h"
#include "plplot/plstream.h"

using namespace std;

// g++ `pkg-config --cflags --libs plplotd-c++` prog.cpp -o prog

class x01cc
{
public:
   x01cc(int, const char**);
   void plot1();

private:
   plstream *pls;
};

void x01cc::plot1()
{
        // Make a simple function, y(x) = x^2
        int N = 100;
        double xmax = 5.0;
        double dx = xmax/(double)N;
        double x[N], y[N];
        x[0] = -xmax/2.0; y[0] = x[0]*x[0];
        for(int i=1; i<N; i++){
                x[i] = x[i-1] + dx;
                y[i] = x[i]*x[i];
        }

        // Try to draw the function
        // plstream p = plstream();
        // pls->init();
        pls->env(x[0],x[N-1],y[0],y[N-1],1, 0);
        pls->line(N,x,y);
        // pls->end();
}

x01cc::x01cc( int argc, const char **argv )
{
   pls = new plstream();

   // Parse and process command line arguments.
   pls->parseopts( &argc, argv, PL_PARSE_FULL );

   // Initialize plplot.
   pls->init();
   plot1();
   delete pls;
}

int main( int argc, const char **argv )
{
   x01cc *x = new x01cc( argc, argv );
   delete x;
}


```

---

### Post by Choragos on 2010-04-09
ah ha!  thanks a bunch.  Had no idea.

---


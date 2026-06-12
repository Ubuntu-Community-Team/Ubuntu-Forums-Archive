---
title: "Cannot link a C++ program to plain C libraries (Ubuntu 17.04, G++ 6.3)"
date: 2017-07-06
forum: Programming Talk
---

### Post by frr2 on 2017-07-06
Dear polite inhabitants of the Ubuntu fora,

I'm an occasional hobby programmer... 

I have an old library written in GCC on Linux,
which I've been maintaining for maybe a decade
across the gradual developemnt of Linux distroes...
Unfortunately it happens to be considered an 
in-house project on my job, and I'm not allowed 
to publish it openly for some reason.

It's all very basic, running in the console,
I even wrote the thing in VIM 
and have a hand-written Makefile
- I mean to say that there's no complex IDE
between me and the compiler.

Most of the stuff is in C, but the "project"
also contains a program in simple C++.
In this single program, I'm #including
C headers from C++, and I need to link
some C libraries to the C++ "main() translation unit".
I'm using gcc to compile+link the C stuff,
and g++ to compile and link the C++ stuff.
All in one Makefile, it has worked like that for ages.

I've obviously learned years ago to use 
extern "C" {}  (I have that ifdef'ed in the .H files)
and I can try "using namespace std;"
or call functions prefixed with ::myfunc()
to get across some of the common pitfalls
of C/C++ hybridization.

I've just tested that the build works fine
in Debian 8.x Jessie (freshly updated) with GCC 4.9.2.

I have a remote friend/colleague, trying to build the software.
He's using  Ubuntu 17.04, with G++ 6.3. 
And, he's got linking errors.
When we started debugging today, he had the distro
about 3 months old. By now he's after apt-get update
and apt-get upgrade, which did not solve the problem.

When I run make, I get a flurry of happy messages
as the "plain C" translation units get compiled with gcc
and linked into a library (both .so and .a forms available).
But the make trace ends with approximately the following:

```

g++  -Wall -g -D_REENTRANT -fPIC  -c -o mb_read.o mb_read.cc
 g++ -o mb_read -L. -lmodbus -lpthread -lpcre mb_read.o
 mb_read.o: In function `regex_match(char*, char*, int, int*)':
 /home/xyz/Desktop/modbusRelay/linuxmodbus-0.4.3/mb_read.cc:71: undefined reference to `pcre_compile'
 /home/xyz/Desktop/modbusRelay/linuxmodbus-0.4.3/mb_read.cc:90: undefined reference to `pcre_exec'
 /home/xyz/Desktop/modbusRelay/linuxmodbus-0.4.3/mb_read.cc:118: undefined reference to `pcre_free'
 mb_read.o: In function `main':
 /home/xyz/Desktop/modbusRelay/linuxmodbus-0.4.3/mb_read.cc:685: undefined reference to `modbus_init'
 /home/xyz/Desktop/modbusRelay/linuxmodbus-0.4.3/mb_read.cc:692: undefined reference to `new_modbus_rtu'

```

The libmodbus.so/.a is my own library in the local directory, 
and libpcre.so is in some system-wide libdir.
Those are the two "plain C" libraries that I'm using.

So after the initial fumbling with 'extern "C" {}" and namespaces,
I realized that this is a linker error, rather than a compile-stage error.
And, that I seem to have all the known pitfalls just right.

I checked with "nm" that the relevant symbols of the "plain C"
functions are NOT decorated in the C++ main.o, and also 
that I can see them in the libraries just fine (tried all .so .a and .o).

I got rid of the -g and -fPIC just in case. To no avail.

I went on to strace the "g++ -o", to see that it does indeed
find all the libraries, and does open them (some positive 
descriptor number results for each library).

From there, I'm lost.
The "project" contains two other small examples that
are written in plain C, and are compiled with gcc.
These link just fine.

It would take me some time to produce a "smallest possible 
demonstrator for problem reproduction" and the computer
is even somewhat out of my reach... but maybe I could
scribble some "hello world" quickly, if desired.

So the question is... does any of this ring a bell?

The guy with Ubuntu seems to be using some
middle-eastern locale as a systemwide default.
Makes me wonder if that could be a problem...
The source text of my programs is in plain ASCII though,
and has always been.

Any ideas are welcome :-)

Frank

---

### Post by steeldriver on 2017-07-06
I suspect it's just a matter of link order:

```

g++ -o mb_read **mb_read.o** -L. -lmodbus -lpthread -lpcre 

```

The objects need to go from dependent to dependency (you may also need to swap pthread and pcre)

IIRC you may want to compile **and **link with the -pthread flag instead of explicitly linking libpthread

---

### Post by frr2 on 2017-07-06
@[**[COLOR=#DD4814][B]steeldriver**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1627500"):   :-) You know what?  Your diagnosis was spot on :-) Thank you!
Ahh yes, I can see your status...

I believe I've written this piece of software in RedHat 9, but the g++ linker line in the Makefile probably stems from earlier projects going as far back as maybe 2001 (RedHat 6.2).
I never stop learning. Thank you :-)

---

### Post by steeldriver on 2017-07-06
Glad to help ;)

I'm not sure when the GNU linker behavior changed - clearly it must have resolved these kinds of dependencies at some point since this gotcha comes up fairly often with legacy code

---


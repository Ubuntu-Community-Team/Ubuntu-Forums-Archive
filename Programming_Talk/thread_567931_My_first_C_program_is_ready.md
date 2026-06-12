---
title: "My first C program is ready"
date: 2007-10-05
forum: Programming Talk
---

### Post by scourge on 2007-10-05
It's an Xboard chess engine called Sloppy: [http://koti.mbnet.fi/~ilaripih/sloppy/](http://koti.mbnet.fi/~ilaripih/sloppy/)

Yeah, I shamelessly borrowed the style sheets from the Bluefish homepage.

Anyway, Sloppy is licensed under GPL 3 and is better than the default xboard engine (Gnuchess) in many ways:
- stronger
- doesn't lose on time in "x moves in y minutes" games
- doesn't crash when a game reaches 300 moves
- doesn't go crazy if the game ends up being a draw by the 50-move rule
- Displays the full principal variation. Useful for analyzing games.


What I'd like you to do is run a couple of tests (would you kindly ;) ). First you'll need to compile Sloppy, which is as easy as downloading the source code, entering the right folder and typing "make". Then please run Sloppy and enter the following commands:
- "bench" - this will run Sloppy's benchmark
- "divide 7" - runs the parallel perft test to depth 7
- "quit" - quits the program

Then you should dump the contents of your console here. It would also be helpful to know the OS and the CPU you have. On my Feisty 64-bit Core 2 Duo E6600 pc it looks like this:
```
Sloppy 0.1.0 by Ilari Pihlajisto

Build date: Oct  5 2007
Debugging level: 1
Optimized for 64-bit

Initializing...
  Found 2 CPUs
  Using "book in memory" book mode
  No opening book was found
  Book learning ON
  Hash table size: 36 MB
...Done

Type "help" to display a list of commands
White: bench
Running benchmark at search depth 8...
100% [========================]

Benchmark finished in 26.43 seconds.
Main nodes searched: 10298009
Quiescence nodes searched: 17290626
Total nodes per second: 1043640
Average branching factor: 2.72
Hash table hit rate: 12.35%
White: divide 7
0: a3 106743106
1: b3 133233975
0: c3 144074944
1: d3 227598692
1: f3 102021008
0: e3 306138410
1: g3 135987651
0: h3 106678423
1: a4 137077337
0: b4 134087476
1: c4 157756443
0: d4 269605599
0: f4 119614841
1: e4 309478263
0: g4 130293018
1: h4 138495290
0: Na3 120142144
1: Nc3 148527161
0: Nf3 147678554
1: Nh3 120669525
Perft(7): 3195901860 nodes.
Time: 12.89 seconds.
Processing speed: 247878838 nodes per second.
White: quit
```

The times and nodes per second values will be different, and the order of the moves in "divide" may also be. But the node counts, branching factor and hash table hit rate should be the same on every machine. The "divide" test uses all your cpus/cores, and the number before a move is the thread number that was used. So on a quad-core machine there should be threads 0 - 3, and they should get used somewhat evenly.

So the "divide" test should be a lot faster on multi-core systems, but "bench" shouldn't. Both of the tests should however get a great speed boost on 64-bit platforms.


Thanks for your help. If you want to play against Sloppy you should install Xboard: sudo apt-get install xboard.
Then something like: xboard -size Medium -fcp ./sloppy

---

### Post by engla on 2007-10-05
Cool "first" program :) Very nice. Hope all goes well. I don't dare to play against this thing.

Default make rule didn't work, because of either gcc version or arch-dependent options
```
gcc -std=gnu99 -c -Wall -pedantic -O3 -pipe -mtune=generic avltree.c -DAPP_NAME='"Sloppy"' -DDEBUG_LEVEL=1
avltree.c:1: error: bad value (generic) for -mtune= switch
make: *** [avltree.o] Fel 1
```
So I chose these options and it worked
```
$ make CFLAGS="-O2 -pipe"
gcc -std=gnu99 -c -Wall -pedantic -O2 -pipe avltree.c -DAPP_NAME='"Sloppy"' -DDEBUG_LEVEL=1
...
```
(-O2 is better than -O3 according to me. I didn't think about that you perhaps tried them both :)

My stats are in the sig, for this cozy ibook.
```

Sloppy 0.1.0 by Ilari Pihlajisto

Build date: Oct  5 2007
Debugging level: 1
Optimized for 32-bit

Initializing...
  Found 1 CPUs
  Using "book in memory" book mode
  No opening book was found
  Book learning ON
  Hash table size: 36 MB
...Done

Type "help" to display a list of commands
White: bench
Running benchmark at search depth 8...
100% [========================]

Benchmark finished in 163.31 seconds.
Main nodes searched: 10298009
Quiescence nodes searched: 17290626
Total nodes per second: 168931
Average branching factor: 2.72
Hash table hit rate: 12.35%
White: divide 7
0: a3 106743106
0: b3 133233975
0: c3 144074944
0: d3 227598692
0: e3 306138410
0: f3 102021008
0: g3 135987651
0: h3 106678423
0: a4 137077337
0: b4 134087476
0: c4 157756443
0: d4 269605599
0: e4 309478263
0: f4 119614841
0: g4 130293018
0: h4 138495290
0: Na3 120142144
0: Nc3 148527161
0: Nf3 147678554
0: Nh3 120669525
Perft(7): 3195901860 nodes.
Time: 256.05 seconds.
Processing speed: 12481700 nodes per second.
White: quit

```

---

### Post by scourge on 2007-10-05
> Cool "first" program  Very nice
Thanks. I had previous programming experience, just not in C.


> Default make rule didn't work, because of either gcc version or arch-dependent options

Okay, I changed the CFLAGS to -O2 -pipe.


Well, the numbers seem right. Now if I could get some multi-core and/or 64-bit reports...

---

### Post by scourge on 2007-10-05
> (-O2 is better than -O3 according to me. I didn't think about that you perhaps tried them both

Okay, I did some tests, and on my system O3 is definitely faster. But apparently O2 is generally recommended.

---

### Post by slavik on 2007-10-05
correction:
ansi c = c89
c99 = C with some C++ stuff (const, // for line comments, others)

---

### Post by scourge on 2007-10-06
> **slavik said:**
> correction:
ansi c = c89
c99 = C with some C++ stuff (const, // for line comments, others)

Thanks, that's fixed now. I knew what C99 is, just didn't realize it wasn't ANSI C.

---

### Post by slavik on 2007-10-06
> **scourge said:**
> Thanks, that's fixed now. I knew what C99 is, just didn't realize it wasn't ANSI C.
live and learn ... and then use Perl. :-P

---

### Post by hod139 on 2007-10-06
> **scourge said:**
> Thanks, that's fixed now. I knew what C99 is, just didn't realize it wasn't ANSI C.

It is ANSI C. It was adopted as an ANSI standard in March 2000.  [http://en.wikipedia.org/wiki/C_(programming_language)#C99]("http://en.wikipedia.org/wiki/C_%28programming_language%29#C99")

> **slavik said:**
> correction:
ansi c = c89
c99 = C with some C++ stuff (const, // for line comments, others)
This is just wrong.  Please read the wikipedia article.


EDIT: [Here it is]("http://www.nirvani.net.nyud.net:8090/docs/ansi_c.pdf") if you are interested

---

### Post by scourge on 2007-10-06
Interesting. There seems to be some confusion about this, and the Wikipedia article actually says about C89 that "this version of the language is often referred to as ANSI C...". It clearly says that C99 is an ANSI standard though.

> c99 = C with some C++ stuff (const, // for line comments, others)

How is const in C99 different from C89?

---

### Post by Compyx on 2007-10-06
> **scourge said:**
> Interesting. There seems to be some confusion about this, and the Wikipedia article actually says about C89 that "this version of the language is often referred to as ANSI C...". It clearly says that C99 is an ANSI standard though.

How is const in C99 different from C89?

It isn't. const is still a type qualifier, just like in C89/C90, it doesn't provide a constant like in C++.

Other additions to C99 include the declaration/definition of new types without starting a new block, ie:
```

for (int i = 0; i < 10; i++)

```

The are also variable length arrays, // comments and implicit int was removed (finally!).

One thing C99 isn't is 'C with some C++' thrown in'. It also isn't very generally implemented or accepted.

Google for 'n1256.pdf' to find the latest draft of the C99 standard if you want to learn more.

---

### Post by maddog39 on 2007-10-06
> **Compyx said:**
> It isn't. const is still a type qualifier, just like in C89/C90, it doesn't provide a constant like in C++.

Other additions to C99 include the declaration/definition of new types without starting a new block, ie:
```

for (int i = 0; i < 10; i++)

```The are also variable length arrays, // comments and implicit int was removed (finally!).

One thing C99 isn't is 'C with some C++' thrown in'. It also isn't very generally implemented or accepted.

Google for 'n1256.pdf' to find the latest draft of the C99 standard if you want to learn more.
I tried doing that once with gcc 4.1 and it gave me an error saying I couldn't do that. :/

---

### Post by slavik on 2007-10-06
> **scourge said:**
> Interesting. There seems to be some confusion about this, and the Wikipedia article actually says about C89 that "this version of the language is often referred to as ANSI C...". It clearly says that C99 is an ANSI standard though.



How is const in C99 different from C89?
I did not know const was in c89 :(

---

### Post by scourge on 2007-10-06
> I tried doing that once with gcc 4.1 and it gave me an error saying I couldn't do that. :/

You probably didn't give gcc the std=c99 or std=gnu99 argument.

I use C99 in my chess engine mainly because I need fixed-length integers and 64-bit integers.

---


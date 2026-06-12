---
title: "Wow, I didn't expect Linux to be this good at number-crunching"
date: 2005-06-26
forum: Programming Talk
---

### Post by scourge on 2005-06-26
I'm in the process of writing my first C program, which also is my first Linux-compatible app. It's a Winboard chess engine and it uses bitboards (64-bit integers) to represent the table. It's coming along nicely, and I've got move generating, alpha-beta search, material evaluation etc. working, so I thought I'd do a basic benchmark to see how fast it calculates the moves:

CPU: Athlon XP 2600+

Ubuntu Hoary:
-kernel 2.6.10-5-686
-gcc version 3.3.5
-calculates 1,80 million moves per second

Windows XP:
-Service Pack 2 installed
-gcc version 2.95.2
-calculates 1,48 million moves per second

I expected the test to run faster in Linux, but the difference is over 20%! Can that be right, or have I missed something? Most of the cpu cycles were spent doing bitwise operations with 64-bit integers ("unsigned long long" to be specific), so a 64-bit processor would probably be about twice as fast here.

If anyone wants, I can upload the source code somewhere. Before this project I had only programmed with Visual Basic, so be warned that there's probably a thousand things wrong with the code.

I'm already falling in love with C. Visual Basic was good, easy and fast for most of the apps I've written, but not this one because I need unsigned 64-bit integers, bitwise operators, and performance. VB has none of those things.

---

### Post by jcs296 on 2005-06-27
I have no really good idea why it would be faster in Linux than Ubuntu, except maybe gcc produces more efficient binaries on Linux, or perhaps there were more background processes running in Windows.  

I've written parts of a chess program myself (mine was in Java), except for various reasons it never got finished. The executable jar for my program (with source and documentation included) is available at [http://homepages.nyu.edu/~jcs296/samplecode.html#ChessProgram](http://homepages.nyu.edu/~jcs296/samplecode.html#ChessProgram), there's a link to download the jar there if you're interested.  I wouldn't mind seeing your source code if you don't mind, I'm trying to learn C and it would be fun to look at.  Good luck with the program,
Joe

---

### Post by scourge on 2005-06-27
Thanks, I'll take a look at your source code. How's the performance in your Java program? Isn't Java slow as heck for this kind of things?

I first wrote my chess program in VB. It used alpha-beta spiced up with MTD(f), transposition tables, killer heurestics, history heurestics, iterative deepening and some tricks of my own. On my Athlon 2600+ it searched 6 plys in about 10 seconds in midgame and calculated about 70000 moves per second. Now by using C as the programming language and bitboards as board representation my new engine searches to 6 plys in less than half second and 8 plys in about 5 seconds, and that's only with basic alpha-beta. Of course it helps that it only evaluates material at this point.

Okay, let me comment the source a little more and translate all the Finnish text into English, then I'll upload the source. Keep in mind that I'm a beginner with C also and my style is "write code first, think later", so it's a little sloppy and it's probably not a good idea to learn my coding style. But I think my program performs well where it counts because I really tried to optimize the use of bitboards. By using bitmasks and rotated bitboards for sliding pieces the moves for any kind of piece are generated in just a few cpu cycles.

I also used bitboards for other things than board representation. A move is just a 32-bit integer: the last 6 bits are the From square, the next 6 are the To square, next 3 are the moving piece, next 3 captured piece, next 3 promotion piece, and next 3 castling. The remaining 8 bits are ignored.

---

### Post by LordHunter317 on 2005-06-27
[QUOTE=scourge]
I expected the test to run faster in Linux, but the difference is over 20%! Can that be right, or have I missed something?[/quote]Look closer at your specifications, namely your compiler versions.

---

### Post by jcs296 on 2005-06-28
Well it sounds like your program is far more advanced than mine; I used bitboard but did loops for some of the move generation instead of rotated bitboards, and a more plain vanilla alpha-beta search.  Java is definitely not a language to use for a serious chess program; I just needed some experience writing a larger program in Java and thought it would be a good exercise.  So my source might not really be that useful given that yours is more advanced, but it's there if you're interested.

---

### Post by tread on 2005-06-28
Yep, for that substantial a difference I'd look at the compiler. Were you using gcc on windows too? That would be the only way to make the comparison I think.

---


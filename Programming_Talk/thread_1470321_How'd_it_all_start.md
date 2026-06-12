---
title: "How'd it all start?"
date: 2010-05-02
forum: Programming Talk
---

### Post by palz2015 on 2010-05-02
This might sound noobish, but when UNIX was first invented, and the applications for it, how did people make the first compiler? How did they type the code for it?:popcorn:

And how do you compile the first compiler :D

---

### Post by TheStatsMan on 2010-05-02
The first compilers were written in assembly.  [http://en.wikipedia.org/wiki/History_of_compiler_writing](http://en.wikipedia.org/wiki/History_of_compiler_writing)

---

### Post by mmix on 2010-05-02
[http://plan9.bell-labs.com/who/dmr/chist.html](http://plan9.bell-labs.com/who/dmr/chist.html)

---

### Post by dwhitney67 on 2010-05-02
Read the book of Genesis.  From there, try the wiki pages.

---

### Post by schauerlich on 2010-05-02
Compilers were written in assembly language. Assemblers were written in machine code. Machine code was written very tediously. :)

---

### Post by Compyx on 2010-05-03
[http://en.wikipedia.org/wiki/Bootstrapping_%28compilers%29]("http://en.wikipedia.org/wiki/Bootstrapping_%28compilers%29")

---

### Post by palz2015 on 2010-05-20
Oh, one other thing: How would you type the code for this compiler without an application (like vi, ed, nano)?

---

### Post by lisati on 2010-05-20
> **palz2015 said:**
> Oh, one other thing: How would you type the code for this compiler without an application (like vi, ed, nano)?

One way that I've heard of but not actually used myself is to work out everything by hand, then flick a bunch of switches on the computer's front panel.

---

### Post by nmaster on 2010-05-20
computers didn't always have a screen and a keyboard.  early computers would require you to flip switches in order to control bits.  you'd then move a big lever to load a particular bit sequence into a register.  

computers have moved a long way.  read the wikipedia pages to figure it out.  its very cool to think about how this was originally done.

---

### Post by nmccrina on 2010-05-20
All this talk of bits and machine language and levers makes me feel like a wimp for using Java :D

Also, [http://xkcd.com/378/]("http://xkcd.com/378/")

---

### Post by wmcbrine on 2010-05-20
> **neal.m.master said:**
> early computers would require you to flip switches in order to control bits.Switches?! Luxury! In my day, you [programmed a computer by rewiring it](http://en.wikipedia.org/wiki/ENIAC).

Actually that was a few decades before my day. But I did do some hand assembly for the ZX81 (i.e., write the program on paper in assembly, then look up the opcodes from a book, calculate the addresses (by hand), do a bit of hex-to-decimal (by hand), and finally POKE in the results).

---

### Post by nmaster on 2010-05-22
> **wmcbrine said:**
> Switches?! Luxury! In my day, you [programmed a computer by rewiring it]("http://en.wikipedia.org/wiki/ENIAC").

Actually that was a few decades before my day. But I did do some hand assembly for the ZX81 (i.e., write the program on paper in assembly, then look up the opcodes from a book, calculate the addresses (by hand), do a bit of hex-to-decimal (by hand), and finally POKE in the results).

I just had to do a project like that in my computer science class.  we built a virtual cpu in logisim.  its too bad most kids don't learn this kind of stuff unless they go to one of the better universities.

---

### Post by r-senior on 2010-05-24
Wires? Luxury! In my day all we 'ad were a few coloured beads and a stick!

Actually my first job was writing machine code for density measurement devices. There was no compiler to use, no operating system to code against, and, for some reason I can't recall, no assembler to help either. When I started the only output device was a buzzer, although we added a 40x2 LCD display on later models. The machine code was typed into a file, frequently disassembled to verify it and burned it into a succession of EPROMs.

Same principle as the much earlier methods of switches, punch-cards and so on: direct input of machine code. Humbling really, when you consider the legacy left by pioneers like Ritchie, Thompson, Kernighan et al.

---

### Post by KdotJ on 2010-05-24
> **neal.m.master said:**
> I just had to do a project like that in my computer science class.  we built a virtual cpu in logisim.  its too bad most kids don't learn this kind of stuff unless they go to one of the better universities.

At my university we used a program called CPUsim where you can simulate assembly language and see how the registers, stack and memory all do their jobs

---

### Post by simeon87 on 2010-05-24
In my days, we taught a mammoth to do computations for us... :P :guitar:

---

### Post by Krupski on 2010-05-24
> **palz2015 said:**
> This might sound noobish, but when UNIX was first invented, and the applications for it, how did people make the first compiler? How did they type the code for it?:popcorn:

And how do you compile the first compiler :D

"It" all started with toggle switches.

The first computer I ever built was an 8008 with 256 bytes of static ram, a video display generator chip and circuit ("borrowed" from the Don Lancaster TV Typewriter project) and toggle switches.

To program it, I entered the address and data by setting toggle switches - up for "1" and down for "0". 

I put opcodes and operands, branches and branch offsets into memory, byte by byte with toggle switches and a pushbutton.

After hours of work, pressing reset would run the program (if there was no mistake).

After three days of switches, mistakes, more switches and more mistakes (and gallons of iced tea plus bathroom visits), FINALLY pressing reset ran a WORKING program!!!

The uppercase letter "A" appeared on the CRT screen!

That is how it all started.

I would have almost sold my soul for a hex keypad back then...

---

### Post by Krupski on 2010-05-24
> **wmcbrine said:**
> Switches?! Luxury! In my day, you [programmed a computer by rewiring it](http://en.wikipedia.org/wiki/ENIAC).


I must admit that my first computer was more advanced than jumper wires and thousands of 12AU7 vacuum tubes. I bow down to you, sir! [IMG]http://three-dog.homelinux.com/phpBB3/images/smilies/the-man.gif[/IMG]

---

### Post by shawnhcorey on 2010-05-24
One of the first computers I used was a PDP-8/L.  To load the operating system, you entered the bootstrap program on the front panel by flipping switches.  Then you load the paper tape with the OS in the console teletype and flipped the run switch.  The OS loaded at 3 characters per second (CPS).  It took just over an hour to load.

The next computer was a Xerox 530 with punch cards and an eleven-platter removal disk.  The console was a 10 CPS teletype.  Luxury.

---

### Post by Krupski on 2010-05-24
> **shawnhcorey said:**
> One of the first computers I used was a PDP-8/L.  To load the operating system, you entered the bootstrap program on the front panel by flipping switches.  Then you load the paper tape with the OS in the console teletype and flipped the run switch.  The OS loaded at 3 characters per second (CPS).  It took just over an hour to load.

The next computer was a Xerox 530 with punch cards and an eleven-platter removal disk.  The console was a 10 CPS teletype.  Luxury.

My first luxury was an Anderson/Jacobson terminal. It was basically an IBM Selectric typewriter (complete with typeball!) and a serial port at 134.5 baud.

Typing sent out serial data, incoming serial data was printed on paper.

MUCH nicer that the lousy KSR-33 Teletype! :)

---

### Post by shawnhcorey on 2010-05-24
> **Krupski said:**
> MUCH nicer that the lousy KSR-33 Teletype! :)

_Anything_ is nicer that a noisy, $#@! teletype!

---

### Post by JwB Zoofware on 2010-05-24
Code by Charles Petzold is a really good read explaining computers from the ground up (not in a "IT For Dummies" way, but in a very technical, geek tantalizingly electrical engineering way). 

It shows how we went from wiring a few switches into different logic gates (along with circuit diagrams) and inputting machine code via control panels to more modern day concepts.

The sheer difficulty and tedium of what the earliest computer scientists and pioneers went through is astounding IMO and deserves a LOT of respect.

---

### Post by manzdagratiano on 2010-05-24
The CS kids in my college had a mandatory 'Compiler Design' class - sounded very enigmatic - I had the thought of taking it myself - but when they actually got to it, all my enthusiasm vanished away, since they used to be struggling with writing parse tables and the like to define rules; most hated it... I guess one would like it only when they know that the end product holds a purpose for them

---

### Post by TheUnwiseman on 2010-05-24
> **nmccrina said:**
> All this talk of bits and machine language and levers makes me feel like a wimp for using Java :D

Also, [http://xkcd.com/378/]("http://xkcd.com/378/")

Also, [http://xkcd.com/505/]("http://xkcd.com/505/")

---

### Post by nmccrina on 2010-05-24
> **TheUnwiseman said:**
> Also, [http://xkcd.com/505/]("http://xkcd.com/505/")

Wow, I had forgotten that one! It gets more epic every time I read it. :D

---

### Post by nmaster on 2010-05-25
we used MARS: [http://courses.missouristate.edu/KenVollmar/MARS/](http://courses.missouristate.edu/KenVollmar/MARS/)

we use patterson&hennessey with mips.  i think there is an arm version of the text also, but we stick with mips.

---


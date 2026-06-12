---
title: "programming in straight binary &amp; hex"
date: 2009-01-03
forum: Programming Talk
---

### Post by kavon89 on 2009-01-03
My computer science teacher likes to tell "war stories" about programming in the old days, and he went on about coding full programs in binary and hex...

Any of you ever spend long nights coding in binary or hex back in the day (or still today)? How is it done?

---

### Post by monkeyking on 2009-01-03
hehe, my old cs teacher used to do the same,
he even brought some old punch card used for sorting in the old days.

I don't think you can code directly in this low level format,
on your x86 box. I think you need to use assembler to execute it.
I mean load your hex/bin into a register.

---

### Post by melojo on 2009-01-03
If you guys are interested here is a game that uses a commands similiar to assembly to control simple robots and have them battle.  If you scroll down the page there are other games that do the same thing using assembly and different programming languages.  most of the links may not work but you should be able to do a google search and maybe find them.

I used to mess around with them.

---

### Post by pp. on 2009-01-03
> **kavon89 said:**
> Any of you ever spend long nights coding in binary or hex back in the day (or still today)? How is it done?

I'm not that old. What I did I think was in decimal numbers, on an hp programmable pocket calculator.

> **monkeyking said:**
> I don't think you can code directly in this low level format,
on your x86 box. I think you need to use assembler to execute it.
I mean load your hex/bin into a register.

You certainly can code in machine instructions, it just a bit tedious. The assember is not used to execute any programs, it's just there to convert your nice symbolic program into the half-bytes or whatever your processor fancies.

---

### Post by stroyan on 2009-01-03
I once did a little bit of direct binary coding with an HP 2100 series and a DEC PDP-10.  They actually have a full register of rocker switches that can be used to set specific values in to specific memory locations bit by bit.
The 2100 that I used had a paper tape to load a simple assembler.  But it required entering a boot instruction sequence by the rocker switches first.
The cast-off PDP-10 that I was experimenting with didn't even have a working tape reader attached.
I see that there are simulators for these old systems available at [http://simh.trailing-edge.com/](http://simh.trailing-edge.com/) .
Somehow I am not actually tempted to give them a try.
I guess I got my fill thirty years ago. ;-)

---

### Post by jimi_hendrix on 2009-01-03
is there a binary/hex compiler i can use and a tutorial i can learn this 1337 art in?

---

### Post by stroyan on 2009-01-03
There is a reason that people don't program in straight hex bytes.  It is ridiculously complicated.  If you really want to work in straight binary or hex then there is no compiler involved.  It is just you and a binary editor like hexer.  It is up to you to work with the instruction format.  You could work with a "bare metal" emulation of a simple system.

  Or you could work with executables within an OS like ubuntu.  You would start that on x86 ubuntu with "man elf" for the format of an executable file.
The "Intel® 64 and IA-32 Architectures Software Developer’s Manual Volume 2A: Instruction Set Reference" tells about the actual encoding of instructions as bit patterns.
You can find that at [http://www.intel.com/products/processor/manuals/](http://www.intel.com/products/processor/manuals/)
The actual details of linux system calls are spelled out in documents you would find at [http://refspecs.freestandards.org/lsb.shtml](http://refspecs.freestandards.org/lsb.shtml)

---

### Post by GoS_ on 2009-01-03
It was very relevant to program in binary/hex back when the programming was done on the computer's front panel.  These days programming in hex has no significant advantages (that I can think of) because you aren't communicating with the computer any more directly than you would be if you used assembly language.  If you wanted to program in hex I suppose you could just write programs in assembly and then translate the instructions to hex by hand :).  I don't know what tool you would use beyond that point though.  Interesting topic.

---

### Post by |{urse on 2009-01-03
if you would like to learn "easy" hla or High Level Assembly check this site out. If you are fairly used to C you will catch on quickly.

[http://webster.cs.ucr.edu/](http://webster.cs.ucr.edu/)

So far as programming in straight binary,isn't that something only an idiot savant can actually do from memory? sit down and code in 01?

---

### Post by pmasiar on 2009-01-03
> **jimi_hendrix said:**
> is there a binary/hex compiler i can use and a tutorial i can learn this 1337 art in?

no there is not - that was the whole point, you just edit a file in any octal (for PDP/11) or hexadecinal editor, using binary opcodes directly, basically doing the work which MASM does for you.

Or patch memory directly from panel - sadly computers don't have such panels anymore. :-)

---

### Post by kavon89 on 2009-01-04
Heh, controlling the memory with some switches on a panel? That is really neat, sort of wish I did that kind of stuff... and at the same time I imagine it required a lot more thinking to do something we consider simple now.

---

### Post by wmcbrine on 2009-01-04
I did it back in my ZX81 days -- wrote out programs in assembly language, on paper, looked up the opcodes from a book, and POKEd them into memory.

I was happy when I finally got an assembler, for my next computer. :D

---

### Post by jpkotta on 2009-01-04
I call it machine coding, because you are specifying the program in machine language.  I had to write a short program in machine code when I took an assembly class.  That was the only time I've ever had to.  There are almost always tools (assembler and disassembler) so that you don't have to work with machine language.

I once took a short course on SCSI.  The instructor was incredibly smart.  Years ago he was a programmer, and he wrote some things in machine code because the assembler didn't give him enough control.  He said you can't be sure that the assembler truly outputs one machine instruction for each op code.  I'd say that for any project of reasonable size, it's more worthwhile to write your own assembler that you can trust, if you're worried about such things.

---

### Post by pp. on 2009-01-04
> **|{urse said:**
> programming in straight binary,isn't that something only an idiot savant can actually do from memory? sit down and code in 01?

The "instruction sets" of all processors I studied were (a) somewhat limited in size and (b) kind of well structured. Hence, coding the correct verb was not usually an issue, and most assembly programmers knew those codes by heart. Determining the addresses in RAM of your functions, procedures and of the data your program was to process was much more challenging, especially if you had to insert a few instructions into your nearly complete program. As I said before, that was somewhat tedious.

> **jpkotta said:**
> he wrote some things in machine code because the assembler didn't give him enough control.  He said you can't be sure that the assembler truly outputs one machine instruction for each op code. 

I have never ever found an assembler which did not output exactly and in a 1:1 ratio those instructions I put into the program. Also, you could easily see what the assembler produced, and as I said above, most programmers knew the op codes anyway.

 The issue could possible exist in a cross assembly set-up, such as programming peripheral devices from within your program. You'd then have instructions for more than one kind of processor within the same program, and the assembler might not be equipped to cope with that.

---

### Post by mmix on 2009-01-04
you can do it.

[http://www.homebrewcpu.com/](http://www.homebrewcpu.com/)

---

### Post by rplantz on 2009-01-04
> **|{urse said:**
> So far as programming in straight binary,isn't that something only an idiot savant can actually do from memory? sit down and code in 01?

I worked in a physiology research lab in the 70s. We bought a Data General Nova 3. As I recall, the ROM boot module was $1,500 (in 1974 dollars). We couldn't afford it, so I learned to key in the boot loader from the front panel switches. Fortunately, it was only three instructions:
```

reset the disk
read one sector
jump to here

```
Resetting the disk set it to track 0, sector 0. That sector contained a boot program, which was read into memory. The last instruction in the program wrote over the "jump to here" instruction, replacing it with an instruction that jumped to the beginning of the newly loaded boot program.

It was common to reboot the computer several times a day, so I knew that program in binary by heart. Even had a couple of dreams about it.

We also had an old Wang desktop calculator in the lab. It was about the size today's desktop computers, but it only did +, -, *, and /. It had a card reader that read only one card at a time. It was only programmable in binary, using machine language. I once programmed it to compute sine functions. I don't recall how many hours it took me to write the program.

I'm a retired CS professor who used to tell some of these war stories. One of my war stories led to my realizing how old I am, and this was over 10 years ago. I was telling my students about the work I did designing part of the guidance system on the Gemini capsule. It was an analog design, not digital. One of my students said at the end of my story, "Wow, you worked on Gemini?!? My *grandfather* worked on it too." After a moment's pause, I realized that I really was old enough to be his grandfather. Sigh. Yes, I gave him the "A" he earned.

---

### Post by Krupski on 2009-01-04
> **kavon89 said:**
> My computer science teacher likes to tell "war stories" about programming in the old days, and he went on about coding full programs in binary and hex...

Any of you ever spend long nights coding in binary or hex back in the day (or still today)? How is it done?

My old "war story" is... way back in the late 1970's, a friend of mine and I built (wire-wrapped) a computer with a Z-80 cpu, a single chip static ram of 256 bytes and character generator circuit "borrowed" from a Don Lancaster TV Typewriter project.

The address and data bus was controlled with toggle switches. To program it, we had to look up opcodes, translate them into binary, flip the right switches up or down, then hit the "write" button to put it into RAM.

Then, increment the address counter switches and do the next one.

Branch offsets were especially fun to calculate (not!).

When all was finished, we hit the reset button and hopefully it would work.

Our first program was to put the letter ascii "A" on the TV screen.

It took 3 hot summer days of programming and gallons of iced tea to finally get it to work.

We flipped a coin and I won... meaning I got the "honor" of pressing the reset button.

The TV screen jumped and a bright letter "A" appeared in the upper left corner of the screen.

I jumped up and screamed "OH YEAH!!!" - we finally did it!

Nowadays, people click on icons and start whining when it doesn't work. Boo-hoo... try spending THREE DAYS to get a single letter on the screen.

THAT'S computing! And I was there! :D

(right around that same time, Bill Gates was playing with CP/M... and the Apple was a garage project... I missed the boat somewhere along the way).

-- Roger

---

### Post by Krupski on 2009-01-04
> **rplantz said:**
> I was telling my students about the work I did designing part of the guidance system on the Gemini capsule. It was an analog design, not digital. One of my students said at the end of my story, "Wow, you worked on Gemini?!? My *grandfather* worked on it too." After a moment's pause, I realized that I really was old enough to be his grandfather. Sigh. 

My dad (would be 83 if he were alive) was a tool & die maker and years ago he made some precision graphite rotary valves for the Bell Agena upper stage (used in Gemini docking tests). It's kinda neat to think that little parts my dad built are still in earth orbit today.

---

### Post by arvevans on 2009-01-04
Actually you can write an executable program using just the hex editor.  It gets complicated because you do have to make all the header stuff indicate that the program is executable, and so on.

Of course you do have to fully understand the abstraction layer(s) used on your computer because your new program will be probably run there, not directly by the CPU.

Writing the program itself is made somewhat easier than would have been in the "bad old days" because today you can use BIOS calls and avoid having to write all the low-level drivers yourself.

Yes, we used to do it that way in the old BC (Before Compiler) days.  Then along came Assemblers, followed by Macro Assemblers, and the world has not been the same since...thank goodness.

If you really want to do this level work, you can obtain one of the polular RISC computer chips from ATMEL, Advanced Micro Devices, and many others, and do the machine-level programming with a hex or octal editor, use a loader to install the program in CPU memory, and then re-boot the CPU to execute your new program.

---

### Post by Krupski on 2009-01-04
> **arvevans said:**
> Yes, we used to do it that way in the old BC (Before Compiler) days.  Then along came Assemblers, followed by Macro Assemblers, and the world has not been the same since...thank goodness.

I come from the "BK" days (before keyboards). When programming with toggle switches, even a hex keypad would have been heaven.

---

### Post by kavon89 on 2009-01-05
> **|{urse said:**
> So far as programming in straight binary,isn't that something only an idiot savant can actually do from memory? sit down and code in 01?

Well if you're pretty good at switching numbers from decimal to binary and vice versa you just remember the decimal numbers, not a sequence of 1s and 0s.

---

### Post by monkeyking on 2009-01-05
When I was studying cs we had a program we used for digital circuit simulation.

It was quite rewarding, we built our own simple cpu.
The first assignment was a one-step pipeline,
It was just about constructing the alu and checking opcodes in binary.
This was rather fun.
The next assignment was making a 5 or 6 step pipeline,
This was very difficult especially the forwarding, branch prediction and all that.
But it grew into a competition about who could contruct the fastest one.
It was allabout squezing everyting into the shortest circuirt.

I remember the trick was to use a carry look ahead adder instead of a ripple carry,

Ahhh these were the fun days.


The program we used doesn't exist anymore but anyone interested in this low-level stuff should try this low level stuff.
[http://en.wikipedia.org/wiki/Logic_simulation](http://en.wikipedia.org/wiki/Logic_simulation)
Also check this book, very recommended [http://books.google.dk/books?id=1lD9LZRcIZ8C&dq=Hennessy+and+Pattersons+%22Computer+Organization+and+Design%22.&printsec=frontcover&source=bl&ots=o5zWpdFdJx&sig=StTh9FW9l7pzW4gR-d2uCT_mM4c&hl=da&sa=X&oi=book_result&resnum=1&ct=result#PPR5,M1](http://books.google.dk/books?id=1lD9LZRcIZ8C&dq=Hennessy+and+Pattersons+%22Computer+Organization+and+Design%22.&printsec=frontcover&source=bl&ots=o5zWpdFdJx&sig=StTh9FW9l7pzW4gR-d2uCT_mM4c&hl=da&sa=X&oi=book_result&resnum=1&ct=result#PPR5,M1)
This is supposed to be better than this one
[http://www.amazon.co.uk/Structured-Computer-Organisation-Andrew-Tanenbaum/dp/0131485210](http://www.amazon.co.uk/Structured-Computer-Organisation-Andrew-Tanenbaum/dp/0131485210)


This was a one-semester course, the next semester was doing our own compiler with typechecking, and this could run on our own pipeline cpu.

This was a very thorough introduction to the world of bits and compilers.

---

### Post by pp. on 2009-01-05
> **kavon89 said:**
> Well if you're pretty good at switching numbers from decimal to binary and vice versa you just remember the decimal numbers, not a sequence of 1s and 0s.

Flamewar! Hexadecimal, not decimal, on account of the constant word length!

---

### Post by wmcbrine on 2009-01-05
Yeah, hexadecimal is a lot easier to convert to/from binary. That's its entire reason for being. Each hex character = four binary digits.

---

### Post by jon419 on 2009-01-06
> **monkeyking said:**
> When I was studying cs we had a program we used for digital circuit simulation.

It was quite rewarding, we built our own simple cpu.
The first assignment was a one-step pipeline,
It was just about constructing the alu and checking opcodes in binary.

The program we used doesn't exist anymore but anyone interested in this low-level stuff should try this low level stuff.
[http://en.wikipedia.org/wiki/Logic_simulation](http://en.wikipedia.org/wiki/Logic_simulation)


Not to Hijack this thread.  But we had the same course at the university I attended.  We used JLS to do all our circuit simulations: [http://www.cs.mtu.edu/~pop/jlsp/bin/JLS.html]("http://www.cs.mtu.edu/~pop/jlsp/bin/JLS.html")

The even have a library of completed circuits, including a one cycle and multi cycle MIPS.

---


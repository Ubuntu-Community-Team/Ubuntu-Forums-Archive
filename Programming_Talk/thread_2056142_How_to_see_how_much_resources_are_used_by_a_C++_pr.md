---
title: "How to see how much resources are used by a C++ prog"
date: 2012-09-10
forum: Programming Talk
---

### Post by layers on 2012-09-10
I have a C++ algorithm that manipulates a bunch of matrices in C++,  which I know can run on an Altera DE1 board (which has 8MB SDRAM, 512K  SRAM, and 4MB Flash). I want to put the program on an Arduino Uno (2KB  SDRAM, 1KB EEPROM, 32KB flash), but I am not sure if the Uno can take it  and run it (scared it will keep running out of memory).

What is the best way to check? Should I run the program on my computer and somehow follow the average memory it uses?

---

### Post by trent.josephsen on 2012-09-10
Umm... I'm confused. How exactly are you running a C++ program on a board without a microprocessor? Is the processor implemented in the FPGA (which seems likely)? Is it the same kind of processor the Arduino has (which seems unlikely)? Is it running standalone or under an RTOS of some sort?

With certain assumptions I'm tempted to call "reasonable", an FPGA-based solution may incur much less overhead than running a standard C++ program on an Arduino... but I have no idea what assumptions may be reasonable. More detail is required.

---

### Post by layers on 2012-09-10
Alright. I am currently doing it with Eclipse and an FPGA. Eclipse supports it. And the Arduino has a processor - ATMega328P.
I want to use an Arduino because my goal at the end is to drive a few motors, and I thought I don't need a whole FPGA.

Honestly, I don't exactly know what processor implementation is, and I don't need it. So far, with the FPGA, I have a program that compiles uploads on the device, and runs, waits for a cin from the Eclipse window and then with that string, it continues executing and displays on a VGA monitor (through the FPGA).

---

### Post by trent.josephsen on 2012-09-10
Well, without a whole lot more information about how the FPGA board is organized and programmed (programmed with its own firmware, not your software), it's going to be essentially impossible to predict the memory / resource usage of the end result, given that you're talking about a completely different platform.

Bottom line: Just try to run it and see what happens. Hardware is cheap.

---


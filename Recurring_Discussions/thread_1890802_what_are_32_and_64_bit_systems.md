---
title: "what are 32 and 64 bit systems?"
date: 2011-12-04
forum: Recurring Discussions
---

### Post by *^kyfds( on 2011-12-04
hi.

can someone explain to me what the difference is between 32 and 64 bit systems, and what (other than what contacts are) the bits are - are they digital, or physical contacts on a peice of hardware?

---

### Post by ubername on 2011-12-04
In a very brief nutshell:

They are digital bits; it tells you the size of the chunks of information that are pushed around the processor in your computer.

---

### Post by *^kyfds( on 2011-12-04
is the size of the bits difined by the make and model of the CPU?

or the OS?

---

### Post by BC59 on 2011-12-04
32 bits or 64 bits defines how much data the processor can handle in a single operation. Means that the 64-bit version is going to operate faster since it can handle more data.
In conclusion 64-bit is faster, but is hard to notice, and is recommended if your system supports it. 
On Ubuntu download page says "32 bit (recommended)", but that "recommended" means the user will deal with fewer issues, if he doesn't know all the technical details of his computer. 
From Pangolin 12.04 and after Ubuntu will promote 64-bit images. This means the 64-bit image will be selected by default for download. 
Until now, the 64-bit images weren't recommended due to the lack of multiarch support, but looks now the problem is solved.

---

### Post by overdrank on 2011-12-04
Moved to Recurring Discussions

---

### Post by click4851 on 2011-12-05
just to be clear, for the question(s) from post #3 

Yes and yes.

---

### Post by 3rdalbum on 2011-12-05
> **BC59 said:**
> 32 bits or 64 bits defines how much data the processor can handle in a single operation. Means that the 64-bit version is going to operate faster since it can handle more data.

It's more to do with the length of numbers. Certain mathematical operations used in compression and other intensive tasks require 64-bit numbers (these are more precise numbers; think of it as "more decimal places"). These numbers can be worked with on a 32-bit system, but it might take three operations to do a 64-bit sum on a 32-bit CPU, that only takes one operation on a 64-bit CPU.

So yes, for some things 64-bit is faster. Not all things. Also note that 64-bit systems can address more memory. A good analogy is this: If all phone numbers were four digits, you could only have 10,000 phone subscribers. If all phone numbers have eight digits, you can have a maximum of 100,000,000 phone subscribers.

It's the same with RAM - if you can only have 32-bit numbers, you can only address 4 GiB of RAM (in the real world, a little less). If you have 64-bit numbers, you can have vastly more than 4 GiB of RAM available.

Because the memory addresses held in RAM are larger, and the numbers take up more bits, there is more memory used on a 64-bit system. However if you do a lot of video editing and things like that, and you have 2 GiB of RAM or more, you definitely should use 64-bit.

Most CPUs are compatible. Wikipedia will tell you if your CPU model is 64-bit compatible. As an easy rule, for Intel CPUs, if it's a Core 2 or later it's 64-bit, except if it's an Atom. AMD CPUs generally have the numbers '64' in the names of their 64-bit CPUs. If it doesn't, check Wikipedia.

---

### Post by F.G. on 2011-12-05
ok, so my understanding, in agreement with most of the stuff people have written here it that it is the width of the system bus, and therefore defines the amount of addressable space (RAM) and also the size that instructions or bits of data. so an OS will need to be a 64 bit OS in order to use the 64 bit bus. a 32 bit OS will work on a 64 bit machine, because the chunks of data will fit, but a 64 bit OS will not work on a 32 bit machine as the instructions, etc are all too big.  the size of the system bus will also define the maximum integer that can be stored in a computer (you can actually make larger numbers but they have to be broken into bits).

---

### Post by 3rdalbum on 2011-12-06
> **F.G. said:**
> a 32 bit OS will work on a 64 bit machine, because the chunks of data will fit, but a 64 bit OS will not work on a 32 bit machine as the instructions, etc are all too big.

That's close enough, but actually it's because 64-bit OSes require 64-bit instructions. A 64-bit CPU has them, a 32-bit one doesn't. A 64-bit CPU also has 32-bit instructions so it can run 32-bit code. Still your explanation is an easy way to explain it to someone non-techie :-)

> the size of the system bus will also define the maximum integer that can be stored in a computer (you can actually make larger numbers but they have to be broken into bits).

Not just integers, but floating point numbers (numbers including a decimal point). That's why they talk about "precision" in numbers, and "double-precise" numbers

If you have some spare time and money I'd recommend you read the book "CODE" by Charles Petzold. It's a very enlightening book. Getting a bit old now (written before 64-bit CPUs reached desktop computers) but 99.99% of the book still applies, and it teaches you everything from "How do electrons move" to "How to build a logic gate", and counting in binary, and how computers actually perform calculations using logic gates... well worth looking at, even if you don't follow all the calculations or understand all the text (I didn't).

---


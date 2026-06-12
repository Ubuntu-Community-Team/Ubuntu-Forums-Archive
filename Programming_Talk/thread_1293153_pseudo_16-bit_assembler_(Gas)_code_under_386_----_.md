---
title: "pseudo 16-bit assembler (Gas) code under 386 ---- byte array indexing?"
date: 2009-10-16
forum: Programming Talk
---

### Post by isosi on 2009-10-16
Hi,

movb numbers+%dl, %al

this line gives error on compilation

Error: invalid sections for operation on `numbers' and `L0'

but decimal constant instead of "%dl" works good,

example: movb numbers+14, %al.

Is there another way to read byte by byte from array ?

the code is here :

*************************

 .section .data

numbers:                                                                      #These are the data items
 .byte 3,67,34,13,45,65,54,34,44,33,22,11,66,0
                                                                                                 # 0 is end of array
 .section .text

 .globl _start
_start:

 movb $0,%dl                                                             # index of array members
 movb numbers, %al                                            # load the first byte of numbers array to register %al
 movb %al, %bl                                                       # since this is the first item, %al (%eax) is the biggest
                                                                                            #
start_loop:                                                                 # start loop
 cmpb $0, %al                                                          # check to see if we&#8217;ve hit the end
 je loop_exit
 incb %dl                                                                      # (index + 1) of array
                                                                                            # load next value
 movb numbers+14, %al                                   # ---------------------------------------> how to get variable instead
                                                                                                           #of decimal constant 14?
                                                                    # movb numbers+%dl, %al    is not working
 cmpb %bl, %al                                                       # compare values
 jle start_loop                                                         # jump to loop beginning if the new
                                                                                            # one isn&#8217;t bigger
 movb %al, %bl                                                       # move the value as the largest
 jmp start_loop                                                        # jump to loop beginning
loop_exit:
                                                                                             # %bl (%ebx) is the status code for the exit system call
                                                                                             # and it already has the maximum number
 movb $1, %al                                                            #1 is the exit() syscall
 int $0x80

***************

the data is only bytes so i want to use only byte operation on them
not word (2 bytes ) or long (4bytes) or q (8 bytes).

---

### Post by NathanB on 2009-10-16
Simply use the LEA instruction to load the address of "numbers" into EBX and then use that as your index into the array.

---

### Post by isosi on 2009-10-16
ebx register is 32 bit long but i am interesting only on 8 bit long notation ;)  
and i was confused with "lea" documentation.

---

### Post by falconindy on 2009-10-16
If you want to read through an array byte by byte, just declare a loop the length of the array and step through it with a register used as a counter.

Apologies that this isn't in GAS (only familiar with NASM), but hopefully you'll get the idea...
```

section .data
   array   db    1, 2, 3, 4, 5, 6, 7, 8, 9, 0
   arrayLen   equ   $-array

section .text
   global _start

_start:
    sub   esi, esi
    mov   ebp, arrayLen

  readloop:
    mov   al, [array + esi]
    ; do stuff with the contents of al
    inc   esi
    cmp   esi, ebp
    jne   readloop
```

edit: hmm, upon refreshing my memory about GAS syntax, and re-reading your code, the above might not be as helpful as i first hoped...

---

### Post by NathanB on 2009-10-17
Hi isosi,

I seriously suggest you study the GAS examples available from this site:  [http://asm.sourceforge.net/resources.html#tutorials](http://asm.sourceforge.net/resources.html#tutorials)

A more extensive tutorial is available here:
[http://www.drpaulcarter.com/pcasm/index.php](http://www.drpaulcarter.com/pcasm/index.php)

I realize the trouble with tutorials is that they leave a lot of stuff unexplained.  Sometimes it is better to just read a good book on the subject.  Here are two suggestions:

Assembly Language Step By Step, for Linux!
[http://www.duntemann.com/assembly.htm](http://www.duntemann.com/assembly.htm)

The Art of Assembly Language Programming
[http://homepage.mac.com/randyhyde/webster.cs.ucr.edu/www.artofasm.com/index.html](http://homepage.mac.com/randyhyde/webster.cs.ucr.edu/www.artofasm.com/index.html)

If none of that proves helpful, please feel free to ask in this forum.

Nathan.

---

### Post by isosi on 2009-10-20
Thanks for response,
 to address byte in 32-bit or 64-bit system may be is not the best case ;)

I am thinking if it is possible to manipulate byte data in this example more clever way
using 32-bit or 64-bit long registers, than code example given in the first post?

**********

example to understand my point:

**********

If there is a ruler of 10cm so to find average length of 10 sticks from 9 to 10 cm
will be one way, and if there is a ruler 1 meter long, 
so to find average length of the same 10 sticks will be another way.

*** First way (10cm ruler):

 it is more convenient to measure every stick with 10cm ruler, and then sum up results,and divide from number of sticks.

now imagine the same algorithm with 1 meter ruler ;D No there should be more clever way.

*** Second way (1 meter ruler):

put 10 sticks one by one in a line, measure total length of
resulting line with 1 meter ruler and divide result from number of sticks.


***
of course i assume that to put sticks in line is more easy than to measure it with
10 cm ruler, and that to keep 10 sticks in line during measuring is not problem.

So in conclusion i think second way is much more better, faster (but less compact - 1 meter ruler :D ).
This way makes real useful use of 1m length ruler.

**********

Now return to cpu registers. Is there any way to do that with 64 bit length registers same way like with 1 meter ruler when dealing with data in byte length? 

Of course i understand that for fastest execution is one way,
for smallest memory use is another way, 
for smallest source code yet another way,
for smallest execution size another way and so on ... :)

---

### Post by falconindy on 2009-10-20
> **isosi said:**
> Now return to cpu registers. Is there any way to do that with 64 bit length registers same way like with 1 meter ruler when dealing with data in byte length?
There's multiple ways to refer to a single register in order to get a different length. However, you're fairly restricted.

Let's take a look at EAX (with my amazing ascii art skills)
```

32                16        8         0
|---------------EAX---------------|    32 bits
                   |-------AX-------|    16 bits
                   |--AH----|---AL--|     8 bits each
```
You've got finer grained access to the lower order bits of each register, but as larger registers became available and CPU power scaled up, the same accomodations were not made available for the higher order bits. RAX is available to access the entire length of a 64 bit register, but you have no ability to access bits 32 to 64 alone.

Your best bet is to throw the data into memory and use a pointer. In NASM, you can define, say, a quad word and use base + offset with a pointer type to look at a piece of it.
```
lea    edx, qwData
mov    al, byte ptr [edx]
```
The above would get you the first byte of the quadword 'qwData' in the AL register.

[s]I'm sure GAS has this functionality as well.[/s]
[This link](http://www.ibm.com/developerworks/library/l-gas-nasm.html) actually shows that pointers in GAS are insanely easy...

---

### Post by isosi on 2009-10-27
As time goes, the experience comes ;)

This IBM site is good, cool ;)  

But in another place I have found instruction that was looking for 
the code example in the first post. It is "xlat" or "xlatb".
[LEFT]As happy I was to found this so  sad I became to find out that they are old time dinosaurs, at least for Gas syntax. To found documentation for this instructions for Gas syntax was realy "Mission impossible" :D
[/LEFT]
So this is one story and next one is another story.

I was happy to find out that mov numbers, %rax  (64 bit notation) actually puts eight bytes (so eight numbers) in register %rax. So at last i get used all register length  and one memory read per 8 byte. So i save up 7 memory reads, but actually if it gives any benefit, it is hard to say? 
To get one number (byte) from register, will require some additional
bits operations (mask or use another technique); and in total, result  will be slower than just to put one byte in register from memory and compare with another (at least i think so). 

Actually it is good question which way faster:

8 x (memory (1 byte read) to register(8,16,32,64 bit ?) + compare operation)
or 
memory (8 byte read )to register(64bit) + 8 x (bit register operation + compare operation) ?

---

### Post by falconindy on 2009-10-28
> **isosi said:**
> Actually it is good question which way faster:

8 x (memory (1 byte read) to register(8,16,32,64 bit ?) + compare operation)
or 
memory (8 byte read )to register(64bit) + 8 x (bit register operation + compare operation) ?
The latter option is almost certainly going to be theoretically faster. Measurably faster? *shrug*

---


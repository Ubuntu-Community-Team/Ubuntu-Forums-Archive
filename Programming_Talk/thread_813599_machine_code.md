---
title: "machine code"
date: 2008-05-31
forum: Programming Talk
---

### Post by perillux on 2008-05-31
I want to learn a little machine coding, just for fun, maybe I can make a hello world program and I will be very happy :)

I mean pure machine code, not assembly, 1's and 0's is all I want to type.

I cannot find anything teaching me this on google.  Can anyone please point me in the right direction.

---

### Post by amingv on 2008-05-31
I believe machine code instructions are given directly to the processor (ie you can't fill a text file with 0s and 1s and expect it to run) and it's very tedious even for a trivial "Hello world" program, especially considering how advanced processors are now.
I don't think you'll find a guide so easily (if at all, though I might be wrong).

---

### Post by inportb on 2008-05-31
While it would be pretty impractical, it might be fun to make such a novelty program.

I would just use assembly language and let the assembler translate to machine code for me.

---

### Post by JupiterV2 on 2008-05-31
You want to learn binary?

Simple:

A bit = open (1) or closed(0)
A byte is made up of bits.

If we have an eight bit byte, then 1 byte might look like this:

00000000

Binary uses base 2 notation.
Each bit, starting from the right, represents 2 raised to a power multiplied by the bit.

So, if we took a the first four bits of a number 0100, we'd use the following to calculate it:

2^3 x 0 = 8 x 0 = 0
2^2 x 1 = 4 x 1 = 4
2^1 x 0 = 2 x 0 = 0
2^0 x 0 = 1 x 0 = 0

0100 = 4

Using a full 8 bit byte:

11111111

2^7 x 1 = 8 x 1 = 128
2^6 x 1 = 4 x 1 = 64
2^5 x 1 = 2 x 1 = 32
2^4 x 1 = 1 x 1 = 16
2^3 x 1 = 8 x 1 = 8
2^2 x 1 = 4 x 1 = 4
2^1 x 1 = 2 x 1 = 2
2^0 x 1 = 1 x 1 = 1

11111111 = 256

ASCII (I don't know the ISO standard off-hand) traditionally used only 7 bit bytes, so you could represent numbers 0-127 (unsigned).

The decimal numbers for the alphabet are the following:
65-70 == A-Z
97-122 == a-z

So if I wanted to represent "Hi" in binary, it might look like this:

2^6 x 1 = 4 x 1 = 64
2^5 x 1 = 2 x 0 = 32
2^4 x 1 = 1 x 0 = 16
2^3 x 1 = 8 x 1 = 8
2^2 x 1 = 4 x 0 = 4
2^1 x 1 = 2 x 0 = 2
2^0 x 1 = 1 x 0 = 1

2^6 x 1 = 4 x 1 = 64
2^5 x 1 = 2 x 1 = 32
2^4 x 1 = 1 x 0 = 16
2^3 x 1 = 8 x 1 = 8
2^2 x 1 = 4 x 0 = 4
2^1 x 1 = 2 x 0 = 2
2^0 x 1 = 1 x 1 = 1

10010000 = H
11010001 = i

Just a basic tutorial. For a more in depth explanation, just look up binary language.

Hope this helps.

EDIT: Binary can't be directly translated by any compiler or hardware that I've ever heard of. Binary is somewhat fictitious, it's just a way we can represent what it is the hardware is doing. It's a representation of "gates" that allow electrons to flow or not flow in a sense...It's like a picture. It's not the real thing and you can't make it real.

---

### Post by Wybiral on 2008-05-31
You can use a hex editor, but the problems is that you're also have to write an executable (they header and all the sections required by your program). Why don't you just learn assembly? The opcodes for assembly usually have a practically 1-to-1 relationship with the bytes in the machine code.

---

### Post by perillux on 2008-05-31
> Why don't you just learn assembly?

I might do that next... but the reason is because I don't really have a need for assembly or binary in the first place, I just feel like giving it a try for fun.  Anyway, how is it possible to actually enter the 1's and 0's into a program to make it executable?  the only way I see is what you said, use a hex editor, but then that's in hex, not binary.

---

### Post by Wybiral on 2008-05-31
> **perillux said:**
> I might do that next... but the reason is because I don't really have a need for assembly or binary in the first place, I just feel like giving it a try for fun.  Anyway, how is it possible to actually enter the 1's and 0's into a program to make it executable?  the only way I see is what you said, use a hex editor, but then that's in hex, not binary.

Yes, but the hex represents the binary. Why enter eight 0s and 1s when you can enter one hex value?

It looks like you're going at this backwards anyway, you have to understand what the bytes are doing to use the 1s and 0s, and you have to understand the opcodes to get why each byte does what it does... In essence, you have to learn assembly to do what you want anyway. Why not start there?

---

### Post by DavidBell on 2008-05-31
AFAIK a stream of individual 0's and 1's has no real meaning to a typical x86 cpu, because input is handled as a series of 32bit(**) wide 'words', but the full 32bit width comes in in a single clock cycle.

At the most basic level, all assemblers do is give these 32bit words names that are easy to remember, so 000100100010000100100010 might become JMP or MOV or ADD, or whatever.

So there's nothing to stop you writing your binary program as a series of 0/1s in a text editor, make a little program that converts your 0's and 1's into hex/32bit, and then put that into a .bin file, and then...... but really it's just an assembler in reverse.

DB

(** I'm assuming x86 takes 32 bit instructions, not sure though as I've never done x86 assembler, either way it wont be individual 0/1s - rather 8, 16, or 32 bit wide words/instructions)

---

### Post by heikaman on 2008-05-31
If you just want to get the opcode use the assembler, but if you really want to understand how it works and write machine code yourself (which is a very daunting process and should only be done for educational purposes) you need to google **x86 architecture** and **Encoding x86 instructions** or read a **Computer Architecture** book in general, and you still need to learn assembly :)

But since I really like this subject, I will give you a Very brief x86 encoding tutorial :) 

x86 instructions can range from 1 byte to 15 bytes long, an example for 1 byte instruction is the NOP (no operation instruction 10010000 or 0x90), in general/from a bird's eye view x86 instructions format looks like this:
```

bytes:          0,1,2,3             4,5               6             7              8,9,10,11          12,13,14,15
function:    prefix bytes    1/2bytes opcode	   reg/mem   scaled indexed        mem displacement       imm data
```

*Although this is 16 bytes long, the actual instruction can not exceed 15 bytes because some bytes are mutually exclusive.*

Now lets encode a simple x86 instruction "mov $0x8888 , %eax" :

Depending on the operands, memory addressing, and other stuff, the MOV instruction can vary, but here we want to move  a 2 byte immediate operand ( 0x8888 ) to register EAX which takes the following format:

```
opcode      w=0 8bit / w=1 16bit        eax      first byte     second byte(if w=1)
1011              1                     000       10001000        10001000
```

In binary:
10111000 10001000 10001000

In hex:
0xB8 0x88 0x88

Now comes the fun part, executing the instruction :) I will use this small C program to execute the instruction, and 
watch the results with gdb:

*Maybe there's an easier way to do this , but this is the only way I know of*

First the C program, which basically calls function run() which changes its own return address to the opcode to trick the
processor into executing our code (it's just like a buffer overflow):

[PHP]char opcode[]="\xB8\x88\x88";

void run(){
	long *ret;
	ret=&ret+2;    //return address on stack
	*ret=(long*)&opcode; //now run() will return to opcode
}

main(){
	run();
}[/PHP]

```
Compile with:

gcc mov.c -o mov -ggdb 
```

This is the complete gdb session:

[PHP]gdb mov			//run with gdb
(gdb) break run		//make a break point at run() function
(gdb) display /i $pc	//add a display to see the inst mnemonic
(gdb) run			//run the program
(gdb) nexti		// skip instructions until you see ret
(gdb) nexti
0x0804835e in run () at mov.c:7
0x804835e <run+26>:	ret		//this where function run() will return to the opcode address

(gdb) nexti
0x0804954c in opcode ()
1: x/i $pc
0x804954c <opcode>:	mov    $0x8888,%eax	 //Finally our hand coded instruction

(gdb) nexti  			//one more nexti to execute the instruction 

(gdb) info registers 		//dump registers
eax            0x8888	34952
ecx            0xbf877640	-1081641408
edx            0xbf877620	-1081641440[/PHP]

---

### Post by nvteighen on 2008-05-31
> **heikaman said:**
> 
[PHP]char opcode[]="\xB8\x88\x88";

void run(){
	long *ret;
	ret=&ret+2;    //return address on stack
	*ret=(long*)&opcode; //now run() will return to opcode
}

main(){
	run();
}[/PHP]

Dumb question: why ret=&ret + 2;? Why do you have to add 2 and precisely 2?

---

### Post by heikaman on 2008-05-31
> **nvteighen said:**
> Dumb question: why ret=&ret + 2;? Why do you have to add 2 and precisely 2?

Not dumb, but actually a very good question.

This is all just part of a typical function prologue when a function is called the arguments are pushed on the stack in reverse order, then the return address.
In the function body **EBP** is pushed on the stack, and space is reserved on the stack for the local variables (by subtracting from **ESP**) and then the local variables are pushed on the stack in the same order as they appear in the code.

For example for a function like this:

[PHP]
void func(int x , int y){
        int *temp;
}
[/PHP]

The stack frame will look like this:

```

**Low MEM**
[INDENT]temp //local variable
EBP // saved frame pointer
RET // return address
x
y[/INDENT]
**High MEM**

```

so incrementing the address of temp pointer gives you the address of the stuff that follow temp on the stack :)
[PHP]
temp=&temp;   //now temp points to the address of temp on the stack
temp++;      // now temp points to &EBP
temp++;      //now temp points to &RET (func return address)
*temp=&someaddr // changes func return address
[/PHP]

***Note**: because temp is a long* , temp++ increments temp with 4 bytes
so temp+=2 = temp+8bytes*

Here's another example:
[PHP]
void print(){
     printf("Hello\n");
}

void run(){
    long *ret;
    ret=&ret+2;          //return address on stack
    *ret=(long*)&print; //now run() will return to print
}

main(){
    run();
}  
[/PHP]

**compile** and run, this will actually print "Hello" and terminate with a segmentation fault :D

---

### Post by nvteighen on 2008-05-31
Thank you!

Playing around with different pointer types, I've noticed there's no difference in using long* or int*. Why, if long is twice an int?

This version won't segfault, just return 1. Hope you don't dislike my GNU-ish C style...
[PHP]
#include <stdio.h>
#include <stdlib.h>

void hello(void)
{
	printf("Hello!\n");
	exit(1);
}

void run(void)
{
    int *ret;
    ret = &ret + 2;    /*return address on stack*/
    *ret = (int *)&hello; /*now run() will return to hello*/
}

int main(void)
{
    run();

    return 0;
}[/PHP]

---

### Post by heikaman on 2008-05-31
> **nvteighen said:**
> Thank you!

Playing around with different pointer types, I've noticed there's no difference in using long* or int*. Why, if long is twice an int?

long and int are both 4 bytes :D 

[PHP]

main(){
    printf("int: %d bytes\n"\
    		"long: %d bytes\n"\
    		"long long: %d bytes\n" , sizeof(int), sizeof(long) , sizeof(long long));
}
output:

int: 4 bytes
long: 4 bytes
long long: 8 bytes
[/PHP]

so long is 32 bits 4 bytes, long long is 64 bits , 8 bytes.
I think it's machine-dependent but this is the minimum width specified since C99 standard
[http://en.wikipedia.org/wiki/Integer_(computer_science)#Data_type_names]("http://en.wikipedia.org/wiki/Integer_(computer_science)#Data_type_names")

> 
This version won't segfault, just return 1
```

void hello(void)
{
    printf("Hello!\n");
    exit(1);
}

```


It won't segfault because when run() returns to hello() instead of main() the stack is all missed up, run() was supposed to push EIP on the stack so that hello() can return to run() , but you call exit() anyway before hello() reaches the ret instruction :)

---

### Post by robheus on 2008-05-31
> **perillux said:**
> I want to learn a little machine coding, just for fun, maybe I can make a hello world program and I will be very happy :)

I mean pure machine code, not assembly, 1's and 0's is all I want to type.

I cannot find anything teaching me this on google.  Can anyone please point me in the right direction.

Writing a program like that is not done anymore nowadays.
You probably have heard about this about the 1st generation computers in the 40ies/50ies, when there wasn't even an assembler, and you had to manually enter the '0's and '1's on a panel.

Current computers have very large instruction sets, and the closest you can get to accessing the processor is using assembly language.

But instead of wanting to write a program in 0/1 for a real processor, why don't you look for a programmable processor **emulation**, or perhaps even an abstract [Turing machine](http://en.wikipedia.org/wiki/Turing_machine).

Edit: 
[Turing simulator(1)](http://sourceforge.net/projects/visualturing/)
[Turing simulator(2)](http://www.cheransoft.com/vturing/)

---

### Post by pmasiar on 2008-05-31
In Forth, it is pretty trivial to execute a binary sequence.

But for 'hello world' you need to handle output to terminal, which is asynchronous, byte per byte. Why would anyone with traces of sanity did that in binary? I know people  who could do that back in '80ies, but it is extreme amount of work (hours and days) for  trivial accomplishment.

Also, I do not understand why you want binary and reject hex (it is exactly the same, just more compressed: 4 binary digits are one hex digit), or why you reject ASM: one ASM statement translates directly to one binary statement, assembler just packs bits representing register number and instruction mnemonics into single binary value. Insisting on binary but not ASM is like insisting on running marathon, but with shoes one size smaller: distance is exactly the same, just more unnecessary pain. And this is also the reason why you cannot find the guide: nobody cares.

Programming in ASM is hard enough. Learn it first, then memorize opcodes, and you can program in bin. It is long-forgotten skill (and applicable for tiny programs only): people now instead build bigger, more complicated programs.

If you want to program closer to the metal, better way is not go binary, but learn Forth: do as close to the metal as you want to, where you want to, and build more complex functions on top of that.

---

### Post by Frak on 2008-05-31
Heh, binary. The only reason why you would take 3 months to write a hello world program ;)

But seriously, since processes from the processor to hardware are not burdened by human intervention, I would suggest downloading a Turing Machine to do some emulated programming.

---

### Post by perillux on 2008-05-31
guys, you keep giving me the same arguments: "no one codes like that anymore" yes I know this.  I'm not trying to become some leet coder that uses binary.

and I keep giving the same answer, I don't NEED to go this this low level of programming, I don't even need to go as far as assembly, HOWEVER, I would learn assembly just because it's challenging, but then, why not take it a step farther, and write a simple hello world program in binary
**just to say that I have done it** not trying to make any advanced OpenGL next gen PC games here.

Also, I'm not sure it would be all that difficult, I compiled a simple hello world program in assembly and opened it in a hex editor, and I noticed half of it was junk bytes at the end, so after removing all that this is the entire program:

```
7F 45 4C 46 01 01 01 00 00 00 00 00 00 00 00 00 02
00 03 00 01 00 00 00 80 80 04 08 34 00 00 00 FC 00
00 00 00 00 00 00 34 00 20 00 02 00 28 00 05 00 04
00 01 00 00 00 00 00 00 00 00 80 04 08 00 80 04 08
A2 00 00 00 A2 00 00 00 05 00 00 00 00 10 00 00 01
00 00 00 A4 00 00 00 A4 90 04 08 A4 90 04 08 0D 00
00 00 0D 00 00 00 06 00 00 00 00 10 00 00 00 00 00
00 00 00 00 00 00 00 00 00 B8 04 00 00 00 BB 01 00
00 00 B9 A4 90 04 08 BA 0D 00 00 00 CD 80 B8 01 00
00 00 BB 00 00 00 00 CD 80 00 00 [b]48 65 6C 6C 6F 20
77 6F 72 6C 64 21 0A[/b]
```

go ahead and try it, simply crate a blank file called "hello" open it with a hex editor and put all that in it, then save it, and give the file execute permissions an run it with ./hello in terminal, and you should see that it is a working program.
I don't know about you but this doesn't seem that daunting to me, considering everything in bold is simple the text to be printed.

Ever since I started programming years ago I've always wanted to do this, I want to learn just enough to be able to write a program, and then go straight through using only 1's and 0's (maybe I'll just do it in a text editor and then convert it to hex) and run the program and it says something.  Everyone always says "why on earth would u want to do that?" but the more I think about it, the more "do-able" it seems to become. (again, just talking about a simple "print 1 line of text to the terminal" program).

I might as well have posted this in the "off-topic" section of the forum, because it's not a necessity, it's just something I want to do, but I figure I'd get more programming savvy people if I posted here.

---

### Post by Wybiral on 2008-05-31
> **perillux said:**
> Also, I'm not sure it would be all that difficult, I compiled a simple hello world program in assembly and opened it in a hex editor, and I noticed half of it was junk bytes at the end, so after removing all that this is the entire program:

Yes, but you do have to keep in mind that the operating system needs that ELF header info to understand where things are in the executable. Writing an entire executable from scratch is no joke, but you can do it from assembly by writing the header info as inlined bytes in your program, I once wrote "hello world" in hex, and got it down to 92 bytes (beat that) most of which was just ELF header stuff (though I cheated for some of it): [http://davy.wybiral.googlepages.com/tinyHello](http://davy.wybiral.googlepages.com/tinyHello)

But, there's nothing "low level" about the binary. That's useless information. It's the hex values of the opcodes that matter. And even then, those ARE assembly, just not the verbal mnemonics.

---

### Post by perillux on 2008-05-31
ya, well, I guess I'll just go with assembly then.  Just had a sudden urge to do it in binary, but it's fading now lol

---

### Post by Lster on 2008-05-31
[QUOTE=heikaman]so long is 32 bits 4 bytes, long long is 64 bits , 8 bytes.[/QUOTE]

> int: 4 bytes
long: 8 bytes
long long: 8 bytes


That's on a 64 bit, though! :)

---


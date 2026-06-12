---
title: "Viewing RAM contents in realtime"
date: 2007-01-29
forum: Programming Talk
---

### Post by TheFuzzy0ne on 2007-01-29
Hi everyone.

Would someone mind telling me of a debugger I can use within Kubuntu that will allow me to read my RAM live and edit it?

I have seen lots of these for Windows, and the only one I can find for Linux is LDasm, which won't work with Kubuntu.

Many thanks.

Daz.

---

### Post by lnostdal on 2007-01-29
hm; i think you might be after GDB + maybe a frontend like DDD: [http://www.gnu.org/software/ddd/](http://www.gnu.org/software/ddd/)

---

### Post by TheFuzzy0ne on 2007-01-29
> **lnostdal said:**
> hm; i think you might be after GDB + maybe a frontend like DDD: [http://www.gnu.org/software/ddd/](http://www.gnu.org/software/ddd/)

Thanks for such a prompt reply. I had thought that originally, also, but naked GDB (with no front end) only appears to allow me to load a file, and not access the RAM directly. I tried XXGDB, and KGDB, both didn't seem to do what I wanted.

I have installed DDD, and it looks quite promising, although I am prompted to open a program when I want to attach the debugger to a process. I'm not quite sure why this is, as I am expecting to see a list of running processes when I click on the 'Attach to Process' menu option. I guess I should attach the debugger as the program starts rather than trying to attach it to an already running process as I am used to doing with Windows.

I will see how I get on.

Thanks again, my head ache is starting to feel so much better. :)

Daz.

---

### Post by TheFuzzy0ne on 2007-01-29
Crud!

I can't seem to get any input out of it. I tried attaching it to Firefox, and when I run it, Firefox exits. I also get the message: "no debugging symbols found". I don't have a clue what this means, but I still can't seem to find any way to actually view the content in RAM for a particular process. I guess I need to look into DGB a little deeper and learn how to use it.

Thanks again.

:)

---

### Post by Wybiral on 2007-01-29
It's not exactly the raw ram, but "/dev/mem" allows you to read/write system memory. Be careful though!

This little C++ program will create a dump of all of the visible characters in it...

```

#include <fstream>
#include <iostream>

using namespace std;

int main(int argc, char** argv)
{
   char c;
   unsigned long int offset=0;
   ifstream curFile("/dev/mem");
   ofstream fout("fileDump");
   while(!curFile.eof() && !curFile.fail())
   {
      curFile.get(c);
      if(c>31 && c<127)
      {
         fout.put(c);
         offset++;
      }
      if(offset==80)
      {
         fout.put('\n');
         offset=0;
      }
   }
   curFile.close();
   fout.close();
}

```

Compile it with "g++ whateverYouSaveItAs.cpp"

Execute it with "sudo ./a.out"

And the file "fileDump" will appear wherever you terminal is open to.

You can open it with a text editor and check it out.

Likewise you can write to /dev/mem... But like I said, be VERY careful and don't say I didn't warn you.

BTW, reading it should be pretty safe. I occasionally do for various reasons.

---

### Post by TheFuzzy0ne on 2007-01-29
> **Wybiral said:**
> It's not exactly the raw ram, but "/dev/mem" allows you to read/write system memory. Be careful though!

This little C++ program will create a dump of all of the visible characters in it...

```

#include <fstream>
#include <iostream>

using namespace std;

int main(int argc, char** argv)
{
   char c;
   unsigned long int offset=0;
   ifstream curFile("/dev/mem");
   ofstream fout("fileDump");
   while(!curFile.eof() && !curFile.fail())
   {
      curFile.get(c);
      if(c>31 && c<127)
      {
         fout.put(c);
         offset++;
      }
      if(offset==80)
      {
         fout.put('\n');
         offset=0;
      }
   }
   curFile.close();
   fout.close();
}

```

Compile it with "g++ whateverYouSaveItAs.cpp"

Execute it with "sudo ./a.out"

And the file "fileDump" will appear wherever you terminal is open to.

You can open it with a text editor and check it out.

Likewise you can write to /dev/mem... But like I said, be VERY careful and don't say I didn't warn you.

BTW, reading it should be pretty safe. I occasionally do for various reasons.

Thanks a lot for that. I think that will help me out a lot, and it sure gives me something to go with. I'll bet the equivilant C++ program to do that in Windows wouldn't be quite as simple. Man, you've just gotta love Linux.

---

### Post by lnostdal on 2007-01-29
> **TheFuzzy0ne said:**
> Crud!

I can't seem to get any input out of it. I tried attaching it to Firefox, and when I run it, Firefox exits. I also get the message: "no debugging symbols found". I don't have a clue what this means, but I still can't seem to find any way to actually view the content in RAM for a particular process. I guess I need to look into DGB a little deeper and learn how to use it.

Thanks again.

:)

just gonna paste some stuff

```

lars@ibmr52:~/programming/c$ cat a.c
#include <stdio.h>

int imASymbol;

void imAlsoASymbol(int a)
{
}



int main(int argc, char **argv)
{
  return(0);
}

lars@ibmr52:~/programming/c$ gcc -Wall a.c -o a
lars@ibmr52:~/programming/c$ strip a
lars@ibmr52:~/programming/c$ nm a
nm: a: no symbols
lars@ibmr52:~/programming/c$ gcc -Wall a.c -o a
lars@ibmr52:~/programming/c$ nm a
08049520 A __bss_start
080482a4 t call_gmon_start
08049520 b completed.5761
08049424 d __CTOR_END__
08049420 d __CTOR_LIST__
08049514 D __data_start
08049514 W data_start
080483d0 t __do_global_ctors_aux
080482d0 t __do_global_dtors_aux
08049518 D __dso_handle
0804942c d __DTOR_END__
08049428 d __DTOR_LIST__
08049434 d _DYNAMIC
08049520 A _edata
08049528 A _end
080483f8 T _fini
08048414 R _fp_hw
08048300 t frame_dummy
0804841c r __FRAME_END__
08049500 d _GLOBAL_OFFSET_TABLE_
         w __gmon_start__
080483c9 T __i686.get_pc_thunk.bx
08048324 T imAlsoASymbol
08049524 B imASymbol
08048234 T _init
08049420 a __init_array_end
08049420 a __init_array_start
08048418 R _IO_stdin_used
08049430 d __JCR_END__
08049430 d __JCR_LIST__
         w _Jv_RegisterClasses
08048350 T __libc_csu_fini
08048360 T __libc_csu_init
         U __libc_start_main@@GLIBC_2.0
08048329 T main
0804951c d p.5759
08048280 T _start

```

..see what's going on? strip removes symbols (debug info) to make binaries smaller

you generally want to compile stuff with the -g option to add extra debug info:

```
 gcc -Wall -g a.c -o a
```

-Wall gives you helpful hints; always include that one too!

as for GDB/DDD you can attach to an already running processes -- i have never had the need to do this though so i do not know how off-hand and do not feel like checking this out ATM :P  anyone else?

i instead start the software "under" GDB/DDD: 

```
gdb a
```

..is this something you can do? if i type run and press enter it starts .. if something crashes i can see the backtrace by typing bt and pressing enter; this will include info about files/line-numbers etc. when the binaries are compiled with -g .. and well; ddd is just about the same thing + more .. just type "ddd your-program" and press enter

---

### Post by LordHunter317 on 2007-01-29
Accessing /dev/ram won't do what you want without pain.  I wish people would just pretend it doesn't exist.

You need to learn to use gdb and a front-end.  It's more than capable of doing what you want to do.  It'd be helpful if you'd describe what you're actually trying to do.

---

### Post by Wybiral on 2007-01-29
> **LordHunter317 said:**
> ...It's more than capable of doing what you want to do.  It'd be helpful if you'd describe what you're actually trying to do.

I agree.

But, I'm not sure about "/dev/ram" I haven't been able to get anything out of those guys (maybe it was a typo?), however "/dev/mem" can actually be pretty useful. If you make a dump of the visible characters such as above ^^, a simple "find" in a text editor can reveal some interesting stuff that's tucked away in your memory, and is not restricted to one process.

Unfortunately you'll only get 1mb out of it (not entirely sure why that is...)

I haven't delved too deeply into gdb, but I'm sure it's very useful from what I have seen of it.

But sometimes you just need a plane dump of all of your recent memory.

Are there any gdb commands to give you a full ram analysis or cover more than one process?

---

### Post by LordHunter317 on 2007-01-29
> **Wybiral said:**
> But, I'm not sure about "/dev/ram" I haven't been able to get anything out of those guys (maybe it was a typo?), however "/dev/mem" can actually be pretty useful.Yes, I meant /dev/mem and no it isn't. 

> If you make a dump of the visible characters such as above ^^, a simple "find" in a text editor can reveal some interesting stuff that's tucked away in your memory, and is not restricted to one process.Sure, but it is restricted to whatever is mapped into physical RAM at the time.  Meaning you're essentially seeing random pages over which you have no control.  Ergo, useless.

> But sometimes you just need a plane dump of all of your recent memory./dev/mem doesn't give you that though.  You don't know what it will give you.

---

### Post by lnostdal on 2007-01-29
> **Wybiral said:**
> *mind-numbing babbling*
Are there any gdb commands to give you a full ram analysis or cover more than one process?

try `help data' while in the gdb-repl 

i have no idea what you mean by "a full ram analysis".. you can examine/manipulate memory (DDD kinda stands for Data Display Debugger) in many different ways and also make it draw [pretty graphics](http://www.gnu.org/software/ddd/plots.png) etc .. 

if you want to display data from multiple processes then start multiple instances of gdb/ddd or attach to them from a single one: [http://sources.redhat.com/gdb/current/onlinedocs/gdb_5.html#SEC28](http://sources.redhat.com/gdb/current/onlinedocs/gdb_5.html#SEC28)

---

### Post by Wybiral on 2007-01-29
Thanks lnostdal, even though you called my post "mind-numbing babbling", I'll assume it was a friendly joke and let it go :)

I'll definitely look into gdb more deeply. It sounds like it can DEFINITELY serve some very practical purposes.

Btw, by "a full ram analysis" I meant something that could give me a dump of more than just a couple of processes, something that would actually let me check out the contents of my memory. I think that's what the OP is was trying to do too.

---

### Post by lnostdal on 2007-01-29
> **Wybiral said:**
> Btw, by "a full ram analysis" I meant something that could give me a dump of more than just a couple of processes, something that would actually let me check out the contents of my memory. I think that's what the OP is was trying to do too.

If this is the case I'm kinda interested in what the OP "really wants" too.  (or maybe not :P)

---

### Post by Wybiral on 2007-01-29
Me too, actually...
I just get this nagging feeling that maybe...
Just maybe...
He/she's up to no good with all of this memory reading/writing :)

But, I could be wrong, maybe there's some logical ethical use?

---

### Post by LordHunter317 on 2007-01-29
> **Wybiral said:**
> Btw, by "a full ram analysis" I meant something that could give me a dump of more than just a couple of processes, something that would actually let me check out the contents of my memory.That's just thing though.  On a virtual memory system, you never want to do this.  Ever.  It makes no sense.  I can't emphasize this enough.

---

### Post by TheFuzzy0ne on 2007-01-30
Hi Guys.

Wow, that's a lot of posting! Sorry I don't have the time to respond to each on individually.

You wanted to know for what purpose my desired actions serve. Well, really there's no 'real' purpose, other than to learn. I like to see how things work, I have been like that since being a young boy. I like to learn whatever I can, even if it seems useless, as with a combined knowledge comes an increase understanding of how things work, and the posible solutions that can be utilised to fix various problem.

I hope this puts everyone's mind at ease.

Thanks for all of the information everyone. Some of it has gone right over my head, but just confirms my suspcions that I must put a lot more effort into it in order to get the results I want. I am fairly new to Linux, and know that it has more capabilities than I am aware of, and it's certainly something I'd like to master before I die. Hehe.

Thank again.

---


---
title: "[SOLVED] [C] Stuck in a tree... (n-ary trees)"
date: 2008-07-22
forum: Programming Talk
---

### Post by nvteighen on 2008-07-22
Hi again!

I'm stuck, as usual, and beg you all kind people for some little help. I'm trying to implement n-ary trees in C, without using Glib and any other library than the C Standard... In fact, I'm trying to do again Programming Challenge 7 ([http://ubuntuforums.org/showthread.php?t=747352](http://ubuntuforums.org/showthread.php?t=747352)), after my infamous Elliptic Curve...

The source is attached. I hope it's clear enough... You'll have to compile using the 'make' command. The output executable will be able to be passed through the debugger.

For some strange reason I can't understand, if I call map_free(), I get invalid free() complain. If I don't call it, there's no complain and almost no memory leakage... Am I freeing memory somewhere else? That's absurd.

The most strange bug is that the whole thing did work (recorded data into nodes, resized memory, freed, etc.) before I wrote linker() in map.c. After that, everything is broken but no error seems to be related to that function!

Thanks!

---

### Post by dribeas on 2008-07-22
> **nvteighen said:**
> 
The most strange bug is that the whole thing did work (recorded data into nodes, resized memory, freed, etc.) before I wrote linker() in map.c. After that, everything is broken but no error seems to be related to that function!


It's hard to debug data structures that are not fully documented. Anyway, with a sample file just like the one in the URL above, running your program dies with a segmentation fault:

```

(gdb) bt
#0  0x08048723 in node_get (var=0x0) at node.c:106
#1  0x080488c8 in linker (var=0x804a170, file=0x804a008) at map.c:99
#2  0x08048b0b in map_set (file=0x804a008, var=0x804a170) at map.c:172
#3  0x080485e4 in main (argc=2, argv=0xbf8717b4) at main.c:57

```

That is in a function called from within linker(), so you might have a problem in linker() after all.

Once you settle for reading the input more than once (which you are doing) I would gather more precise information on the first read, like maximum number of nodes instead of quantity of numbers in input. Then you can settle for more simple data structures that simplify programming, for example a 2D array of size (nodes x nodes) that can represent the graph. On most cases it will not take much more memory than your solution and it will surely be faster an mainly easier to work with.

If I get some more time I may try to debug into your program, but as stated before, it is hard to detect errors when you don't know intentions.

   David

---

### Post by nvteighen on 2008-07-22
Hi!

Thanks for the time spent.

The strange thing is that I get a different backtrace when running through gdb:
```

(gdb) bt
#0  0xb7f5f410 in __kernel_vsyscall ()
#1  0xb7e2b085 in raise () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7e2ca01 in abort () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7e63b7c in ?? () from /lib/tls/i686/cmov/libc.so.6
#4  0xb7e6f61b in free () from /lib/tls/i686/cmov/libc.so.6
#5  0x08048685 in node_free (node=0xb7f4c190) at node.c:66
#6  0x08048bff in map_free (var=0x804a170) at map.c:237
#7  0x080485fd in main (argc=2, argv=0xbfec0b44) at main.c:62

```

But yes, an error in linker() is the only logical solution... Everything else worked before and the only untested function is that one.

Let's see if I fully understand what you say about a 2D array of nodes. I suppose that that array should replace my 'map' structure, so the intersection of two related nodes could be marked by 1 and those which not, by 0 (An [adjacency matrix]("http://en.wikipedia.org/wiki/Adjacency_matrix"))? It makes more sense... though it requires a major code rewrite... (I'd gladly do it; I'm learning).

Yes, I want to get rid of that second file reading routine. It's quite absurd to rely on the file directly that much...

The "intention" is that the map is a high-level representation of the graph. Any map_xxxx() function acts on the graph, meanwhile node_xxxx(9 ones act directly to the nodes (lower-level). The map is, as you see, a list of all node pointers with some more information, so I can iterate through it using regular for-loops and having a way to access all nodes from one place. The node's type is based on GLib's implementation, the difference relies in the data type it holds (int instead of gobject).

I want to keep this the most library-like as possible, hence the split in different modules and obsessive encapsulation. Who knows, maybe I turn it into a shared library after all...

But again, thanks for having taken time to read the source. I know it's not easy to read someone else's source and worse if it's a whole program instead of a snippet.

---

### Post by nvteighen on 2008-07-22
Some progress: the most significant bug was in map_set and map_search, because I had changed how the later returns values but kept checking return values in the old way. That prevented any data to be written into the map structure, keeping its pointers as null and therefore caused a double-free in map_free(). Updated that, now it segfaults in linker() because of uncontrolled recursion, but data is stored and analyzed correctly again, which is the expected behaivor.

Now I can debug the linker effectively knowing that the error is there and not elsewhere. Thanks!

---

### Post by nvteighen on 2008-07-27
Yes! It finally works! Thank you dribeas for your matrix suggestion: An adjacency matrix was pretty easier to use.

OK, I think I have learned a lot by doing this: from recursions and some fake OOP using C to a lot on graphs. I attach the source code; compile it using "make". Any comment will be welcomed! (But don't comment on the ugly output).

---


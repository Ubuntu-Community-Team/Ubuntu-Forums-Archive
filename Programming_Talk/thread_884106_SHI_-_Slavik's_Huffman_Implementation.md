---
title: "SHI - Slavik's Huffman Implementation"
date: 2008-08-08
forum: Programming Talk
---

### Post by slavik on 2008-08-08
GPLv3 applies.

What this project is:
- a learning experience
- practice writing C code
- learning to create something that is actually useful

What has been done:
- the compression is half done
- the code builds a balanced tree from a file

What has not been done:
- decompression is completely absent
- for compression, the dictionary builder is not implemented (the last major part before it can be used)

Why this code is being released:
- I've always posted my code (that may be useful to someone)
- release early, release often (while often might not be often enough)
- Maybe someone will learn what huffman looks like in code

The problems with the code:
- header files contain code that has to be compiled
- the tree returns a node* instead of a tree type (typedef node* tree)
- the dictionary builder will have to be aware of the nodes (tree needs to have move left/right functions)

I have decided to follow the old Linux versioning scheme. Even version denote that some major function is done and the odd version indicates that the next major function is being worked on.

FUTURE MILESTONES:
0.2 - Compression is fully done
0.4 - Decompression is complete
0.6 - File spec is complete and implemented
0.8 - command line arguments spec is complete and implemented
1.0 - There are no problems with 0.8

---

### Post by Quikee on 2008-08-10
Adaptive huffman or 2-pass?

---

### Post by nvteighen on 2008-08-10
I see a couple of things that you may want to check out:
0. Why are you using header files for coding?
1. bitarray.h:ba_new() and ba_new_from_existing() duplicate code; I would make ba_new_from_existing() call ba_new() and then copy src's content if allocation was succesful.

Yes, your code shows the flaws of returning nodes instead of a pointer to the tree... I'm working on a library that, hopefully, should help on that, but it will take some time.

---

### Post by NovaAesa on 2008-08-10
Wow, that's pretty interesting. We learnt about Huffman encoding in Discrete Mathematics last semester. Of course, we had to do it with pen and paper rather than code :P

---

### Post by slavik on 2009-01-10
Just an update:

I set up a google code project for this:
[http://code.google.com/p/slava-huffman-implementation/](http://code.google.com/p/slava-huffman-implementation/)

Link is also in my sig (SHI).

---

### Post by jimi_hendrix on 2009-01-10
slavik i happen to be working on the same thing....i half got the idea from talking with you on irc and half from thinking about writting compression/encryption software...be interesting to see your code

---

### Post by slavik on 2009-01-10
it's there ... feel free to look.

---

### Post by drubin on 2009-01-12
> **slavik said:**
> it's there ... feel free to look.

Thanks for the permissions. Not like putting code online on google makes it very private :) hehe

---


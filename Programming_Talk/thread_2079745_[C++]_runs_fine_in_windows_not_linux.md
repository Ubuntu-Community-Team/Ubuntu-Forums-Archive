---
title: "[C++] runs fine in windows not linux"
date: 2012-11-02
forum: Programming Talk
---

### Post by dempa on 2012-11-02
Hi all.

I compiled a program I wrote both in codeblocks in windows and using g++ in linux. When I use windows/codeblocks, the program compiles and runs exactly as it should. However in linux with g++, it compiles and runs, but produces no output (even when I change line 234 to cout instead of cerr).

[http://pastie.org/private/mgenmlw6bmkx01atn93a](http://pastie.org/private/mgenmlw6bmkx01atn93a)

(sidequestion, why do I get strange highlighting in this paste? Did I not format comments correctly?)


Help is much appreciated.

---

### Post by dempa on 2012-11-02
sorry, here's the matrix header file

[http://pastie.org/private/7gfewtho8yvmgffaurpka](http://pastie.org/private/7gfewtho8yvmgffaurpka)

---

### Post by bird1500 on 2012-11-02
This forum has the ability to post inline formatted source code and to attach files.

---

### Post by trent.josephsen on 2012-11-02
```
typedef unsigned int uint;
```
](*,)

typedef-abuse aside, your matrix.h file isn't loading for me. I did notice this unrelated thing:

```
  if( argc != 2 )
  {
    ...
    exit( 2 );
  }
  assert (argc == 2);
```

Bit redundant, don't you think?

You have a lot of assert()s. You mentioned changing cerr to cout -- if you have reason to believe that you aren't seeing stderr, it could be that an assert() is failing, and failing silently because stderr is suppressed.

Have you checked the return value of the program?

---

### Post by spjackson on 2012-11-02
> **dempa said:**
> 
(sidequestion, why do I get strange highlighting in this paste? Did I not format comments correctly?)

You select the language on the top right above the paste box. The default is Ruby on Rails.

I don't use Code::Blocks but I do have it installed. When I compile and run your program from within Code::Blocks with a parameter of 8, it starts an xterm window and here's the output.
```

8 0
Process returned 1 (0x1)   execution time : 18.768 s
Press ENTER to continue.

```
That would seem to be correct, since all the code to print results is commented out.

I don't know what would be wrong with your settings for you not to get this.

---

### Post by SuperCamel on 2012-11-02
Your program works fine for me. Have you tried making a little 'Hello World' to test whatever configuration you are using?   You are running your compiled program in a terminal, right?

---


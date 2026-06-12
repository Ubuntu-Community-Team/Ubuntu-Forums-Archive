---
title: "New to programing, need help :)"
date: 2007-07-17
forum: Programming Talk
---

### Post by Mekanto on 2007-07-17
Ive only had Ubuntu a couple of days and i want to get into learning C.
The majority of tutorials i found on the internet went into both C and C++, I would prefer to learn C++ after C.
The tutorials seemed to go striaght from history into programming, but i am having trouble compiling.

I don't know if this is right, I tryed to make a program to say 'hello world' or something :guitar:

#include <stdio.h>
main()
{
  printf("hello, world\n");
}

And saved it as hello.c

Then i used the terminal command "cc hello.c" which did nothing it seems.
So i right clicked on the file (hello.c) and selected open with "gcc" which made a new file called 'a.out'.
I click on 'a.out' and nothing happends, I have no idea what im doing could someone help me out please?

---

### Post by jonathanmotes on 2007-07-17
Try typing "./a.out" (without the quotes) in the terminal. I'm sort of new to programming myself, but this is the only way I know of to execute files like this in Linux.

---

### Post by AlexThomson_NZ on 2007-07-17
Yep, your program is a terminal program (ie. it doesn't open any windows), so if you want to see the output it has to be run in a terminal.

Good job tho- your first program! :)

---

### Post by Mekanto on 2007-07-17
Hey thanks it worked in the terminal, is there anything I could change to make it run in its own window?

---

### Post by AlexThomson_NZ on 2007-07-17
Check out [http://www.gtk.org/tutorial/c39.html#SEC-HELLOWORLD](http://www.gtk.org/tutorial/c39.html#SEC-HELLOWORLD) for a good tutorial on gtk+ programming (ie. creating windows programs)

I would strongly recommend getting used to the basics first though!  You are definitely on the right track!

Maybe have a look at loops, structs, pointers, header files, etc. before tackling windowss programming?

---

### Post by Note360 on 2007-07-17
to compile in the terminal the command is

```

gcc -o hello hello.c

```

if you dont specify the output it will save as a.out (-o is the output flag and hello is the name of the output file thingy)

---

### Post by LaRoza on 2007-07-17
If you want free resources for programming (tutorials and books to download) check out my wiki, the link is in my sig.

-edit When putting code on the forum, put it between the [ code ] [ /code ] tags so the formatting is preserved, it makes it easier to read.

---


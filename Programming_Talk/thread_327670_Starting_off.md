---
title: "Starting off"
date: 2006-12-29
forum: Programming Talk
---

### Post by sdmike on 2006-12-29
Ok so I'm a little lost here on how to compile. So lets say if I want to compile an easy thing like hello world, where do I put the code and how do I point to g++ to compile it.

This is new to me so bare with me on this and try not to rip my head off.

Thanks

:-D

---

### Post by Wybiral on 2006-12-29
Ok, first you should get comfortable with the command line... But...

Open up a text editor. Save your hello world program as something like "hello.cpp"

Then open a command line and navigate to the folder that your "hello.cpp" file is in...

Type "g++ hello.cpp" in the command line and hit enter... The file "a.out" should appear in that folder...

Execute it from the command line with "./a.out"

You can change the output file when you compile it with "-o" try this...

```

g++ hello.cpp -o helloWorld

```

Does that help any?

---

### Post by sdmike on 2006-12-29
Ok when I executed the program, it was typing hello world one after the other in the terminal very quickly. Why is that?

---

### Post by sdmike on 2006-12-29
so does this command "g++ hello.cpp -o helloWorld" rename the output file?

---

### Post by Wybiral on 2006-12-29
You can post your hello world source code, it might be in a loop.

-o is for compiling it to an output file with a different name than "a.out" because a.out probably isn't what you want your executable file named.

---

### Post by sdmike on 2006-12-29
it was in a loop my bad lol.

---


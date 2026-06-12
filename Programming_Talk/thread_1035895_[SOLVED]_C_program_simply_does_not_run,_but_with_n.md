---
title: "[SOLVED] C program simply does not run, but with no error message"
date: 2009-01-10
forum: Programming Talk
---

### Post by kapok on 2009-01-10
quick question: i'm trying to learn how to program, and i wrote the simple "Hello World" program in C. i compiled it(thank you guys for that help) and now i have the hello program in my home folder. it has the blue icon with the gears, which means it is an executable. when i double click it though, nothing happens. i thought it should either work or give me an error message. 


maybe the flaw is in my program.
it is:

> main()
{
puts("hello world");
return(0);
}

also, i can't search for help on 'c' in the ubuntu forums, because no matter what you put before or after it, it says that 'c' was left out because it was too short.

---

### Post by Zugzwang on 2009-01-10
Your program works perfectly. But you have to run it from the terminal since you output stuff to its standard output, which is only visible there (or whereever it is routed to).

Have a look at the stickies, i.e. "how to compile & run your first C program".

---

### Post by SledgeHammer_999 on 2009-01-10
And to run it from the terminal:
1.open the terminal
2. write commad--> "./helloworld"   (or whatever the name of the program is)

---

### Post by Nemooo on 2009-01-10
You'll want to include the header stdio.h, because it contains the *puts()* function. All explained here:

[http://ubuntuforums.org/showthread.php?t=689635](http://ubuntuforums.org/showthread.php?t=689635)

---

### Post by kapok on 2009-01-10
thanks guys.

---


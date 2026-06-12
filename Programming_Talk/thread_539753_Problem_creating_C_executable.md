---
title: "Problem creating C executable"
date: 2007-08-31
forum: Programming Talk
---

### Post by Shachiel on 2007-08-31
Hello, I'm new at programming (actually I'm sitting in my C class) and we made the classic Hello World, however everyone here uses Winblows (TurboC) while I'm trying to get the same results using Eclipse. I know the code should be the same, my problem is that after using
```

~/workspace/helloworld/  ./a.out

```

I get some file named Hello, however, when I try to run it on another terminal after creating a launcher from my desktop I get the following error.

"There was an error creating the child process for this terminal"

can anyone please tell me how to avoid this mistake or the equivalent to the ".exe"?

---

### Post by Chickencha on 2007-08-31
I'm a little confused by your post.  What does the command

```
~/workspace/helloworld/  ./a.out
```

intend to accomplish?  How did you go about compiling the code?  And how did you go about trying to execute it?  If you could provide that information, then I might be able to help.

---

### Post by steve.horsley on 2007-08-31
I don't know about Eclipse. On the command line, I would do:
**cc -o Hello Hello.c**
and that woud compile Hello.c to an executable called Hello.

---

### Post by ddrichardson on 2007-08-31
I'm a little rusty but is a.out not an old fashioned elf binary? I believe the syntax is```
gcc -o filename filename.c
```

---

### Post by ddrichardson on 2007-08-31
Apparently I type one minute slower than those in the know ;-)

---

### Post by eph1973 on 2007-08-31
gcc helloworld.c -o helloworld

you want the <file>.c before the -o and the last one would be whatever name you wanted the file to be, so you could type:

gcc helloworld.c -o hello

and you would get an executable file named "hello"

---

### Post by [h2o] on 2007-09-01
> **eph1973 said:**
> gcc helloworld.c -o helloworld

you want the <file>.c before the -o and the last one would be whatever name you wanted the file to be, so you could type:

Order of the options doesn't matter in this case. To me it seems more common to have the file to compile last, and all options first.

---

### Post by eph1973 on 2007-09-01
> **'[h2o] said:**
> Order of the options doesn't matter in this case. To me it seems more common to have the file to compile last, and all options first.

Ahh, yes, my fault.  I had been using gcc <source1.c> <source2.c> ... -o <outputname> in the past, but it does make more sense the other way.  Also, for some reason I originally misread their responses, but they are both 100% correct.

---

### Post by Lord Illidan on 2007-09-01
Also, instead of using Eclipse, why not use a text editor? You get to learn more..it's not just pressing RUN.

---

### Post by Shachiel on 2007-09-01
Wow that was fast, thanks a lot to everybody for the quick replies.

I've tried everything you've told me... however I still get the same error message when attempting to run the executable. I'm trying to run it on terminal so I don't know if that's my mistake, can anyone please help?

Thanks again

.SCHL

---

### Post by Lord Illidan on 2007-09-01
Let's say your c file is 

helloworld.c

So, I would do :

gcc -o helloworld.c helloworld

to compile.

Then I would type :

./helloworld

in that directory to execute it. Clear?

---

### Post by aJayRoo on 2007-09-01
> **Lord Illidan said:**
> Let's say your c file is 

helloworld.c

So, I would do :

gcc -o helloworld.c helloworld

to compile.

Then I would type :

./helloworld

in that directory to execute it. Clear?

Hi, sorry if it seams like I'm picking at you but I believe you have the command line compile incorrectly there, it should be:
```
gcc -o helloworld helloworld.c
```
Easy typo to make, I do it a lot!

---

### Post by Lux Perpetua on 2007-09-01
Maybe I'm paranoid, but I prefer to put the -o option *after* the source file. The reason is that if you accidentally do ```
gcc -o helloworld.c helloworld.c
```or something similarly stupid, it will silently destroy your source file!

---

### Post by [h2o] on 2007-09-02
> **Lux Perpetua said:**
> Maybe I'm paranoid, but I prefer to put the -o option *after* the source file. The reason is that if you accidentally do ```
gcc -o helloworld.c helloworld.c
```or something similarly stupid, it will silently destroy your source file!

But surely ```
gcc helloworld.c -o helloworld.c
``` would also destroy your source file, and it is equally likely to that mistake, isn't it?

---

### Post by Shachiel on 2007-09-03
Great, it works now, thanks a lot everyone =)

---


---
title: "how to look at the source code???"
date: 2010-10-24
forum: Programming Talk
---

### Post by c2tarun on 2010-10-24
hi friends
this is kind of a silly question.
i downloaded the source code of many applications in order to look them. but i don't know from where to start looking at them.
can anyone please give me any suggestions or guidance that from where should i start looking at the source code, like read the documentation first or something like this. 
thanx

---

### Post by phrostbyte on 2010-10-24
Depends what language the application is written in. C code usually is in files with the extension .c or .h. C++ is .cc, .cpp, and .h, Python is .py. Etc. etc.

---

### Post by c2tarun on 2010-10-24
> **phrostbyte said:**
> Depends what language the application is written in. C code usually is in files with the extension .c or .h. C++ is .cc, .cpp, and .h, Python is .py. Etc. etc.

but from where to start looking at the code.
should i start looking by opening each file and look for the main function first.
or is there any documentation available that explains which file contains which function and its working.
thanx

---

### Post by worseisworser on 2010-10-24
figure out what libraries and APIs the application software in question uses; look for documentation there, and you'll understand what the source in front of you does.

..what documentation exists for any software project is entirely arbitrary of course; there is no general answer.

---

### Post by mo.reina on 2010-10-24
look at the main function, then trace the flow from there.

---

### Post by c2tarun on 2010-10-24
hey can anyone tell me how to find main() function from a bunch of .c files???

---

### Post by spjackson on 2010-10-24
> **c2tarun said:**
> hey can anyone tell me how to find main() function from a bunch of .c files???
```

$ fgrep main *.c

```Or if you are using some IDE or other, there's probably a "Find In Files" menu option, or similar.

---

### Post by Jonas thomas on 2010-10-24
> **c2tarun said:**
> hey can anyone tell me how to find main() function from a bunch of .c files???

Sometimes there is a file called main.c you can just open that up and look at it.
Another way to find it is to set up a project in an IDE such as code::blocks (my favorite) and search for it that way.  Another way is through the grep command (not to good at that to advice how).

If the code that your looking at is cpp and has wxwidgets or qt written in it, the main() is so buried you'll never find it.

A learning suggestion, it great that your jumping in trying to learn code by jumping in and looking at it. At a certain level you need to crawl before you walk, walk before your run.

Sometimes if you jump into the deep end of the pool trying to learn how to swim, you just drown..(unless your one of those people who don't)  There are many many resources available to learn how to program..

Are you doing this just for personal enrichment, or is there a specific goal your trying to get to?  Perhaps if you want to elaborate on what your trying to do, we can get suggest a path for you to follow.

---

### Post by ssam on 2010-10-24
i find the program ack-grep very useful. it is a wrapper around grep (command line search tool). from the source directory do

```
ack-grep main
```
or if that gives to many hits
```
ack-grep "main\("
```

main() is sometimes in main.c, eg for gimp it is
```
app/main.c
```
but it could also be something like
```
source/main.c
src/main.c
src/gimp.c

```
or various variations.

reading the gimp main() function, app_run() seems to be the next interesting function.

so then try
```
ack-grep app_run
```
and see where that gets you.

---

### Post by luvshines on 2010-10-24
cscope is a nice C code browser, I use it all the time :)

---

### Post by c2tarun on 2010-10-24
> **Jonas thomas said:**
> Sometimes there is a file called main.c you can just open that up and look at it.
Another way to find it is to set up a project in an IDE such as code::blocks (my favorite) and search for it that way.  Another way is through the grep command (not to good at that to advice how).

If the code that your looking at is cpp and has wxwidgets or qt written in it, the main() is so buried you'll never find it.

A learning suggestion, it great that your jumping in trying to learn code by jumping in and looking at it. At a certain level you need to crawl before you walk, walk before your run.

Sometimes if you jump into the deep end of the pool trying to learn how to swim, you just drown..(unless your one of those people who don't)  There are many many resources available to learn how to program..

Are you doing this just for personal enrichment, or is there a specific goal your trying to get to?  Perhaps if you want to elaborate on what your trying to do, we can get suggest a path for you to follow.

  hey any anyone please suggest me how to open the source files as an existing project in code::block. i tried but unable to locate the file to be opened.

---

### Post by Jonas thomas on 2010-10-25
> **c2tarun said:**
> hey any anyone please suggest me how to open the source files as an existing project in code::block. i tried but unable to locate the file to be opened.

If the project was done in code::blocks there will be a cbp file.  If the project was not created in code::blocks you will need to create a new project and add the cpp, .h files to it.  At this point, you really should go through some getting started tutorial for code::blocks.

---


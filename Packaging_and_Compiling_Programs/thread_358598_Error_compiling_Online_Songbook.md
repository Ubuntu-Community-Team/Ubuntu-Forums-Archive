---
title: "Error compiling Online Songbook"
date: 2007-02-11
forum: Packaging and Compiling Programs
---

### Post by Terry of Astoria on 2007-02-11
On my ubuntu 6.06 server, compiling Onlinesongbook because I think it would be a really cool tool for our reggae band to make "cheat sheets" and songbooks
(see [http://onlinesongbook.sourceforge.net/]("http://onlinesongbook.sourceforge.net/") )I got an error I don't understand. See --

```
me@pavlov:~/songbook/chord$ make
gcc -DUS -g   -c -o common.o common.c
gcc -DUS -g   -c -o xpose.o xpose.c
gcc -DUS -g   -c -o iso.o iso.c
gcc -DUS -g   -c -o chord.o chord.c
gcc -DUS -g   -c -o grid.o grid.c
gcc -DUS -g   -c -o toc.o toc.c
g++ -DUS -g -c -o sortscripture.o sortscripture.c
g++ -DUS -g -o chord common.o xpose.o iso.o chord.o grid.o toc.o sortscripture.o
chord.o: In function `process_file':/home/me/songbook/chord/chord.c:1897: undefined reference to `errno'
collect2: ld returned 1 exit status
make: *** [chord] Error 1
me@pavlov:~/songbook/chord$
```
Can you help me learn to get it to compile?
I figured out that it's talking about line 1897 in the file chord.c but I don't understand the error. Here are the lines 1896 and 1897:
```
                    if(fseek(source_fd, tmp_file_ptr, SEEK_SET) == -1){
                        fprintf(stderr, "Lookahead: rewind failed: %d\n",errno);

```
Thanks, Terry

---

### Post by Terry of Astoria on 2007-02-11
Wait a sec! Googled errno and discovered [This here]("http://www.opengroup.org/onlinepubs/009695399/functions/errno.html")
on a whim I tried adding ```
#include <errno.h>
``` and removed ```
extern int errno;
```
It built with no errors. Do you think that'll work?

---


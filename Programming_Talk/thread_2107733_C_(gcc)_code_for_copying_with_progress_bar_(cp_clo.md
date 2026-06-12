---
title: "C (gcc) code for copying with progress bar (cp clone)"
date: 2013-01-22
forum: Programming Talk
---

### Post by honeybear on 2013-01-22
Hello,

I would like to know whether it has been released a C (gcc) code for copying with progress bar (cp clone). In the book of Dennis, there is one example that does CP. A progress might be not so complicated to be made. 

Would you eventually know a code?

Kind regards

---

### Post by Tony Flury on 2013-01-23
> **honeybear said:**
> Hello,

I would like to know whether it has been released a C (gcc) code for copying with progress bar (cp clone). In the book of Dennis, there is one example that does CP. A progress might be not so complicated to be made. 

Would you eventually know a code?

Kind regards

This raises all sorts of questions : 

1) Which graphical framework (GTK, TK, KBE etc etc).
2) You do know that gcc is just a compiler, which is very different from C which is a language.
3) Is this home work ?

---

### Post by Warren Hill on 2013-01-23
> **Tony Flury said:**
> This raises all sorts of questions : 

1) Which graphical framework (GTK, TK, KBE etc etc).
2) You do know that gcc is just a compiler, which is very different from C which is a language.
3) Is this home work ?

If its a simple Command line app then you could calculate what percentage of the file you have downloaded in a loop and print something, '*' example, for every 5% of the download.

Simple enough?

I won't give the code but it should give you enough of clue to work it out.

If its not home work then we need to know which graphical framework.

---

### Post by jwbrase on 2013-01-23
It's not an exact cp clone, but there is a program called pv in the repositories that can be inserted into a pipeline to display a progress bar on the terminal.

---

### Post by MG&amp;TL on 2013-01-23
So...if there's an example in the "book of Dennis", then why not learn from /rip off that one?

---

### Post by honeybear on 2013-01-24
Ah guys, so much replies, and so much no content for some. 

Surely a console based cp way, since cp is nothing else than cp:

whereis cp


A simple possible starting point is here. So there are many ways to make cool cp looking with a great progress bar. 

Simply that's probably not the right place, forum, public,... about C coding maybe...  

I wanted to exchange about some possible codes. well

```

#include <stdio.h>
#include <assert.h>
#include <stdlib.h>

#define MAXLINE 10 // in the book this is 1000

void copy(char to[], char from[])
{
    int i;

    i = 0;
    while((to[i] = from[i]) != '\0')
        ++i;
}

int main(int argc, char *argv[])
{
    int i;

    // use heap memory as many modern systems do
    char *line = malloc(MAXLINE);
    char *longest = malloc(MAXLINE);

    assert(line != NULL && longest != NULL && "memory error");

    // initialize it but make a classic "off by one" error
    for(i = 0; i < MAXLINE; i++) {
        line[i] = 'a';
    }

    // cause the defect
    copy(longest, line);

    free(line);
    free(longest);

    return 0;
}

```


with another layer with sthg similar to such as this:

```
#include <stdio.h>

int  main(void)
{

char *tu="*";
int i;

for(i=0;i<=100;i++) {

        printf("[%s %d", tu,i); printf("\r");

        fflush(stdout);

        usleep(1000);
        }
}
```

---

### Post by honeybear on 2013-03-03
A C code with a progress bar is a thing which is very easy to make. Since 80s it must exsits, but google does not pop it up.   In 50 lines, one can make a void. I will do one in few weeks for you guys.

---

### Post by conradin on 2013-03-05
The cp command had a progress bar.  I used to see it on some fedora 3 computers I had ages ago.
it was a little animation formatted with == signs and pipes and slashes.

it would kinda look like this, and the number of = sings would progress over time / copy percentage. 
I haven't seen it in modern versions but i assumed its just an option that I had set up in older linux versions.

my understanding of scripting is that things like animations detract from my computer doing what I asked it to do. 
```

#!/bin/bash
for i in `seq 0 10`
do 
	clear
	echo "=--"
	sleep 0.3
	clear
	echo "=/"
	sleep 0.3
	clear
	echo "=|"
	sleep 0.3
	clear
	echo "=\""

done

```

---

### Post by sudodus on 2013-03-05
> **jwbrase said:**
> It's not an exact cp clone, but there is a program called pv in the repositories that can be inserted into a pipeline to display a progress bar on the terminal.
+1

pv is doing this

copy 
```
pv < bigfile.orig > bigfile.copy
```

compress
```
pv < bigfile.orig | gzip > bigfile.copy.gz
```

But this is simpler than cp (not managing wild cards or preserving permissions like cp -p etc)

---

### Post by honeybear on 2013-03-19
> **sudodus said:**
> +1

pv is doing this

copy 
```
pv < bigfile.orig > bigfile.copy
```

compress
```
pv < bigfile.orig | gzip > bigfile.copy.gz
```

But this is simpler than cp (not managing wild cards or preserving permissions like cp -p etc)

I dont like pv that much. It is kinda hacky and not so much reliable.

I have no time to make it, but soon or later, I will release a new CP with this progress bar. I need only 3-4 hours, but I cannot find it.

(oh, I forgot, I code under C mostly. So it will be in C)

---

### Post by sudodus on 2013-03-20
Good luck, and please make it available to the linux community :-)

---

### Post by conradin on 2013-03-21
I bet there is a way to do it using wget!
I havent really thought about it though. 

then I wondered maybe other commands have the progess bar... like cat, mv or something else.
then I found this:
[http://www.ex-parrot.com/~chris/stuff/cwp.c.gz](http://www.ex-parrot.com/~chris/stuff/cwp.c.gz)

maybe that will be helpful!

---

### Post by trent.josephsen on 2013-03-21
[quote=rsync(1)]            --progress              show progress during transfer[/quote]

rsync wins again!

When this topic first came up I thought "Isn't there a command line switch for that?" But I checked cp(1) and saw nothing, so chalked it up to poor memory. For some reason the mention of wget caused it to dawn on me that I had been thinking of rsync in the first place.

---

### Post by sudodus on 2013-03-22
> **trent.josephsen said:**
> rsync wins again!

When this topic first came up I thought "Isn't there a command line switch for that?" But I checked cp(1) and saw nothing, so chalked it up to poor memory. For some reason the mention of wget caused it to dawn on me that I had been thinking of rsync in the first place.
+1

You are right. rsync is the 'power' alternative to cp as always :-)

---

### Post by honeybear on 2013-03-23
actually there is one already with cp -g 

[http://www.mail-archive.com/bug-coreutils@gnu.org/msg00610.html](http://www.mail-archive.com/bug-coreutils@gnu.org/msg00610.html)

would you know where I can get the *.c source?

---

### Post by schragge on 2013-03-23
:?: The source is included in the message you linked. It's a patch to cp/mv code. However, it appears this patch has been rejected by GNU coreutils developers.

---


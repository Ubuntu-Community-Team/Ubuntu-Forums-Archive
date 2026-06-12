---
title: "clear the screen from the C script"
date: 2011-08-22
forum: Programming Talk
---

### Post by DependencyHell on 2011-08-22
Hi all!

I would like to know is there a way to clear the screen via the c command. I used tputs, but it appears it is not working:
```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <string.h>
#include <termios.h>
#include <curses.h>
//(globally defined)
FILE * out_stream=(FILE*)0;
FILE* in_stream=(FILE*)0;
......
int char_to_term(char ch){
  if(out_stream)
    putc(ch,out_stream);
  return 0;
}
int char_to_term2(char ch){
  if(in_stream)
    putc(ch,in_stream);
  return 0;
}
int_main(int argc, char* argv[]){
....
 FILE* input=fopen("/dev/tty","rw");
 FILE* output=fopen("/dev/tty","w");
......
 clear=tigetstr("clear");
 tputs(clear,1,char_to_term);
 tputs(clear,1,char_to_term2);
........

```I was making that code only for my personal training purpose (it prints on the terminal even if redirected...). It also contains the part where i manipulate the cursor movement, but somehow i cannot manipulate "clear".

Any help would be very appreciated

---

### Post by nvteighen on 2011-08-22
The only reasonable way to do this is using ncurses's clear function... unless you're reimplementing ncurses or you're trying to understand how terminals work (termios, etc.). But use ncurses if all you want is to write a text UI where character cells are better than line-buffered stdout and stdin. 

Look here for a nice tutorial about ncurses: [http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/](http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/)

---

### Post by tbastian on 2011-08-22
if you print this character sequence it clears the terminal

```
char clear [5]  = {27, '[', '2', 'J', 0};
```

I'm not really sure how or why it works... I found it in some code I inherited at work once...

---

### Post by tbastian on 2011-08-22
... here is a short example program I just wrote:

```

#include <stdio.h>

int main ( int argc, char ** argv )
{
	char clear [ 5 ] = { 27, '[', '2', 'J', 0 };
	printf ( "%s", clear );
	return 0;
}

```

---

### Post by sisco311 on 2011-08-22
+1 for ncurses, also check out: [http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?answer=1031963460&id=1043284385](http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?answer=1031963460&id=1043284385) (OPTION 4 is interesting...)

> **tbastian said:**
> 
I'm not really sure how or why it works... 

It's an [ANSI escape]("http://en.wikipedia.org/wiki/ANSI_escape_code") sequence.

---

### Post by jawilljr on 2011-08-22
> **tbastian said:**
> if you print this character sequence it clears the terminal

```
char clear [5]  = {27, '[', '2', 'J', 0};
```

I'm not really sure how or why it works... I found it in some code I inherited at work once...

Those are called [Console Codes.](http://manpages.ubuntu.com/manpages/intrepid/man4/console_codes.4.html) It's a throwback from the old VT100/VT102 terminal.

Jerry

---

### Post by nvteighen on 2011-08-22
That ANSI escape will do exactly like the clear shell command: fill the terminal with newlines. This means that the screen contents are still available by scrolling the terminal (in an X terminal emulator) or using the Shift-PgUp on the console. On the other hand, ncurses really clears the screen.

EDIT: ok, it seems that the escape has a different behaivor, replacing by blanklines some of the previous contents... anyway, I wouldn't rely on any ANSI escape.

---

### Post by DependencyHell on 2011-08-22
[QUOTE=nvteighen]unless you're reimplementing ncurses or you're trying to understand how terminals work (termios, etc.)[/QUOTE]
Yes, this is the thing, i am trying to understand how terminals work. I tried to use clear() (didn't help), but the drawback is that i can't use it directly on /dev/tty (as far as i see from man pages), which i want to be used even if i run the code with redirection (awkward, i know...:P but i am just learning by a "pedagogical" example...).
[QUOTE=nvteighen](OPTION 4 is interesting...)[/QUOTE]
Hahaha! it is! i almost did that several times....

---

### Post by DependencyHell on 2011-08-22
Hi all!

After some struggle, i managed to solve my problem...i put the tputs command before the setupterm command, but it should come afterwards.
```

 setupterm(NULL,fileno(output),(int*)0);
 clear=tigetstr("clear");
 tputs(clear,1,char_to_term);

```
Silly me! If anyone would like to try this example, which i made up for to learn about the terminals, it is attached. It basically sweeps with the cursor through the line of text and captures the character when you press any key.
 
Cheers!

---

### Post by Smart Viking on 2011-08-22
For the record, your program doesn't compile on my computer:
```
**[805][smartviking.debian: /home/smartviking]$ gcc choose.c -std=gnu99 -o omg**
choose.c: In function &#8216;main&#8217;:
choose.c:56: warning: implicit declaration of function &#8216;setupterm&#8217;
choose.c:58: warning: implicit declaration of function &#8216;tputs&#8217;
/tmp/ccfIelym.o: In function `main':
choose.c:(.text+0x28a): undefined reference to `setupterm'
choose.c:(.text+0x294): undefined reference to `tigetstr'
choose.c:(.text+0x2b3): undefined reference to `tputs'
choose.c:(.text+0x3ad): undefined reference to `tigetstr'
choose.c:(.text+0x3ca): undefined reference to `tparm'
choose.c:(.text+0x3e1): undefined reference to `tputs'
collect2: ld returned 1 exit status
**[806][smartviking.debian: /home/smartviking]$ gcc choose.c -o omg**
/tmp/ccfrtMp8.o: In function `main':
choose.c:(.text+0x28a): undefined reference to `setupterm'
choose.c:(.text+0x294): undefined reference to `tigetstr'
choose.c:(.text+0x2b3): undefined reference to `tputs'
choose.c:(.text+0x3ad): undefined reference to `tigetstr'
choose.c:(.text+0x3ca): undefined reference to `tparm'
choose.c:(.text+0x3e1): undefined reference to `tputs'
collect2: ld returned 1 exit status
**[809][smartviking.debian: /home/smartviking]$ gcc choose.c -std=c99 -o omg**
choose.c: In function &#8216;detect_key&#8217;:
choose.c:13: warning: implicit declaration of function &#8216;fileno&#8217;
choose.c: In function &#8216;main&#8217;:
choose.c:56: warning: implicit declaration of function &#8216;setupterm&#8217;
choose.c:58: warning: implicit declaration of function &#8216;tputs&#8217;
/tmp/cc6SQ0h4.o: In function `main':
choose.c:(.text+0x2a8): undefined reference to `setupterm'
choose.c:(.text+0x2b2): undefined reference to `tigetstr'
choose.c:(.text+0x2d1): undefined reference to `tputs'
choose.c:(.text+0x3d5): undefined reference to `tigetstr'
choose.c:(.text+0x3f2): undefined reference to `tparm'
choose.c:(.text+0x409): undefined reference to `tputs'
collect2: ld returned 1 exit status

```I'm no good with C so I can't really debug that, all the libraries included at the top of the file are located in /usr/include/.

---

### Post by DependencyHell on 2011-08-22
Hi Smart Viking.

Here's how you should compile it
gcc -o choose choose.c -lncurses
and also it is good to install libncurses5-dev via the synaptic before you compile it :D
i hope now it will work!

Cheers!

---

### Post by Smart Viking on 2011-08-22
Thanks.

Now it did compile but got a Segmentation fault:
```
[830][smartviking.debian: /home/smartviking]$ ./choose 




















(null)
Segmentation fault
[831][smartviking.debian: /home/smartviking]$ 

```

But since the program works on your computer and not mine, it's obviously not easy for you to debug that, just thought you should know. :)

---

### Post by DependencyHell on 2011-08-22
Oops, i forgot to tell you that it takes a line argument. So you run it as
./choose "little Mary has a little lamb"
It sweeps with the cursor through this line.
I forgot to handle the case when you supply no arguments...bad programming habit :(

---

### Post by Smart Viking on 2011-08-22
Ok, now it works, ty. :)

---


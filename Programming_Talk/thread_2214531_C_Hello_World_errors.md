---
title: "C Hello World errors"
date: 2014-04-01
forum: Programming Talk
---

### Post by itpro007ca on 2014-04-01
I'm trying to learn C,but,after saving "```
hello.c
```"


```
#include<stdio.h>

	int main()

	{

		printf(&#8220;Hello World\n&#8221;);

		return 0;

	}

```


and typing cc,or gcc hello.c,I keep getting this error(since I copied and pasted it from a programming site,it is correct.):

```
gcc hello.c
hello.c: In function &#8216;main&#8217;:
hello.c:7:3: error: stray &#8216;\342&#8217; in program
hello.c:7:3: error: stray &#8216;\200&#8217; in program
hello.c:7:3: error: stray &#8216;\234&#8217; in program
hello.c:7:13: error: &#8216;Hello&#8217; undeclared (first use in this function)
hello.c:7:13: note: each undeclared identifier is reported only once for each function it appears in
hello.c:7:19: error: expected &#8216;)&#8217; before &#8216;World&#8217;
hello.c:7:19: error: stray &#8216;\&#8217; in program
hello.c:7:19: error: stray &#8216;\342&#8217; in program
hello.c:7:19: error: stray &#8216;\200&#8217; in program
hello.c:7:19: error: stray &#8216;\235&#8217; in program
```

What's the problem?

I know it has to be compiled and saved as an > a.out file,then executed,right?

Thanks

---

### Post by itpro007ca on 2014-04-01
Changing the line to this got rid of the errors:

> "Hello, world!\n"

So,what was the error and why?

Now,that I was able to : > gcc hello.c and create the > a.out file,how do I get it to run?

Is it>  chmod ?+x filename?

---

### Post by itpro007ca on 2014-04-01
Never mind!

I got it,thanks to a web search for "how to create executable of a C program in Ubuntu."

> ./ a.out

I still need help to understand the error in syntax,though.

---

### Post by steeldriver on 2014-04-01
Your original code had some non-ASCII characters (in particular the funky curved double quotes) - maybe because of the editor you used to create it (or was it copy/pasted from the web?)

The a.out file should already be executable, so you should just need to do

```
./a.out
```

---

### Post by itpro007ca on 2014-04-01
I copied and pasted from the web to nano.

Do the comma and exclamation mark matter?

---

### Post by Iowan on 2014-04-01
> **itpro007ca said:**
> 
Do the comma and exclamation mark matter?Shouldn't... 
but it won't take long to edit the file and try again...

---

### Post by itpro007ca on 2014-04-01
Thanks!

I got it now.I also downloaded > g++(after trying to run it and Ubuntu suggested it!) and was able to save the c++ version as > hello1.c ,then after it overwrote the > a.out file,I clued in that I could rename them hello and hello1 and change the text to differentiate between them.

Now:

I need a C/C++ IDE to get started with.I'm intending to learn C,then C++,then Java,then maybe Pascal(I read a book about that back in the 70s;can't get it out of my mind! lol),then, Perl,Python,Php and Ruby.

I'm thinking of Netbeans,but,I know there's Eclipse,Code Blocks and others.

Recommendations?

---

### Post by Vaphell on 2014-04-02
you can name your binary file that is the result of compilation, add *-o programname*.
```
gcc hello.c -o helloc
g++ hello.cpp -o hellocpp
./helloc
./hellocpp
```

---

### Post by Warren Hill on 2014-04-02
To clarify what's going on here the reason you need the 

```
./
```

Is that the system searches your path for the program and the current directory is not in your path.

There are more details [here on AskUbuntu]("http://askubuntu.com/q/320632/107450")

---


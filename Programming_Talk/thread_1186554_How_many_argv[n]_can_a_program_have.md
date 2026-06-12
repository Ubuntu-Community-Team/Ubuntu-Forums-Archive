---
title: "How many argv[n] can a program have?"
date: 2009-06-13
forum: Programming Talk
---

### Post by Krupski on 2009-06-13
Hi all,

I wrote a little program to merge several files into one. Here's the source:


```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#undef BUFSIZ
#define BUFSIZ 65536

int main(int argc, char *argv[])
{
	FILE* infile;
	char buffer[BUFSIZ];
	int n, count;

	for(n = 1; n < argc; n++) { // for each file on the command line

		infile = fopen(argv[n], "rb"); // open the file

		while(! feof(infile)) { 
			count = fread(buffer, 1, BUFSIZ, infile); // read into buffer...
			fwrite(buffer, 1, count, stdout); // write to stdout
		}

		fclose(infile); // close when done
	} // do next

	return 0;
}


```


Note that the program opens each file specified on the command line (i.e. argv[1], argv[2], etc...)

Normally I only merge a few files together, but the question popped into my mind... HOW MANY can there be before I hit some limit?

Is there such a thing as argv[100]? How about argv[10000]?

How far does it go? 

And if there is a limit, can that limit be changed?

Thanks in advance!

-- Roger

---

### Post by soltanis on 2009-06-13
It goes up to the maximum size of an integer (positive), though technically (in Linux) it is unlimited.

If you need to merge more files, look into the command xargs.

---

### Post by dwhitney67 on 2009-06-13
> **Krupski said:**
> ... HOW MANY can there be before I hit some limit?

Is there such a thing as argv[100]? How about argv[10000]?

How far does it go? 

And if there is a limit, can that limit be changed?

Thanks in advance!

-- Roger

If someone here had posted that the limit is 10326 args, would you retain that little morsel of information in your head?  Seriously, what purpose would knowing this limit serve you?  Would you ever pass hundreds, or even thousands of command line args to an application?

I'd wager that there are perhaps better questions that one could pose here on the forums... but my hopes are dwindling.

---

### Post by Bodsda on 2009-06-13
> **dwhitney67 said:**
> If someone here had posted that the limit is 10326 args, would you retain that little morsel of information in your head?  Seriously, what purpose would knowing this limit serve you?  Would you ever pass hundreds, or even thousands of command line args to an application?

I'd wager that there are perhaps better questions that one could pose here on the forums... but my hopes are dwindling.

And because you can see no use for the answer to his question, you deem such a question unworthy of being asked... interesting.

---

### Post by Krupski on 2009-06-13
> **dwhitney67 said:**
> Would you ever pass hundreds, or even thousands of command line args to an application?

I'd wager that there are perhaps better questions that one could pose here on the forums... but my hopes are dwindling.

Of course I wouldn't pass hundreds of arguments... probably not even ten.

I was simply curious if there WAS a limit and, if so, what it was and, if so could it be changed.

Since you are normally very helpful and obviously very knowledgeable, I won't gripe about the tone of your post. We all have "a bad day" once in a while.  :)

You've helped me lots in the past and I appreciate it.

On that note... I'm surprised you didn't point out that my little utility fails to check the file pointer for NULL (if a command line filename didn't exist - the program would segfault).

;)

-- Roger

---

### Post by Krupski on 2009-06-13
> **Bodsda said:**
> And because you can see no use for the answer to his question, you deem such a question unworthy of being asked... interesting.

Don't worry about it. I'm not.

-- Roger

---

### Post by Krupski on 2009-06-13
> **dwhitney67 said:**
> If someone here had posted that the limit is 10326 args, would you retain that little morsel of information in your head?

Yes, actually I would. Of course, I would wonder why it was an oddball number like 10326 and not 10240 or 16384 or something more.... binary...  :)

---

### Post by stroyan on 2009-06-13
The actual limit on argv is a limit on the total bytes used to represent both the argv and env values for an exec call.
You can inquire that limit with ```

#include <unistd.h>
long max = sysconf(_SC_ARG_MAX);

```
or with a "getconf ARG_MAX" command.

---

### Post by Lux Perpetua on 2009-06-14
> **dwhitney67 said:**
> If someone here had posted that the limit is 10326 args, would you retain that little morsel of information in your head?  Seriously, what purpose would knowing this limit serve you?  Would you ever pass hundreds, or even thousands of command line args to an application?It's quite germane, actually. If the program is being run from a script, there may be nothing preventing the command line from reaching sizes no human could manually enter on a shell prompt. If there were some unobvious limit on the number of arguments, one would need to be aware of it (if not by knowing the exact number, then at least by knowing that there was a limit) when designing shell scripts. It's not hard to imagine that someone, somewhere, at some time would create an operating system in which the length of argv was limited to, say, 256, an ostensibly reasonable but shortsighted restriction. The GNU/Linux folks did not, but I wouldn't take it for granted. 
[quote=dwhitney67]I'd wager that there are perhaps better questions that one could pose here on the forums... but my hopes are dwindling.[/QUOTE]A bit ironic, perhaps? ;)

---

### Post by Linuxidiot on 2009-06-14
Hello, this is a little off topic from what you are chatting about but the forum thread says this is where to post my question. I am interested in learning how to program with python, my current python is 2.6,. I was wondering if there is some kind of interactive programming tool I could use to help me learn how to actually program. When I read up on all the programming languages I decided this one would be the best to learn first. I learn the best from actually doing it. Ive read tutorials but I am completely new to programming and dont really know what any of it means, so if you guys could give me a "programmers guide for retards" It would be very helpfull, thanks guys

---

### Post by ibuclaw on 2009-06-14
The **_POSIX_ARG_MAX** looks to be **4096** as defined in "bits/posix1_lim.h" that is used by "limits.h"


The **ARG_MAX** looks to be **131072** as defined in "linux/limits.h"

And **sysconf(_SC_ARG_MAX)** returns **2097152**



Either way, the number is far greater than what you will ever need.

Regards
Iain

---


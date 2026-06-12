---
title: "Probably stupid compiling question"
date: 2008-03-14
forum: Packaging and Compiling Programs
---

### Post by shingalated on 2008-03-14
For my C class our teacher wants us to use visual studio, but obviously there is no visual studio on Linux, and I think I like anjuta better anyway.  My question is why do none of my programs execute correctly?  Do I need to make some kind of header file.  The main.c file looks fine as far as I can tell.  I write that, compile that in GCC and run the a.out it creates.  I get the menus and prompts in my programs but as soon as I enter anything, I get "Segmentation fault (Core dumped)"  I get this on several computers regardless of OS.

---

### Post by jaddle on 2008-03-14
A segmentation fault (segfault) is generally a sign that your program is writing something to a bit of memory that it shouldn't. Here's a simple example:

int main() {
   *s = malloc(5);
   s[20] = 'q';
}

This will probably segfault, or maybe screw up in some other way, because it tries to write to some memory that hasn't been allocated yet. Check your program carefully to see if there's some spot where it's writing beyond the end of an allocated buffer.

gdb (gnu debugger) can be very helpful for tracking down these problems. In this case, if I compiled this program to an executable called 'crasher', and then ran 'gdb crasher', I'd get a prompt. Typing 'run' will then run the program and, when it crashes with the segfault, it should give a bit more information about where it was when it crashed, and what it was trying to do. You can also use gdb to step through the program one line at a time, and set breakpoints, examine the contents of variables, etc.. It's a very useful tool!

---

### Post by shingalated on 2008-03-15
I don't know if I really need malloc.  I am in a very basic C class.  Do you need malloc in something as simple as these 18 line of code?
```
v#include <stdio.h>
int main()
{
	int n = 0;
	printf("Please enter a number\n");
	scanf("%d", n);
	int CalcFib (int n)
	{
    	if ( n >= 1 )
		{
			return 1;
		}
    	else
		{
			return ( CalcFib ( n - 1 ) + ( CalcFib ( n - 2 ) ) ) ;
		}
	}
}

```

---

### Post by 2161warrior on 2008-03-15
Just a note, but I believe VS can run on [[COLOR="Blue"]Wine[/COLOR]]("http://winehq.org").

2161

---

### Post by KaeseEs on 2008-03-15
> **shingalated said:**
> I don't know if I really need malloc.  I am in a very basic C class.  Do you need malloc in something as simple as these 18 line of code?
```
v#include <stdio.h>
int main()
{
	int n = 0;
	printf("Please enter a number\n");
	scanf("%d", n);
	int CalcFib (int n)
	{
    	if ( n >= 1 )
		{
			return 1;
		}
    	else
		{
			return ( CalcFib ( n - 1 ) + ( CalcFib ( n - 2 ) ) ) ;
		}
	}
}

```

You have a couple of problems here.  First is the scanf(), which needs an address to put the data it reads, so instead of```
scanf("%d", n);
```you want:```
scanf("%d", **&**n);
```

The next issue is that your function declaration is quite odd.  The normal way to do this would be to define the function first, then call it:
```

#include <stdio.h>

int CalcFib (int num)
{
		if ( num >= 1 )
		{
				return 1;
		}
		else
		{
				return ( CalcFib ( num - 1 ) + ( CalcFib ( num - 2 ) ) ) ;
		}
}

int main()
{
		int n = 0;
		printf("Please enter a number\n");
		scanf("%d", &n);
		CalcFib(n);

		return 0;
}
``` (note that I also added a return statement to your main() function, which was lacking one)

Now, in testing I find that your program still segfaults if you enter a negative number at the prompt, as I expected - the reason is that your CalcFib() function enters infinite recursion (which will run you out of stack eventually, although that's probably a bit over your head).  To see this, add a bit of debug output, like so:```
#include <stdio.h>

int CalcFib (int num)
{
		static int runs;//declared static, so auto-initialized to 0
		
		if ( num >= 1 )
		{
				return 1;
		}
		else
		{
				++runs;
				fprintf(stderr, "Ran %d times\n.", runs);
				return ( CalcFib ( num - 1 ) + ( CalcFib ( num - 2 ) ) ) ;
		}
}

int main()
{
		int n = 0;
		printf("Please enter a number\n");
		scanf("%d", &n);
		CalcFib(n);

		return 0;
}
```

On my machine, this dies after it runs 261616 times(you may want to minimize the window you're running it in and wait a minute if you try this code, as the I/O takes _much_ longer than arithmetic, slowing down the recursive 'loop',  and it will take more time to segfault).

Now, the fix you want here is to figure out what CalcFib() is supposed to do, figure out how to do this, and then decide what you want to do with the return value (probably output it with printf(), but whatever works).


Now, some final notes - the compiler would have told you about some of these things (the scanf() especially) if you had told it to!  Here's the best way to compile a program while you're still developing and debugging it:```
gcc filename.c -o programname -Wall -g
``` The **-Wall** switch enables all compiler warnings, while the **-g** switch tells the compiler to keep symbol (variable & function names, line labels) information in the executable.  This way, if you run the program through **gdb** to analyze a crash, it can tell you all these things.

---

### Post by Arwen on 2008-03-15
Just a note about gdb.When you type "backtrace", when you run gdb and right after your program crashed, it might give you more details(actually it helped me a lot with pointers).

---

### Post by shingalated on 2008-03-15
Thanks guys :-D  For some reason I thought it was related to header files, but I'm pretty new at this, and my teacher is zero help.

---


---
title: "segmentation fault problem"
date: 2011-05-19
forum: Programming Talk
---

### Post by maohacker on 2011-05-19
im having a problem with a basic program.
 i try to receive integer values from the prompt, copy it in an array and then print it to the screen.
 But i have a segmentation fault, i dont even know what is this this kind of error.

```

#include <stdio.h>
#include<stdlib.h>
#include<ctype.h>
#define N_PROC_MAX 10
#define N_PROC_MIN 3



int main (int argc, char *argv[])
{
	int i, j, n, count, tab[N_PROC_MAX];
	
	if( (argc<N_PROC_MIN) || (argc>N_PROC_MAX ) ){
		printf("The command should receive from %d to %d argument(s)\n", N_PROC_MIN,N_PROC_MAX);
		exit(0);	
	}
	
	for (i=0; i<argc; i++)
		tab[i]=atoi(argv[i+1]);
	
	for (i=0; i<argc; i++)
		printf("%d ", tab[i]	);
}


```

---

### Post by Zugzwang on 2011-05-19
```

for (i=0; i<argc; i++)
		tab[i]=atoi(argv[i+1]);

```

Why do you use "i+1" instead of "i" here? This way, you are trying to access one element *after* the last one.

Also, consider using a debugger to execute your program step-by-step to find such problems in the future.

---

### Post by maohacker on 2011-05-19
thanks, it works! which step by step debugger could you advice me to use, you should have noticed that im begginer.

---

### Post by Zugzwang on 2011-05-19
> **maohacker said:**
> thanks, it works! which step by step debugger could you advice me to use, you should have noticed that im begginer.

That depends on your environment. Are you using Windows, Linux, Solaris, or something else? In Linux, there are a lot of GNU debugger (gdb) frontends. Personally I like qtcreator's one, but it's a matter of taste. I've heard that there are also good stand-alone ones. Perhaps you already have an eclipse environment installed? In that case, the choice is obvious (use eclipse's frontend).

By the way: Capitalization helps to increase the readability of your posts.

---

### Post by nvteighen on 2011-05-19
A segmentation fault (segfault) occurs when your program tries to access some data that's outside of its own current stack frame. Usually, it's triggered by dereferencing an uninitialized pointer, whose value is undefined and happens to point some memory region that's not owned by your program (which is the most likely case).

And that's what you were doing, although indirectly. Accessing an array is an operation that works by dereferencing a pointer (**a[noparse][i][/noparse]** is equivalent to ***(a + i)**). If an array is of length 5 and you try to access something "after" a[4], e.g. a[5], you'll be actually trying to access a region of memory that might not be yours.

Sometimes, instead of a segfault you get garbage data... that happens when the undefined pointer is casually valid and allows you to access some data... :P

---

### Post by Arndt on 2011-05-19
> **nvteighen said:**
> A segmentation fault (segfault) occurs when your program tries to access some data that's outside of its own current stack frame. Usually, it's triggered by dereferencing an uninitialized pointer, whose value is undefined and happens to point some memory region that's not owned by your program (which is the most likely case).

And that's what you were doing, although indirectly. Accessing an array is an operation that works by dereferencing a pointer (**a[noparse][i][/noparse]** is equivalent to ***(a + i)**). If an array is of length 5 and you try to access something "after" a[4], e.g. a[5], you'll be actually trying to access a region of memory that might not be yours.

Sometimes, instead of a segfault you get garbage data... that happens when the undefined pointer is casually valid and allows you to access some data... :P

Your explanation is correct, but I guess that in this case accessing one cell beyond the end of argv gets you NULL (something I think is always the case, but not something you should rely on, or maybe I'm thinking of envp), and then atoi when given NULL is the one which generates the segmentation violation.

---

### Post by JupiterV2 on 2011-05-19
Accessing out-of-bounds memory is, if I'm not mistaken, considered "undefined" behaviour and can result, as nvteighen suggests, in either a segfault or garbage data. It is up to the compiler how to deal with it because the C standard does not stipulate how that particular situation should be handled. 

It's worthwhile reading '[What Every C Programmer Should Know About Undefined Behavior]("http://blog.llvm.org/2011/05/what-every-c-programmer-should-know.html")' for both novice and experienced programmers. I know I'm guilty of at doing some of those "tricks" at least once.

---

### Post by nvteighen on 2011-05-19
> **Arndt said:**
> Your explanation is correct, but I guess that in this case accessing one cell beyond the end of argv gets you NULL (something I think is always the case, but not something you should rely on, or maybe I'm thinking of envp), and then atoi when given NULL is the one which generates the segmentation violation.

I wouldn't rely on that. Maybe it works that way in some platform, but the C Standard leaves that as undefined... which is the worst possible programming scenario: not knowing what the consequences of a certain action will actually be! (I tend to analyze this as the lack of any interface, but that's just me and my obsession on interface-semantics :P).

---

### Post by Barrucadu on 2011-05-19
For future reference, you can use valgrind to help debug things like this.

---

### Post by maohacker on 2011-05-20
thanks for all your explanations guys, it helped me to understand a bit about Segmentation Fault, but not enough to understand MY NEW PROBLEM.
      i am trying to call an call an "xmessage" command via an "execv" call, but my aim is to modify some elements of the arguments vector with a strcopy function, but the strcpy generate a segment fault. 
  here is the stuff.

```

#include <stdio.h>
#include<stdlib.h>
#include<sys/types.h>
#include<sys/wait.h>
#include<string.h>
//#include<ctype.h>

int main (){
    char tmp[30];
    char* msg[]={"xmessage", "i have  got ","12345", " millions USD", (char *)0};
    // the string 12345 is to avoid a NULL pointer
    
    strcpy(msg[2], "20");
    
    printf("%s%s%s", msg[0],msg[1],msg[2]);   // print an overview
    execv("/usr/bin/xmessage", msg);
    printf("\n This msg should not be print if success!!");
    
    return 0;
}

```

[SIZE=3]***once more thanks for all guys***[/SIZE]

---

### Post by dwhitney67 on 2011-05-20
You should declare the following line to indicate that it is an array of const char pointers.
```

**const** char* msg[]={"xmessage", "i have  got ","12345", " millions USD", (char *)0};

```
This would imply to you (and the compiler) that the strings cannot be changed.

If you want to replace the third string with another literal, then in lieu of the strcpy(), use the assignment operator.
```

msg[2] = "20";

```

P.S.  With the above in mind, the declaration of msg can now be:
```

const char* msg[]={"xmessage", "i have  got ", NULL, " millions USD", NULL};

```

---

### Post by maohacker on 2011-05-20
now it runs well,
thanks very much.
THANKS!

---

### Post by JupiterV2 on 2011-05-20
I would also suggest that, in the future, you use strncpy() over strcpy() as its a bit safer.

---

### Post by cgroza on 2011-05-20
> **JupiterV2 said:**
> I would also suggest that, in the future, you use strncpy() over strcpy() as its a bit safer.
What is the difference?

---

### Post by dwhitney67 on 2011-05-20
> **cgroza said:**
> What is the difference?

Using strcpy() (and gets(), sprintf(), etc) can pose a risk to the application.

Consider the following:
```

char server_name[8];

printf("Enter the server name: ");
scanf("%s", server_name);

/* or */

gets(server_name);

```
Now imagine if the user enters a server name like **foo.at.domain.com**. What will happen to the server_name buffer?

Similarly, with strcpy().
```

int main(int argc, char** argv)
{
   char server_name[8];

   if (argc < 2)
   {
      printf("Usage: %s <server>\n", argv[0]);
      return -1;
   }

   strcpy(server_name, argv[1]);

   ...
}

```
strncpy(), fgets(), snprintf(), etc allow for the programmer to specify the size of the buffer, thus mitigating the possibility that some user will attempt to thwart the application by inserting a huge string.

The principles discussed above are considered basic concepts of "Information Security" (or "Information Assurance").

---


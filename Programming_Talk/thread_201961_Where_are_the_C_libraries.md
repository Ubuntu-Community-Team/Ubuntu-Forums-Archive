---
title: "Where are the C libraries?"
date: 2006-06-22
forum: Programming Talk
---

### Post by bb2120 on 2006-06-22
First of all, hi everyone. 
After managing to install Ubuntu (which was a lot easier than I expected), I am now having trouble compiling hello.c into a binary. Oh dear.

The first hurdle was realising I needed to *sudo apt-get install gcc*
However, now when I try *cc hello.c* I get the following message in the terminal:

[I]hello.c:1:19: error: stdio.h: No such file or directory
hello.c: In function ‘main’:
hello.c:5: warning: incompatible implicit declaration of built-in function ‘printf’[/I]

I presume that this is due to the lack of the stdio.h library.

**Could someone please explain to me what I need to do to be able to compile c programs**. I have a solid knowledge of programming (mainly php), but don't expect me to know my way around Ubuntu. 

P.S. I'm running Breezy Badger

---

### Post by glinsvad on 2006-06-22
```

sudo apt-get install build-essential

```

It includes libc-dev, gcc, g++, make and dpkg-dev which should suffice for C/C++ programming. For downloadable documentation also check out glibc-doc and libstdc++6-4.0-doc...

---

### Post by bb2120 on 2006-06-22
Thaks for the quick reply but there are more problems...

[I]bede@bedepc:~$ sudo apt-get install build-essential
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[/I]

What do I do now? I presume I'm having problems because I did *sudo apt-get install gcc* which installed half of the stuff that *build-essential* does.

Is there any way to completely undo *sudo apt-get install gcc* so that I can *sudo apt-get install build-essential* without problems? Or is that not worth doing?

---

### Post by glinsvad on 2006-06-22
Usually I only get those kinds of install-errors when I'm running Synaptics while using apt-get... just kill Synaptics and rerun the command

---

### Post by bb2120 on 2006-06-22
Problem solved. Glinsvad, I love you (Don't get any ideas, though)

---

### Post by Monika on 2006-06-23
I have the same problem, but build-essential hasn't solved it :( Any ideas what other packages I might be missing?

---

### Post by glinsvad on 2006-06-23
[QUOTE=Monika]I have the same problem, but build-essential hasn't solved it :( Any ideas what other packages I might be missing?[/QUOTE]

Could you describe the problem? Is it when running gcc/g++ or installing through apt-get? What error messages do you see?

---

### Post by glinsvad on 2006-06-23
For easy reference I'm giving the Hello-example

Create a file called hello.cpp with the following code:
```

#include <iostream>
using namespace std;

int main(int nArgs, char **szArgs)
{
cout<<"Hello" <<endl;
}

```

Now to compile it, run this command:
```

g++ hello.cpp -o hello

```

Finally run the program
```

./hello

```

---

### Post by Monika on 2006-06-23
I'm still getting the same compilation errors that bb2120 had before the install:
> hello.c:1:20: error: studio.h: No such file or directory
hello.c: In function ‘main’:
hello.c:4: warning: incompatible implicit declaration of built-in function ‘printf’


The install has improved the situation cause I remember having these same problems compiling programs in C++ before (haven't tried for a while) and now it *does* work :D But I still don't have the libraries for C apparently.

In case you want to check if it's not a mistake on my end (I am a beginner), the program looks like this:
```
#include <studio.h>

int main() {
	printf("Hello");
	return 0;
}
```

And I'm trying to compile it like this:
```
gcc hello.c -o hello
```

Thanks for your help :)

---

### Post by hod139 on 2006-06-23
It's 
```
<stdio.h>
```
not 
```
<studio.h>
```
(no u)

---

### Post by bb2120 on 2006-06-23
It's an easy mistake to make. It's an abbreviation of Standard I/O

---

### Post by Monika on 2006-06-23
](*,) 

Thanks for pointing that out! :)

---

### Post by Jessehk on 2006-06-23
> 
```

#include <iostream>
using namespace std;

int main(int nArgs, char **szArgs)
{
cout<<"Hello" <<endl;
}

```


That is not really good C++. 

This is an ideal "Hello, world" program:

```

#include <iostream>

int main() {
    std::cout << "Hello, world!" << std::endl;
}

```

and in C:
```

#include <stdio.h>

int main(void) {
    printf("Hello, world!\n");

    return 0;
}

```

:)

---

### Post by glinsvad on 2006-06-23
> 
That is not really good C++. 


Eeeh, our two examples in C++ do exactly the same thing. If the program only uses the standard (std) namespace, then what's the problem? I recent having to do ten extra keypresses (two times "std::") every time I print something to the screen. Besides, it was taken directly out of an official C++ textbook...

---

### Post by mepapp on 2006-06-25
hello. I just installed build-essential and compiled a "hello world" successfully. However, upon compiling a more complex program, gcc failed to find either stdio.h or math.h. As background: I had the exact same problem before, with Breezy: it worked for a little while and suddenly the files just disappeared. I updated to Dapper thinking it would fix the problem. Again, brief success followed by failure. I have tried reinstalling libc6 but that hasn't helped. 

My program(from a c tutorial):
```
#include < stdio.h>
#include < math.h>

int main() 
{
	int	angle_degree;
	double	angle_radian, pi, value;
	printf ("\nCompute a table of the sine function\n\n");
	pi = 4.0*atan(1.0);
	printf ( " Value of PI = %f \n\n", pi );
	printf ( " angle      Sine \n" );
	angle_degree=0;
	while ( angle_degree <= 360 )
	{
		angle_radian = pi * angle_degree/180.0; 
		value = sin(angle_radian);
		printf ( " %d     %f \n ", angle_degree, value );
		angle_degree = angle_degree + 10;
	}
	return 0;
}	

``` 

My (repeated) error message:
```
$ gcc hello.c -lm
hello.c:1:20: error:  stdio.h: No such file or directory
hello.c:2:19: error:  math.h: No such file or directory
hello.c: In function ‘main’:
hello.c:8: warning: incompatible implicit declaration of built-in function ‘printf’
hello.c:12: warning: incompatible implicit declaration of built-in function ‘atan’
hello.c:22: warning: incompatible implicit declaration of built-in function ‘sin’

```

---

### Post by mepapp on 2006-06-25
Incidentally, this doesn't work (now) either:

```
#include < stdio.h>

int main() 
{
	printf("Hello World!");
	return 0;
}	

```

because

```
~$ gcc hello.c
hello.c:1:20: error:  stdio.h: No such file or directory
hello.c: In function ‘main’:
hello.c:5: warning: incompatible implicit declaration of built-in function ‘printf’

```

---

### Post by mepapp on 2006-06-25
Apparently libc6-dev is the package I'm looking for, but rebuilding that makes no difference.

---

### Post by mepapp on 2006-06-25
Someone take me out the backdoor and put me out of my misery....


The ()/$%&§$§/!!! spaces in [this]("http://www.physics.drexel.edu/courses/Comp_Phys/General/C_basics/c_tutorial.html") tutorial led me to reinstall my girlfriend's whole system, and delete many files when space became a premium etc. etc. etc.

Trust the packages first, your own code second.

thanks lamego (on irc), whoever you are

---

### Post by glinsvad on 2006-06-25
True, the tutorial is pretty lame. Just to pencil it out so everybody will know what went wrong:

It is:
```

#include <stdio.h>

```

Not:
```

#include < stdio.h>

```

No space in front of stdio.h! The compiler is told to look for a file called " stdio.h" but the correct library is in "stdio.h"...

EDIT: Same problem with #include < math.h>

---


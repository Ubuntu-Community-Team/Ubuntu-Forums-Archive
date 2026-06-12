---
title: "Problem With Compiler :/ (gcc)"
date: 2009-04-11
forum: Programming Talk
---

### Post by Ben Crisford on 2009-04-11
Solved now guys, thanks loads for replying so quickly and constructively.

Its the community that makes ubuntu what it is :D.

Thanks,
Ben :)

------------------------------------

I am having trouble with GCC... :(

I'm new to C and I have written a blackjack program but it won't compile...  However, it does compile for other people using the same compiler and the same command, just not me :/.

I am using this command:
```
gcc blackjack.c -g -o blackjack
```
Yes - i'm in the right dir.
And yes it is saved :D.

Using the exact same command my friend can compile the same program...

The error I get is:
```
blackjack.c:4: error: expected identifier or &#8216;(&#8217; before &#8216;{&#8217; token

```

Here is my code, but I don't think it can be a problem with that because it works for my friend:
```
#include <stdio.h>

int main() {
	int play;
	int deal;

	printf ( "Welcome to Ben's blackjack game!\n" );
	printf ( "Would you like to play (1 = yes or 2 = n0)\n" );
	scanf ( "%d", &play );
	if ( play == 1 ) {
		printf ( "Type 3 to deal, or type 4 for help\n" );
		scanf ( "%d", &deal );
		if ( deal == 4 ) {
			printf ( "In blackjack, the player aims to get 21 points each deal.  They do this by getting cards of different values\n but if the player gets over 21 then they are bust, which means they get 0\n" );
		}
		else {
			printf ( "Invalid Command\n" );
		}
    }
    else if ( play == 2 ) {
		printf ( "Ok then, bye!\n" );
    }
    else {
	printf ( "Invalid Command\n" );
	}
}
```

Any idea whats wrong.

Cheers,
Ben

---

### Post by dwhitney67 on 2009-04-11
Nothing is wrong with the syntax of the program; it compiles fine.

Thus, either you do not have GCC installed on your system or you have a bum installation of such.

Try installing GCC first:
```

sudo apt-get install build-essential

```

---

### Post by Ben Crisford on 2009-04-11
> **dwhitney67 said:**
> Nothing is wrong with the syntax of the program; it compiles fine.

Thus, either you do not have GCC installed on your system or you have a bum installation of such.

Try installing GCC first:
```

sudo apt-get install build-essential

```

I did that before I even did helloworld.

I tried again today and it said it was already installed...

---

### Post by iponeverything on 2009-04-11
try:

```
sudo apt-get install tofrodos
```

```
dos2unix blackjack.c
```

then try to compile it.

---

### Post by dwhitney67 on 2009-04-11
I do not know what to say then.  If you were able to build a "hello world" app without any trouble, then the only other possibility I can think of is that perhaps you have a hidden control-character in your latest code.

I merely copied/pasted what you posted, and as I stated, it compiled fine.  Try to do the same as I did, into another file, and try to compile it.

P.S.  I used vim and the command line to compile the program.

---

### Post by Arndt on 2009-04-11
> **Ben Crisford said:**
> I did that before I even did helloworld.

I tried again today and it said it was already installed...

Make sure gcc really is what you think: do "which gcc". Also, you can invoke it like this: "gcc --version" and let it tell you what it is. Maybe we will get a hint. I find the error message quite strange, as if it was about another language.

Another possibility is that some strange character has gotten into the code, which confuses the compiler, without even being visible when printed. If you copy/pasted the program normally here, it shouldn't be the case, but one never knows.

Next (or why not first), reduce your program to the barest minimum which still gives the error.

After that, there are verbosity flags you can give gcc to make it say what steps it is invoking while compiling. Compare that output with that from your friends.

---

### Post by stroyan on 2009-04-11
Differences in header files and cpp macros could produce that error.
A macro could map "main" into gibberish.
Of course, your system should have the same stdio.h as everyone else.
But something is very strange about your system.  Perhaps that is it.
You can use "gcc -E blackjack.c" to see exactly what the header file and cpp macros have done to the source code.

---

### Post by Flareside on 2009-04-11
Try specifying the language by adding -x c to specify that the language is C. If you don't specify the language like that, it tryies to guess what language your using, and I have found it's guessing ability to be disappointing. I get errors similar to the one you got whenever I try to compile things in C++ without specifying -x c++.

For example, when I compile things the command looks like this: gcc -x c++ -o '/path/to/output/file' '/file/to/be/compiled'

---

### Post by dwhitney67 on 2009-04-11
> **Flareside said:**
> Try specifying the language by adding -x c. If you don't specify the language like, that it tryies to guess what language your using, and i have found it's guessing ability to be disappointing. I get errors similar to the one you got whenever I try to compile things in C++ without specifying -x c++.

You should not have to do this; use 'gcc' to build C programs, and 'g++' to build C++.  If you want to use 'gcc' to build a C++ program, then specify the stdc++ library (-lstdc++).  Most people do not use 'gcc' as such to build their C++ apps.

The problem you are experiencing is that you are probably not following convention by using a file extension known by gcc/g++.  For C code, this is typically .c and for C++, either .cpp, .cc, or .C.  The usage of .cpp is the most common.

---

### Post by Ben Crisford on 2009-04-11
Thanks everyone for your replies.

I sorted it now, turns out it was just all the pastebins and copy/pastes for my friends had messed up the code without me knowing.

But its solved now, and thanks again.

Ben :D.

---

### Post by Flareside on 2009-04-11
I always save my files as .cpp, and even with g++ I still get occasional errors if I don't specify C++, so I've just got into the habit of adding -x c++ whenever I compile something.

---


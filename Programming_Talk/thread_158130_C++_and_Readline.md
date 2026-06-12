---
title: "C++ and Readline"
date: 2006-04-10
forum: Programming Talk
---

### Post by pianoboy3333 on 2006-04-10
What's with readline, I can't seem to get it to work, here's what I tried:

```

#include<stdio.h>
#include<readline/readline.h>
#include<readline/history.h>
#include<iostream>
#include<string>

int main(){

	char asdf=readline("# ");

	return 0;
}

```

---

### Post by rplantz on 2006-04-10
[QUOTE=pianoboy3333]What's with readline, I can't seem to get it to work, here's what I tried:

```

#include<stdio.h>
#include<readline/readline.h>
#include<readline/history.h>
#include<iostream>
#include<string>

int main(){

	char asdf=readline("# ");

	return 0;
}

```[/QUOTE]

readline returns a char *. Your variable, asdf, is a char. Don't forget to allocate the memory that your char * points to before you call readline.

---

### Post by pianoboy3333 on 2006-04-10
[QUOTE=rplantz]readline returns a char *. Your variable, asdf, is a char. Don't forget to allocate the memory that your char * points to before you call readline.[/QUOTE]

so use char * asdf=readline("# "); ? How do I allocate memory?

---

### Post by pianoboy3333 on 2006-04-10
When I do char * asdf=readline("# "); I get the error:

```

/tmp/ccIv9qtJ.o: In function `main':test.cc:(.text+0x24): undefined reference to `readline'
collect2: ld returned 1 exit status

```

---

### Post by rplantz on 2006-04-10
Okay, I take back what I said about having to allocate space for the text string. I've never used readline before, and some exploration indicates that it allocates the space itself. You **definitely** want to check this out!

I had to install libreadline5-dev, which I did using synaptic. It included libncurses5-dev as a dependency.

Next, I had to specify the readline library when compiling with the -lreadline option:```

$ g++ -lreadline readln.cc

```

Here's the program I used to test this:```

// added memory deallocate -- 4/12/06
#include<stdio.h>
#include<readline/readline.h>
#include<readline/history.h>

int main(){

   char* asdf = readline("# ");
   printf("You entered: %s\n", asdf);
   free(asdf);
   return 0;
}

```

Again, I've never used readline in a program, so please double-check everything I've said here. I did not test my program to see if readline works as advertised.

From the very little I read about readline while figuring this out, it looks interesting. I learned something new today. :) I would appreciate any pointers to places where I can learn more about readline.

---

### Post by tomchuk on 2006-04-10
EDIT: Oops, beaten to the punch. 
rplantz - the readline info page is a pretty good source: lots of info, examples, etc.

Don't worry about allocating memory, from readline(3):
```

The line returned is allocated with malloc(3); the caller must free it when finished.

```

foo.c:
```

#include <stdio.h>
#include <readline/readline.h>
#include <readline/history.h>

int
main ()
{
    char *foo = readline("# ");
    printf("%s\n", foo);
    return 0;
}

```

compile with:
```

gcc -Wall -lreadline -ofoo foo.c

```

---

### Post by thumper on 2006-04-11
Why is the post topic C++ and the examples all C?

If you are looking for a C++ way, then don't use readline.

---

### Post by pianoboy3333 on 2006-04-11
[QUOTE=thumper]Why is the post topic C++ and the examples all C?

If you are looking for a C++ way, then don't use readline.[/QUOTE]

What do you suggest I use then?

*EDIT* rplantz example works fine....

---

### Post by thumper on 2006-04-11
```
#include <string>
#include <iostream>

int main()
{
   std::string line;
   while (std::getline(std::cin, line)) 
   {
      if (line == "quit") 
      {
         std::cout << "Bye\n";
         break;
      }
      else std::cout << "echo: " << line << '\n';
   }
}

```

Caveat: untested code.

---

### Post by LordHunter317 on 2006-04-11
[QUOTE=thumper]Caveat: untested code.[/QUOTE]It's uncomparable anyway. readline() does infinitely more than read a line, it's the command-line editing library most code applications use.  

Now, to be fair, if you're jsut using it for the former application, thumper's code works fine.  If you're not, there is no equivalent C++ library I'm aware of, nor would you want to write one.

---

### Post by rplantz on 2006-04-11
This is very cool. After reading very little of the info on readline, it was very simple to modify my program so that I could maintain a history of previously entered lines. The other thing I realized is that I can edit a line using the arrow keys instead of deleting characters and typing them over again.

I have to admit that my initial response to pianoboy3333's question was "dumb question" and I almost gave a response like thumper's. But I was a CS professor for 21 years, where I learned a lot from my students' "dumb questions." First, they asked things that I didn't even know about. (Such is the case here. I had never heard of readline before.) Second, I had to then learn about the topic in order to avoid embarrassing myself in front of an entire class of students. (Still did that a few times. :) )

Thanks for raising the question and for the responses.

---

### Post by pianoboy3333 on 2006-04-11
[QUOTE=thumper]```
#include <string>
#include <iostream>

int main()
{
   std::string line;
   while (std::getline(std::cin, line)) 
   {
      if (line == "quit") 
      {
         std::cout << "Bye\n";
         break;
      }
      else std::cout << "echo: " << line << '\n';
   }
}

```

Caveat: untested code.[/QUOTE]

This would have been my last resort, but with readline() you can also interact with things such as Ctrl-T to do something...

A fine example is at [http://piano.juicemedia.tv/rlexample.cc]("http://piano.juicemedia.tv/rlexample.cc")
Compile it with `g++ rlexample.cc -o rlexample -lreadline'

---

### Post by thumper on 2006-04-12
None of the examples (above, or the example posted above) actually free the memory that readline allocates.

According to the man page readline mallocs the memory and it is up to the caller to free it.  Make sure you do.  Assigning it to a string does not free the memory.

---

### Post by rplantz on 2006-04-12
[QUOTE=thumper]None of the examples (above, or the example posted above) actually free the memory that readline allocates.

According to the man page readline mallocs the memory and it is up to the caller to free it.  Make sure you do.  Assigning it to a string does not free the memory.[/QUOTE]

Thanks. I saw that later when I read more on the man page. I added the free() to my very simple example above.

---


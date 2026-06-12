---
title: "compile C ( with gcc ) lil problem.."
date: 2008-01-01
forum: Packaging and Compiling Programs
---

### Post by shadows123 on 2008-01-01
Hey everyone!
i am trying to compile a simple C file with GCC..
I'll show you..
This is the file with code:
```
print("Hello, world!\n");
```
maybe it's wrong idk lol..
then i try:
```
kevin@Kevin-PC:~$ gcc Desktop/hworld.c -o Desktop/test/lol.c
/tmp/ccs9W3GN.o: In function `main':
hworld.c:(.text+0x19): undefined reference to `print'
collect2: ld returned 1 exit status
kevin@Kevin-PC:~$ gcc Desktop/hworld.c -o Desktop/test/lol.c
/tmp/ccwy6O1P.o: In function `main':
hworld.c:(.text+0x19): undefined reference to `print'
collect2: ld returned 1 exit status
```
Idk..
it was just lil test to understand how it works..
Thanks!

---

### Post by revanthedarth on 2008-01-01
C codes aren't that simple, you need a main function. And, there is no print function, but there is printf, which is what you tried to use. For example:

```

#include <stdio.h>
int main()
{
	printf("Hello, World\n");
}

```
This code should work.

By the way, do not make your output files *.c . Use *.o for it. For example,
```

gcc test.c -o output.o

```
That won't confuse you. And, to run the app you just created, type 
```

./output.o

```
gcc makes a.out by default.

---

### Post by LaRoza on 2008-01-01
See [http://laroza.wikidot.com/one](http://laroza.wikidot.com/one) for how to compile and run a C program in Ubuntu.

[http://laroza.wikidot.com/c](http://laroza.wikidot.com/c)

---

### Post by shadows123 on 2008-01-01
Hmm
few questions lol :p

==> If we do like myvar=what he enters. how can you do that? lol..
like.. you can define myvar = 100, but what do you have to do that it's what he types?

==> Is it possible to just click on it to run? or you have to make it .deb ?

==> What's the return function used for?

==> How to do that when he enters text, after he entered, the app says something.. i did try like return printf("lol") but it just shows lol before entering something..

==> [#include <stdio.h>] How to know what to include? lol..

Hey thanks guys!
I learn a lot :p

---

### Post by LaRoza on 2008-01-01
> **shadows123 said:**
> Hmm
few questions lol :p

==> If we do like myvar=what he enters. how can you do that? lol..
like.. you can define myvar = 100, but what do you have to do that it's what he types?

==> Is it possible to just click on it to run? or you have to make it .deb ?

==> What's the return function used for?

==> How to do that when he enters text, after he entered, the app says something.. i did try like return printf("lol") but it just shows lol before entering something..

==> [#include <stdio.h>] How to know what to include? lol..

Hey thanks guys!
I learn a lot :p

See my wiki, the one in my sig, for C tutorials.

Usually, you run it in the terminal, so you can click on it and run in the terminal. Be aware it will close when it is finished.

The return function (isn't really a function) but it gives the exit code of the program. Run a program, any program, from the terminal. Close it. Then type in the terminal:

```

echo $?

```

It will give the programs status. 0 is used for success.

The standard functions are in only a few headers. The wiki in my sig has tutorials and library references for C.

Here is a little example of bad C code, but it is simple enough to follow:

[php]
#include <stdio.h>

int main(int args,char ** argv)
{
    char name[20];
    puts("What is your name? ");
    gets(name);
    printf("Hello %s, welcome to C\n",name);
    return 0;
}
[/php]

You will get a warning when you compile that.

---

### Post by shadows123 on 2008-01-01
0 used for success?
when i put that function in terminal i get 13 xD
kevin@Kevin-PC:~$ echo $?
13

hMM
i don't see any fault in above code xD
maybe it's in the int main(here) or in the include?
the rest seems good..
i check your library seems good included file..
but.. what's wrong then?

Have a way to go lol i really don't see anything bad..
Thanks for the help :p


AH. i just compiled..
it seems gets is bad..
what abt fgets?
neither..
kevin@Kevin-PC:~$ gcc Desktop/compile.c -o Desktop/test/compile.o
Desktop/compile.c: In function &#8216;main&#8217;:
Desktop/compile.c:7: error: too few arguments to function &#8216;fgets&#8217;

Hmm
lol

---

### Post by LaRoza on 2008-01-01
0 is usually used for success, however, depending on the app, different codes may be used.

If you open dc (type dc in a terminal) then type 'q' it will exit. Then type "echo $?", and you will get 0.

The code is correct, and is valid, however, gets() is a bad function to use.

You'll note that the length of the character array called "name" is 20. 

gets will take a pointer (in this case, a name of an array) as an argument, and stick any input there. So, when you use gets(name), it sticks the input in that memory address and up. Nothing stops it from going past 20, in fact, if you go past it enough, you will crash the program. 

fgets() takes 3 arguments [http://www.space.unibe.ch/comp_doc/c_manual/C/FUNCTIONS/fgets.html](http://www.space.unibe.ch/comp_doc/c_manual/C/FUNCTIONS/fgets.html)

---

### Post by shadows123 on 2008-01-01
i see..
as it makes prob when compiling with gets.. what can you do then?
why is gets dangerous?
" warning: the `gets' function is dangerous and should not be used."
Thanks...

Edit: found out it's only a warning..
so if you'd go further you'd get like
[PHP]
#include <stdio.h> 

int main(int args,char ** argv) 
{ 
    char name[20]; 
    puts("What is your name? "); 
    gets(name); 
    puts("Hello %s, welcome to C\n What's your age?",name);
    gets(age);
    printf("Your name is %s and your age is %a",name); 
    return 0; 
} 
[/PHP]
but there you'd have too much puts..

---

### Post by LaRoza on 2008-01-01
> **shadows123 said:**
> i see..
as it makes prob when compiling with gets.. what can you do then?
Thanks...

Use fgets()

---

### Post by shadows123 on 2008-01-01
See what i posted above.. how you'd do that? lol
hey man i'm sorry to disturb, thanks a lot for explanations :)

---

### Post by LaRoza on 2008-01-01
[php]
#include <stdio.h>

int main(int args,char ** argv)
{
    char name[20];
    puts("What is your name? ");
    fgets(name,19,stdin);
    printf("Hello %s, welcome to C\n",name);
    return 0;
}
[/php]

puts() takes only one argument, a string (or a pointer)

---

### Post by shadows123 on 2008-01-01
Hmm
but that doesn't take his age?
also can you explain me the %s? lol..
thanks :D

---

### Post by LaRoza on 2008-01-01
> **shadows123 said:**
> 
also can you explain me the %s? lol..
thanks :D

printf() takes multiple arguments, in the first code post, it took one, a string:

printf("Hello world\n");

You can also use it to format (that is what the 'f' in printf means) and use variables.

Read up on printf() to understand it more, but here is a little example of it.

[php]
#include <stdio.h>

int main(int args,char ** argv)
{
    char * name = "LaRoza";
    int age = 19;
    char a = 65;
    printf("My name is %s. I am %d. The letter %c\n",name,age,a);
    return 0;
}
[/php]

---

### Post by shadows123 on 2008-01-02
Hmm
buy how'd you do my thing den of asking age & name?
[php]
#include <stdio.h>

int main(int args,chat ** argv)
{
       puts("Hey! What's your name, age, are you proud of yourself?");
       fgets("name,age,proud");
       printf("Hey! %n, You are %a years old! Congrats! Are you proud of yourself? %p !!!",name,age,proud);
       return (0);
}
[/php]
But that doesn't work right..
so is it actually possible to do that? lol

---

### Post by LaRoza on 2008-01-02
> **shadows123 said:**
> Hmm
buy how'd you do my thing den of asking age & name?
[php]
#include <stdio.h>

int main(int args,chat ** argv)
{
       puts("Hey! What's your name, age, are you proud of yourself?");
       fgets("name,age,proud");
       printf("Hey! %n, You are %a years old! Congrats! Are you proud of yourself? %p !!!",name,age,proud);
       return (0);
}
[/php]
But that doesn't work right..
so is it actually possible to do that? lol

That code doesn't make sense...

Did you read about fgets()? I gave a link... I also gave an example.

You have to declare variables in C, if you don't know that you should read a C tutorial, see my wiki.

As for you question, here is an answer, although I am not going to explain it.

[php]
#include <stdio.h>

int main(int args,chat ** argv)
{
       char name[20];
       int age;
       char proud[5];
       puts("Hey! What's your name, age, are you proud of yourself?");
       scanf("%s,%d,%s",name,age,proud);
       printf("Hey! %s, You are %d years old! Congrats! Are you proud of yourself? %s !!!",name,age,proud);
       return (0);
}
[/php]

Before posting further, read and go through a C tutorial.

---


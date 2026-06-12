---
title: "[SOLVED] Taking input using C"
date: 2008-10-24
forum: Programming Talk
---

### Post by PmDematagoda on 2008-10-24
Hey there, first off, I must say that this is my first time with C, so if I sound stupid, you know the reason why;). Anyway, to the problem, I know how to use syntax in C quite generally, but the problem I am having is how to accept input in C, like where you input a choice which is then accepted and stored in a variable using C.

Can anyone help out?

---

### Post by PmDematagoda on 2008-10-24
By the way, I tried checking out scanf in this way:-
```
#include <stdio.h>

int A,B,C;

int main (void){
  extern A,B,C;
  printf("Enter the first value to be added:- ");
  scanf("%d",A);
  if (A!=" "){
  printf("\nEnter the second value to be added:- ");
  }
  scanf("%d",B);
  if (B!=" "){
  C=A+B;
  }
  printf("The result= %d",C);
}
```
but it gives me a segmentation fault, which obviously means I'm doing it wrong.

---

### Post by Zugzwang on 2008-10-24
> **PmDematagoda said:**
> 
but it gives me a segmentation fault, which obviously means I'm doing it wrong.

Solution: Read a C book! If you have this problem, then you're likely not to be quite "ready" for serious development, so going through a book and its example might probably be wise.

With regards to the actual problem: Note that you have to pass a pointer to the location in which scanf() should store the result, so use "scanf("%d",&A);". Also you are comparing an int against a (the address of a string), that does not seem to make sense. Use "-Wall" when compiling for additional warnings that give you valuable hints.

---

### Post by PmDematagoda on 2008-10-24
> **Zugzwang said:**
> Solution: Read a C book!

Note that you have to pass a pointer to the location in which scanf() should store the result, so use "scanf("%d",&A);".

I do have a book for reference, but I guess I'm just a bit too hasty, which I probably shouldn't do:-P.

And your advice solved my problem.

Thanks!

---

### Post by Tony Flury on 2008-10-24
scanf needs a pointer to the variable, and not the variable itself. - so try 

> **PmDematagoda said:**
> 
```
#include <stdio.h>
...
...
  scanf("%d",&A);
...
  scanf("%d",&B);
...
...
}
```


Also bear in mind using %d on scanf will get an integer - and that will never equal " ", and the if statements are comparing int with a char*, so those if statements will never work.

I think you need to read up on scanf and what it does - one thing you do need to know is that %d as a pattern will ignore any input that wont be part of a valid integer - so if the user types spaces or other characters (that aren't numbers) then they will be ignored by your use of scanf.

---

### Post by mike_g on 2008-10-24
My preferred way to get input is by using [fgets](http://www.cplusplus.com/reference/clibrary/cstdio/fgets.html). 

That will safely accept any string. You can then compare strings using [strcmp](http://www.cplusplus.com/reference/clibrary/cstring/strcmp.html).

Then if you need to convert it to an integer you could use [strtol](http://www.cplusplus.com/reference/clibrary/cstdlib/strtol.html).

---

### Post by PmDematagoda on 2008-10-24
Thanks for the advice and small intros to the other procedures usable under C guys, it may make the journey through C a little more easier:).

And I admit, I was wrong to try something like this when I had not even completely read the book, let alone the section that dealt with this, which I admit, is a bad decision on my part. But at least I learnt(well, I hope I did;)) to not do something like this again.

---

### Post by LaRoza on 2008-10-24
> **PmDematagoda said:**
> Thanks for the advice and small intros to the other procedures usable under C guys, it may make the journey through C a little more easier:).

And I admit, I was wrong to try something like this when I had not even completely read the book, let alone the section that dealt with this, which I admit, is a bad decision on my part. But at least I learnt(well, I hope I did;)) to not do something like this again.
The C standard library isn't big.

See my wiki.

---

### Post by namegame on 2008-10-24
I really don't use scanf() or printf() very often.

I've developed the habit of fscanf() and fprintf() as many of my programming tasks read from an input file and write to an output file.

I don't know the advantages and disadvantages of each however if and when you need to receive input from a file fscanf() will be useful.

And example of fscanf() and fprintf():

[php]

fscanf(stdin, "%d", &variable);  
fprintf(stdout, "%d", variable);

[/php]

The above statements read and write to standard input and output respectively. This input and output can be redirected as follows:

[php]

./a.out < input.file > output.file

[/php]

---

### Post by nvteighen on 2008-10-24
> **namegame said:**
> I really don't use scanf() or printf() very often.

I've developed the habit of fscanf() and fprintf() as many of my programming tasks read from an input file and write to an output file.

I don't know the advantages and disadvantages of each however if and when you need to receive input from a file fscanf() will be useful.

And example of fscanf() and fprintf():

[php]

fscanf(stdin, "%d", &variable);  
fprintf(stdout, "%d", variable);

[/php]

The above statements read and write to standard input and output respectively. This input and output can be redirected as follows:

[php]

./a.out < input.file > output.file

[/php]
Well, that's pure UNIX philosophy!

---

### Post by namegame on 2008-10-24
> **nvteighen said:**
> Well, that's pure UNIX philosophy!

I'm not sure if this is good or bad. 

Enlighten me. Maybe I can learn something. :)

---

### Post by PmDematagoda on 2008-10-24
> **LaRoza said:**
> The C standard library isn't big.

See my wiki.

I had a look around your wiki yesterday and it certainly looks like a great resource. My congratulations on maintaining such a great and professional looking wiki LaRoza:).

---

### Post by LaRoza on 2008-10-24
> **PmDematagoda said:**
> I had a look around your wiki yesterday and it certainly looks like a great resource. My congratulations on maintaining such a great and professional looking wiki LaRoza:).

Thanks. I hope people find it useful :-)

There are bits I need to update though.

---

### Post by nvteighen on 2008-10-25
> **namegame said:**
> I'm not sure if this is good or bad. 

Enlighten me. Maybe I can learn something. :)
Sure: [http://www.linfo.org/unix_philosophy.html](http://www.linfo.org/unix_philosophy.html), [http://en.wikipedia.org/wiki/Unix_philosophy](http://en.wikipedia.org/wiki/Unix_philosophy)

The UNIX Philosophy is actually all about keeping modularity at all levels: at code  but also at the system itself. Modularity in code is probably something you already know and hopefully also use: structured programming, avoiding globals, "1 function <=> 1 task", etc. C was designed to be used that way; the so-called "C Philosophy" is the same as the UNIX one... both were created simultaneously by the same people for the very same project.

At system level, it's about having "1 task <=> 1 program" and make the system be a net of interconnected programs communicating eachother (Just the same as you do when using functions in your C programs). This communication can be done through different channels: the pipe, the program's main() return value (have you ever wondered why main() has to return something?), etc. For that, everything has to use a common interface, which in UNIX is the file. That's why stdout, stdin are always files (either a plaintext or a device file or whatever) and why you can redirect I/O to wherever you like.

Obviously, using fprintf() over printf() doesn't affect that behaivor. You can still redirect output in a program that uses printf() as this function **can be considered** to act as a macro for fprintf(stdout, ...). (that's not what really happens as we first need to parse the variable argument list, but the effect is the same).

---


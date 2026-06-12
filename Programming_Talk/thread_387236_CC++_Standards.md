---
title: "C/C++ Standards"
date: 2007-03-18
forum: Programming Talk
---

### Post by someonedumb on 2007-03-18
Hi,

I am not new to programming, I've been toying with it in Microsoft compilers for years. I tried to write some small test programs in Ubuntu just to prove to myself it worked.

I started with a simple program that declared a few variables and some text output, and it worked. Added an if/then and it continued to work. Then I thought I'd try adding a for loop, but it broke.

```

Prog.c: In function ‘main’:
Prog.c:7: error: ‘for’ loop initial declaration used outside C99 mode

```

What is C99 mode? Should I expect there to be alot of differences between Microsoft C/C++ and gcc C/C++?

---

### Post by lloyd_b on 2007-03-18
Could you post the code that generated this error?  Also the command line you used to compile it?

I've never seen that "C99 mode" error before, so I'm curious to see if I can replicate that condition on my machine.

Lloyd B.

---

### Post by WW on 2007-03-18
My guess is you did something like this:
```

for (int i = 0; i < ...

```
But gcc wants this:
```

int i;
for (i = 0; i < ...

```

---

### Post by someonedumb on 2007-03-18
A bit of trial and error lead to the syntax that compiles correctly by the way. I was posting this to find out what C99 mode is, and if I should epxect alot more differences between Windows C/C++ and gcc C/C++.

This is the exact code that generated the error:
```

for(int i = 3; i<6; i++){}
```

Compiled using:
```

gcc Prog.c -o Prog.exe
```

---

### Post by DavidBell on 2007-03-18
There are heaps of hits if you google "C99 mode"

---

### Post by thumper on 2007-03-18
> **someonedumb said:**
> A bit of trial and error lead to the syntax that compiles correctly by the way. I was posting this to find out what C99 mode is, and if I should epxect alot more differences between Windows C/C++ and gcc C/C++.

This is the exact code that generated the error:
```

for(int i = 3; i<6; i++){}
```

Compiled using:
```

gcc Prog.c -o Prog.exe
```

C99 refers to the ISO C standard that was ratified in 1999.  The C++ standard was ratified in 1997 I think, with the next C++ standard due for a vote in 2009.

C and C++ are very different languages.  I'm not even going to start here on the differences.

---

### Post by WW on 2007-03-18
The C language has evolved since K&R created it in the '70s. See, for example, [http://en.wikipedia.org/wiki/C_(programming_language](http://en.wikipedia.org/wiki/C_(programming_language)) for a brief history.  Declaring a variable in the initialization of a for loop was not in the original K&R C, but it is allowed in the C99 standard.

According to **man gcc**, the default standard used by gcc is ISO C90 plus gnu extensions (which includes some C99 features, but not, apparently, declaration of variables in the for loop initialization).  If you want to use the declaration in your for loops, you can add the option **-std=c99** to your gcc command.

I've never used Microsoft C, so I don't know which standard (if any) it conforms to.

---

### Post by someonedumb on 2007-03-18
Very interesting. I always thought C++ was "C plus some stuff". I definitely didn't expect that the standard differences I just encountered were between C and C++.

I was thinking this was a difference between Microsoft's implementation of C/C++ and gcc's implementation.

Thanks alot for the feedback :)

---

### Post by maxamillion on 2007-03-18
> **someonedumb said:**
> A bit of trial and error lead to the syntax that compiles correctly by the way. I was posting this to find out what C99 mode is, and if I should epxect alot more differences between Windows C/C++ and gcc C/C++.

This is the exact code that generated the error:
```

for(int i = 3; i<6; i++){}
```

Compiled using:
```

gcc Prog.c -o Prog.exe
```

Microsoft compilers (in my very minimal experience with them in computer labs on my college campus) allow programmers to get away with certain shortcuts that aren't exactly allowed by standard compilers

Also, please I beg you never to call anything a .exe while you run linux ... it just makes my stomach turn upside down to see that being done

---

### Post by HadroLepton on 2007-03-18
you can also use -std=gnu99 which is the c99 standard with some gnu extensions.
read here for more
[http://gcc.gnu.org/onlinedocs/gcc/C-Dialect-Options.html#C-Dialect-Options](http://gcc.gnu.org/onlinedocs/gcc/C-Dialect-Options.html#C-Dialect-Options)

---

### Post by someonedumb on 2007-03-18
> Also, please I beg you never to call anything a .exe while you run linux ... it just makes my stomach turn upside down to see that being done

Ok, no more .exe

I can't help but be curious, why does it cause so much discomfort?

---

### Post by Tomosaur on 2007-03-18
In short, the answer is that you must declare variables before using them. The GCC compiler sees this:
```

for(int i = 0; i < x; i++){
  //stuff
}

```
as a usage before declaration instance. I think C99 states that all local variables must be declared at the very beginning of the block, so you must use something like this:
```

void my_method(){
  int a = 1;
  int b = 2;
  int c = 3;
  int i = 0;
  //stuff
  for(i; i < c; i++){
    a += b;
    b += c;
  }
}
```

HOWEVER - you should remember that it appilies to a code block, not a method. For that reason, you can declare variables inside if statements and such if you want, since they can only be used within the scope of those internal blocks. I THINK (so don't hold me to it) you can't use the 'int i = 0;' code in the for loop, because the purpose of the first element in the for loop is to register a value into the counter, and not to declare variables. I think you can change the standard gcc uses, so if you don't like this behaviour you can just use a different standard (or hell, just change the behaviour of gcc yourself, that's why it's open source :P).

As for the .exe thing - Linux files aren't recognised by extension. They're recognised via a few things - MIME types, contents etc. Any file can be made executable. I would hesitate to say it makes my stomach turn, but it can confuse people. It's a fairly frequent request from new Linux users ("I can't find setup.exe!"), and I think it annoys a few people after a certain amount of time.

---


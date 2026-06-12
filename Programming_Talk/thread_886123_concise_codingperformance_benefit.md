---
title: "concise coding/performance benefit"
date: 2008-08-10
forum: Programming Talk
---

### Post by badperson on 2008-08-10
Hi,

Is there a substantial (or any) performance benefit to writing this:

```

BufferedReader br = new BufferedReader(new FileReader(new File("file.txt")));


```

over this:

```

File f = new File("file.txt");
FileReader fr = new FileReader(f);
BufferedReader br = new BufferedReader(fr);

```


or are you just more of rock star if you can condense everything as much as possible? 

I'm at kind of an intermediate level, but I've always started writing really verbose code, and then condensing when I know what I'm doing...but if you have a really large app, would it run better if it had fewer lines?
bp

---

### Post by CptPicard on 2008-08-10
The compiler compiles both into equivalent. That's its job really, and by writing "concise" code you are at worst obfuscating it. Code is meant to be read, let the compiler worry about performance.

---

### Post by NovaAesa on 2008-08-10
You're no rockstar for writing concise code (unless it's in a concise code contest :P). When you have more than 2 or 3 nested parentheses on the same line, it makes things a tad hard to read. There are more chances of a mistake as well. But don't make everything too verbose as well. For example, if you have to initialise a variable:

don't do this:
```

int var;
var = 42;

```

just do this instead:
```

int var = 42;

```

There's nothing wrong with making code concise as long as it doesn't sacrifice readability. Use you common sense here.

---

### Post by pmasiar on 2008-08-10
Don't be obsessed on micro-optimization, compilers are much better in it than you ever can hope to be. Instead, optimize macro-structures.

Ie many people adds to string using +=, which is quite ineffective, forcing lots of memory reallocation. Instead, use ArrayList of Strings, and join them into one when done.

And in general, use best tool for the job if you can: either dynamic language which makes you more productive coder, like Python or Ruby, or language which makes code extremely optimized, like C. Anything between is likely be slower than C, and harder to develop and maintain than Python ==> suboptimal.

---

### Post by CptPicard on 2008-08-10
> **pmasiar said:**
> 
Instead, use ArrayList of Strings, and join them into one when done.

Uh, that's Python. :) The Java way is StringBuilder or StringBuffer :)

---

### Post by badperson on 2008-08-10
> Ie many people adds to string using +=, which is quite ineffective, forcing lots of memory reallocation. Instead, use ArrayList of Strings, and join them into one when done.

I've been guilty of that...instead of taking ten minutes to read up on stringBuffer I've just said screw it, use +=...

live and learn. 
bp

---

### Post by slavik on 2008-08-10
for something like a buffered reader in java, do you really want to pollute the symbol table with symbols you are not really using anyway?

---

### Post by CptPicard on 2008-08-10
> **slavik said:**
> for something like a buffered reader in java, do you really want to pollute the symbol table with symbols you are not really using anyway?

You are correct that in this particular example (and similar situations) I would not be giving all of those their own local names, but the question that was being asked very much deserves to be answered the way it was :)

---

### Post by slavik on 2008-08-10
> **CptPicard said:**
> You are correct that in this particular example (and similar situations) I would not be giving all of those their own local names, but the question that was being asked very much deserves to be answered the way it was :)
there was a concrete example given, which I addressed :)

but with the example pmasiar made, the stupider thing to do is:
int i = 0;
i = readfromfile();

or some sort (the point is not to use initialization unless you have to).

---

### Post by mssever on 2008-08-11
> **pmasiar said:**
> Ie many people adds to string using +=, which is quite ineffective, forcing lots of memory reallocation.
I learned that the hard way. My algorithm (which used string concatenation extensively) worked so well for my small test dataset! Then, I gave it a large input file, and suddenly it took > 3 *hours* to process the file (I don't know the exact time, because I went to bed eventually), because all the string concatenation fairly quickly exhausted my available RAM and so my program spent huge amounts of time waiting on swapping.

I was trying to think of ways to limit the size of my input file, when all of a sudden I remembered that Ruby's strings are immutable. So, I switched from concatenating strings to appending to an array and doing a single join operation at the end, and suddenly, my program processed the same input in 20 seconds. Further refinements improved the speed to around 15 seconds, which was quite acceptable for my purposes.

---

### Post by tinny on 2008-08-11
> **CptPicard said:**
> The compiler compiles both into equivalent. That's its job really, and by writing "concise" code you are at worst obfuscating it. Code is meant to be read, let the compiler worry about performance.

Bang on. The complier does a fine job.

Whatever coding style you choose make sure its readable and CONSISTENT.

Also dont worry too much about writing optimal code, this will come with experience.

Code that actually works and delivers the requirement is always better than optimized code that doesnt deliver... Ive seen guys waste weeks trying to deliver the "optimal solution", all while the customer just wants a login page. ](*,)

---


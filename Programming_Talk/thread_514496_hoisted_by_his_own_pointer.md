---
title: "hoisted by his *own pointer"
date: 2007-07-31
forum: Programming Talk
---

### Post by nss0000 on 2007-07-31
Gents:

Couple weeks now since I started re-learning  C. Hacking away ... and much blood flows over pointers: This seems curious:

I can suck-in a command line arg by looping into a char_array:

  For example, loosely speaking say  ......
   
   i=0;
   WHILE ( i < strlen(argv[3]) )
   mystring[i] = argv[3][i] ;
   i++;

 ... but not ...
 
  char *s;
   s = argv[3];

  i=0;
  WHILE ( i < strlen(argv[3]) )
  mystring[i] = (*s)++;
  i++;

Please remove the *point shaft from where it is sticking ...

nss
********

---

### Post by Wybiral on 2007-07-31
Is there a question anywhere in here?

If you're wondering why they aren't the same...

(*s)++;

is not...

*(s++);

The first one is dereferencing, then incrementing, the second one is incrementing, then dereferencing.

---

### Post by DougB1958 on 2007-07-31
> **Wybiral said:**
> Is there a question anywhere in here?

If you're wondering why they aren't the same...

(*s)++;

is not...

*(s++);

The first one is dereferencing, then incrementing, the second one is incrementing, then dereferencing.

It's worse than that, isn't it? Isn't ```
(*s)++
``` incrementing the value that s points to, but leaving s unchanged, while ```
*(s++)
``` yields the value s points to and then increments s (which is what I think the original poster wants)?

---

### Post by Wybiral on 2007-07-31
> **DougB1958 said:**
> It's worse than that, isn't it? Isn't ```
(*s)++
``` incrementing the value that s points to, but leaving s unchanged, while ```
*(s++)
``` yields the value s points to and then increments s (which is what I think the original poster wants)?

Yeah, if it dereferences before incrementing then the data at the address "s" points to is incremented instead of the address held by "s".

Basically...

*(s++) is x[s++]

while

(*s)++ is x[s]++

---

### Post by H264 on 2007-07-31
coming from Java, that is a cool thing to be able to do... hehe.

People talk about how scary pointers are, once you understand this they are not that bad.

---

### Post by Wybiral on 2007-07-31
> **H264 said:**
> coming from Java, that is a cool thing to be able to do... hehe.

People talk about how scary pointers are, once you understand this they are not that bad.

Yeah, I've seen a lot of people terrified by pointers too.

It's not that bad when you realize that '*' means "data at address" and "&" means "address of label".

If you don't dereference it with '*' or '[]' it will always just be an address.

---

### Post by slavik on 2007-08-01
also, when you change s, you lose the beginning of the string, thus memory leak :)

---

### Post by Wybiral on 2007-08-01
> **slavik said:**
> also, when you change s, you lose the beginning of the string, thus memory leak :)

Only if "s" is the only pointer to the memory and the memory was dynamically allocated. Otherwise it's OK to let go of a pointer.

---

### Post by nss0000 on 2007-08-01
Gentlemen:

YES ! Many thanks to those responding: As advised, the form ...
    
     WHILE( i < strlen(argv[1]) )
     filename[i] = *(s++);

... correctly recovers the command_line string, such as:

    <MYPROG foo.dat> --> filename[] = foo.dat

I just noticed that my original *blunder produces an amusing result:
With the improper construct ...

     WHILE( i < strlen(argv[1]) )
     filename[i] = (*s)++;

... and a commandline string produces: 

  <MYPROG foo.dat>  --> filename[] = fghijkl .   YIKES !!

Down in *pointerland the first letter of the arg gets caught while the rest are "in-sequence" chars.I vaguely remember some such warning  ... but it's back-to K&R for some (groan) light reading ...

Again, many thanks for the clue.

nss
*******

---


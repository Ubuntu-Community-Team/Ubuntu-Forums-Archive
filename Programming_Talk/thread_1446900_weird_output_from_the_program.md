---
title: "weird output from the program"
date: 2010-04-04
forum: Programming Talk
---

### Post by cybo on 2010-04-04
**NOTE: this is not a homework assignment. i'm just curious why this is happening.**

i wrote a very simple code in c, it just displays 1000 random characters. the code is stored on my university account to which i connect through putty. after i run my code i get the following output:

```

**prompt>>** ./myprogram
......
......
some random characters
......
......

**prompt>>** PuTTYPuTTYPuTTYPuTTYPuTTYPuTTYPuTTYPuTTYPuTTYPuTTYPuTTY
PuTTYPuTTYPuTTYPuTTYPuTTYPuTTYPuTTYPuTTYPuTTYPuTTYPuTTY
PuTTYPuTTYPuTTYPuTTYPuTTYPuTTYPuTTYPuTTYPuTTYPuTTYPuTTY
PuTTYPuTTYPuTTYPuTTYPuTTYPuTTYPuTTYPuTTYPuTTYPuTTYPuTTY

```

is there an explanation to this?

---

### Post by Can+~ on 2010-04-04
And what would be the code?

I'm guessing that you're going out of your assigned memory page and into other putty sessions' memory, which would be considered an attempt to read reserved space.

---

### Post by lisati on 2010-04-04
> **Can+~ said:**
> And what would be the code?

I'm guessing that you're going out of your assigned memory page and into other putty sessions' memory, which would be considered an attempt to read reserved space.

That's similar to what I was thinking, that a rogue pointer somewhere had somehow picked up on the "wrong" data to output.

---

### Post by Some Penguin on 2010-04-04
You might want to avoid outputting control characters to the console.

---

### Post by The Cog on 2010-04-05
My first guess is that you are sending control characters such as character code 5 (ENQ) that I think means "What type of terminal are you?"

Try sticking to printable characters in the range 32-126.

---

### Post by cybo on 2010-04-05
Cog,

you are correct. i modified the code to generate only printable characters and it worked. thanks. also thank you very much to everyone.

---


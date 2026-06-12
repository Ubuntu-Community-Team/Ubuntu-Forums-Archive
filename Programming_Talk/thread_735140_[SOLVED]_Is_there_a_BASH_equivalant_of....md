---
title: "[SOLVED] Is there a BASH equivalant of..."
date: 2008-03-25
forum: Programming Talk
---

### Post by ibuclaw on 2008-03-25
Hi, thank-you in advanced.

Is there a BASH equivalent of printing the character code of a letter or symbol?

example in C
```

char ch = "A";
printf ("%d", ch);

```

the only thing I can find that is similiar is **echo -e "/xnnn"**.
But that is my question in reverse.

Regards
Iain

---

### Post by LaRoza on 2008-03-25
No simple way.

Do you have to use bash?

[http://www.linuxquestions.org/questions/programming-9/bash-ascii-to-hex-and-hex-to-ascii-488357/](http://www.linuxquestions.org/questions/programming-9/bash-ascii-to-hex-and-hex-to-ascii-488357/)

---

### Post by Martin Witte on 2008-03-25
You can write a few functions yourself, eg:
```

#!/bin/bash
# chr() - converts decimal value to its ASCII character representation
# ord() - converts ASCII character to its decimal value

chr() {
  printf \\$(printf '%03o' $1)
}

ord() {
  printf '%d' "'$1"
}

ord A
echo
chr 65
echo

```

(taken from [http://wooledge.org:8000/BashFAQ](http://wooledge.org:8000/BashFAQ))

---

### Post by ibuclaw on 2008-03-25
Thanks, I didn't know BASH used the C syntax.

I suppose you learn something new everyday!

---

### Post by ibuclaw on 2008-03-25
> **LaRoza said:**
> No simple way.

Do you have to use bash?


Well, I suppose the answer is now yes. As I can't find a way to convert an input argument to its ascii number in C. (ie: a into 97)
Because argv[1] is treated as a string, not a character.
So **printf ("%s", argv[1]);** is the only way to properly print the input argument. (%c will print some random gibberish).

but I can extract a number from an input argument.
**ch = (int)strtol ( argv[1], NULL, 10 );**

So I figured that it may be easier to use a language that treats it's input arguments as characters...

Hence why I ask if BASH can do this. So I can execute the C program with the number argument of the char I want.

Hope this makes sense.

Regards
Iain

[EDIT]
Here's a brief example of what I was trying to (and have now) acheive.
```

___________________________________
#!/bin/bash

ch=$(printf '%d' "'$1")
./cprog $ch
___________________________________
#include <stdio.h>
#include <stdlib.h>
int main(int argc, char *argv[])
{
        int ch = (int)strtol (argv[1], NULL, 10);
        /*
        switch to react to the inputted argument
        */
        return 0;
}
___________________________________

```

---

### Post by eatnumber1 on 2008-08-01
> **tinivole said:**
> Well, I suppose the answer is now yes. As I can't find a way to convert an input argument to its ascii number in C. (ie: a into 97)
Because argv[1] is treated as a string, not a character.
So **printf ("%s", argv[1]);** is the only way to properly print the input argument. (%c will print some random gibberish).

A string in C is an array of characters... so you can do argv[1][0] to get the first character in the first argument... then you can convert it to an int.

Also, in C, you can just cast it to an int, or you can just use it as if it was one.

---


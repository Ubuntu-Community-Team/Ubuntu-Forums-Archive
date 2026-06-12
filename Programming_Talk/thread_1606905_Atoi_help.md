---
title: "Atoi help"
date: 2010-10-27
forum: Programming Talk
---

### Post by DeathStar427 on 2010-10-27
help with converting the original text 4 string to an intiger!
if(text[4] == ' ') { //if the text exists
int v = text[4] - '0'; //declaring "v" as text[4]
v = atoi (text[4]); //i need help here.. converting v (text[4]) into an intiger. 
clientinfo *i = (clientinfo *)getclientinfo(v); //some code that is needed
if (clients[i]->connected){ //if the client is connected.. do {
setmaster(i, true); //setmaster "i" which is the int of the client, true
break;

---

### Post by s.fox on 2010-10-27
Thread moved to Programming Talk.

Please state which language you are using.

---

### Post by trent.josephsen on 2010-10-27
FOR THE LOVE OF ALL THAT IS HOLY, PLEASE INDENT YOUR CODE.

Presumably, text is of type char *.  Therefore text[4] is of type char.  So you're checking if text[4] is a space character... then subtracting the numeric value of '0' from it, and assigning the result to v... but that doesn't even matter, because you immediately overwrite v with the result of a call to atoi, which actually isn't legal because you're passing it a single character rather than a char *.

You will be likely to get better help if you explain what you want to do, rather than posting code and asking why it doesn't work.  An even better approach is to write a small single-purpose program that illustrates the problem you're having, rather than a snippet of a large program with all the relevant declarations cut out.

Also, don't use atoi; you can't tell when it fails.  Use strtol instead.

Here's an example program (square.c) showing how to use strtol:
```
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char **argv)
{
        long value;
        char *endp;
        if (argc != 2) { // verify correct usage
                fprintf(stderr, "Usage: %s <NUMBER>\n", argv[0]);
                return EXIT_FAILURE;
        }

        value = strtol(argv[1], &endp, 0);
        if (endp == argv[1]) {
                fprintf(stderr, "Error: %s is not a number\n", argv[1]);
                return EXIT_FAILURE;
        } else if (*endp) {
                fprintf(stderr, "Warning: Unconverted suffix %s\n", endp);
                // unconverted suffix not fatal; continue
        }

        printf("%ld^2 = %ld\n", value, value*value);
        return EXIT_SUCCESS;
}
```

Compile it like this:
```
gcc -Wall -Wextra -std=c99 -pedantic -o square square.c
```
Note that despite all the warnings being turned on, gcc doesn't complain.

Then run it like this:
```
./square 42
```

Try experimenting with different values in place of "42" so you can get a feel for how strtol deals with non-numeric input.

---


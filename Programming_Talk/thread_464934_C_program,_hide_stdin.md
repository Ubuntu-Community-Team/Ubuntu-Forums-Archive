---
title: "C program, hide stdin"
date: 2007-06-05
forum: Programming Talk
---

### Post by Eviltelm on 2007-06-05
Hi!
I made a c program with some games in a menu which requires a user name and login, but i don't know how to hide the password with '*' when user is typing....
Thank's for the help ;)

---

### Post by ruy_lopez on 2007-06-05
see "man getpass"

---

### Post by Eviltelm on 2007-06-05
Thanks man :)
It doesn't show the pass but how to use '*' now??
thanks

I used:
```
pass = getpass ("Insira password: ");
```

---

### Post by ceeg on 2007-06-05
>      The getpass() function turns off character echoing while reading the
     password.

I don't think your'e going to be able to print characters to the screen if you use the getpass() function. Look up the code for getpass(), you'll need to modify it, likely.

---

### Post by ruy_lopez on 2007-06-06
This is a bit hacky, but it seems to work. Using the code template [from here (link)]("http://www.gnu.org/software/libc/manual/html_node/getpass.html") gives you the basic my_pass function. Messing around with the flags, specifically ECHOCTL, seems to allow printing the "*" asterisks. I'm not sure how safe this is, but at least there's some boundary checking on the buffer, which the standard getpass() doesn't do.

The code in the main(), shows you how to use my_pass().

```

#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <termios.h>

#define MAX_PASS 1024

int main(void)
{
	char pass[MAX_PASS], *password = "hello";
	ssize_t n;
	
	printf("enterpass: ");
	n = my_getpass(pass, sizeof(pass), stdin);
        
        if (strcmp(pass, password) == 0)
	        printf("%s\n", pass);
}


ssize_t my_getpass (char *lineptr, size_t len, FILE *stream)
{
	struct termios old, new;
	int nread = 0;
	char c;

        /* Turn echoing off and fail if we can't. */
	if (tcgetattr (fileno (stream), &old) != 0)
		return -1;
	new = old;
	new.c_lflag &= ~ECHO || ECHOCTL;
	if (tcsetattr (fileno (stream), TCSAFLUSH, &new) != 0)
	       return -1;
	/* Read the password. */
	while ((c = getchar()) != '\n' && nread + 1 < len) {
	       lineptr[nread++] = c;
	       printf("*");
	}
	printf("\n");
	lineptr[nread] = '\0';

	/* Restore terminal. */
	(void) tcsetattr (fileno (stream), TCSAFLUSH, &old);	
	return nread;
}

```

---

### Post by WW on 2007-06-06
Here's a modification of ruy_lopez's code that handle Backspace:
```

#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <termios.h>

#define MAX_PASS 1024

int main(void)
{
    char pass[MAX_PASS];
    ssize_t n;

    printf("enterpass: ");
    n = my_getpass(pass, sizeof(pass), stdin);

    printf("\"%s\"\n", pass);
}

#define BACKSPACE 127

ssize_t my_getpass (char *lineptr, size_t len, FILE *stream)
{
    struct termios old, new;
    int nread = 0;
    char c;

    /* Turn echoing off and fail if we can't. */
    if (tcgetattr (fileno (stream), &old) != 0)
        return -1;
    new = old;
    new.c_lflag &= ~ECHO || ECHOCTL;
    if (tcsetattr (fileno (stream), TCSAFLUSH, &new) != 0)
        return -1;
    /* Read the password. */
    while ((c = getchar()) != '\n' && nread + 1 < len) {
        if (c == BACKSPACE) {
            if (nread > 0) {
                nread--;
                printf("\b \b");
            }
        } else {
            lineptr[nread++] = c;
            printf("*");
        }
    }
    printf("\n");
    lineptr[nread] = '\0';

    /* Restore terminal. */
    (void) tcsetattr (fileno (stream), TCSAFLUSH, &old);	
    return nread;
}

```

---

### Post by ruy_lopez on 2007-06-06
A more methodical look at this reveals that ECHOCTL has nothing to do with it. The only reason the hack worked was because it reset all the other flags, except ECHOCTL.

The flag that matters is ICANON. It line-buffers the input, so that the asterisks only appear once a newline is returned. Thus disabling it enables character at a time buffering.

To correct the code, replace the ECHOCTL line with this:

```
new.c_lflag &= ~(ECHO | ECHOE | ECHOK | ECHONL | ICANON);
```

I've thrown in ECHOE | ECHOK | ECHONL for good measure, just to be safe (that's what Richard Stevens' version of getpass() in APUE uses). *** if you want to see Richard Stevens' version you can get the source [here]("http://www.apuebook.com/src.tar.gz") (it's in the "termios" folder).

---

### Post by Eviltelm on 2007-06-06
Thanks guyz, will try to compile that when i get home, but i don't think i will be able to use it in my work, my teacher won't belive i've done that :)
But will keep it to my own version ;)

btw, how can i get headers to work properly, if i use for instance tst.c and use there abc.h and use the same abc.h in abc.c my const int will result in multiple definition, but if i take the include from abc.c it will say i don't have them .. :(

Thanks again :)

---

### Post by ruy_lopez on 2007-06-06
In tst.c
```

#include "abc.h"

const int test = 1965;

void test_functions()
{
}
```

In abc.c

```

#include "abc.h"

extern const int test;

void abc_functions()
{
}
```

Or instead of having the extern in abc.c, you can put it in the header. The important thing to remember is that the extern just makes available the variable you created in tst.c. Whatever scope you place the extern statement inside, that scope will have access to the variable in tst.c. Placing the extern in the header, will give every file that includes the header access.

---

### Post by Eviltelm on 2007-06-07
yay, thanks :D i put the const  in the main's header and external const in the others headers :)
Thanks and problem solved ;) :p

---


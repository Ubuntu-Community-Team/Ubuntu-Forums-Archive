---
title: "scanf in a while loop (c/c++)"
date: 2010-08-03
forum: Programming Talk
---

### Post by kboy on 2010-08-03
Hello, I'm trying to create a simple program which asks a number of people a yes/no question. when i enter (n for example) as the answer the while loop continues accordingly, but in the second iteration it doesn't request any input from the user, but automatically inputs 'a new line' char to the (input) variable.

as i see it, on every iteration it should receive a new char input from the user using scanf("%c", &input); , but it doesn't.

```

#include <stdio.h>
#define YES		'y'
#define NO		'n'
#define FINISH	'f'

int main(void)
{
	char input = YES;
	int doThink, dontThink, total;
	doThink = dontThink = 0;

	while (input != FINISH){
		printf("Is there life outside earth? ");
		scanf("%c", &input);
		if ((input != YES) && (input != NO))
			printf ("Input incorrect, please press (%c) for yes (%c) for, or (%c) for finish:\n\n", YES, NO, FINISH);
		else if (input == YES)
			doThink++;
		else if (input == NO)
			dontThink++;
	}
        return 0;
}

```

please help.

---

### Post by dwhitney67 on 2010-08-03
When you enter an 'n' or 'y' (ie a single character) and then press <return>, there are actually two characters sitting in the input stream: the single-character you typed and the newline (<return>).

When scanf() returns the single character you request during the first iteration of your loop, what do you think it is going to return on the second pass?  If you guessed the newline character, then you'd be correct.

You have two options:  read input using fgets(), or if you wish to continue using scanf(), then "flush" the input stream until you have read the newline character before attempting to call scanf() again.

P.S.  Although tempting to use, fflush() does not work for the standard input stream.

---

### Post by kboy on 2010-08-03
Thanks a lot, I've used fflush(stdin) before using scanf, and it worked great.

---

### Post by Bachstelze on 2010-08-03
> **kboy said:**
> Thanks a lot, I've used fflush(stdin) before using scanf, and it worked great.

You shouldn't rely on it, though.  It may very well not work on another machine.

---

### Post by dwhitney67 on 2010-08-03
> **kboy said:**
> Thanks a lot, I've used fflush(stdin) before using scanf, and it worked great.

What OS/compiler are you using?  fflush() does _not_ work on Linux.

Here's a simple exercise that demonstrates the failure of fflush():
```

#include <stdio.h>


int main(void)
{
   char ans = '\0';

   while (ans != 'q')
   {
      fflush(stdin);

      printf("Does fflush() really work (y/n/q)?? ");
      scanf("%c", &ans);
   }

   return 0;
}

```
Compile/run this code and let me know what you discover.

---


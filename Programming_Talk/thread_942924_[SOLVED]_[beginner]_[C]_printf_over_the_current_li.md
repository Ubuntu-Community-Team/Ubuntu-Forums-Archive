---
title: "[SOLVED] [beginner] [C] printf over the current line"
date: 2008-10-09
forum: Programming Talk
---

### Post by roccivic on 2008-10-09
Hi everyone,

I wrote this small demo code:

```
#include <stdio.h>

int x = 0;

int main()
{

	printf("This is a test program and will display some useless numbers, \nbut not on the same line\n\n");
	for (x = 0; x < 10; x++) {
		printf("%d\n", x);
		getchar();
	}

}
```

This code will print numbers 0 to 9 each on a new line, but I wonder how this could be modified so that each new PRINTF command inside the FOR loop will overwrite the previous one, obviously without wiping out the output of the PRINTF command before the FOR loop.

Help much appreciated.

Many thanks, Rouslan.

---

### Post by Tomosaur on 2008-10-09
You use the '\r' escape character to return the cursor to the beginning of the line. If your new string doesn't exceed the length of the previous string, you will get characters left over from the previous string. There are ways around this obviously (for example, just blank out the remaining characters with spaces).

So, every time you print a number, just use: printf("\r%d", x);

---

### Post by roccivic on 2008-10-09
Thanks, that worked for erasing the characters :)

But then I tried to add a delay, so that a new number is displayed every second on the same line. But it doesn't work. In fact the program waits for 10 seconds and then displays "9". Here's the code:

```
#include <stdio.h>

int x = 0;

int main()
{
	printf("This is a test program and will display some useless numbers\n");
	for (x = 0; x < 10; x++) {
		printf("\r%d", x);
		sleep(1);
	}

}
```

Could someone please tell me what I'm doing wrong?

Many thanks, Rouslan

---

### Post by Tomosaur on 2008-10-09
Not sure why it's waiting 10 seconds - but doesn't sleep count in milliseconds? So to count 1 second you use sleep(1000)?

This code works (albeit using the Windows stdio.h - I'm on Windows atm):

```

#include <stdio.h>

int main()
{
    int i;
    for (i = 0; i < 10 ; i++){
        printf("\r%d", i);
        sleep(1000);
    }
    return 0;
}

```I think sleep functions exactly the same using the Linux stdio though :S

---

### Post by snova on 2008-10-09
Try this:

```

#include <stdio.h>

int main()
{
    int x;
    printf( "This is a test program and will display some useless numbers\n" );
    for( x = 0; x < 10; x++ )
    {
        printf( "\r%d", x );
        fflush( stdout );
        sleep(1);
    }
}

```

I changed three things:

[LIST=1]
    [*] The variable x was moved out of the global scope.
    [*] You were initializing x twice, so I removed one.
    [*] I added a call to fflush(). This is the important thing that makes it work as you wanted it to.
[/LIST]

The fflush() function flushes all buffered data for a given file, in this case stdout. The reason nothing was being printed was because it was buffering output until a more appropriate time, but then it waited until the program ended.

Edit: No, I checked the manpage, and sleep counts in seconds. You'd be waiting a while with that. :)

---

### Post by Tomosaur on 2008-10-09
> **snova said:**
> Try this:

Edit: No, I checked the manpage, and sleep counts in seconds. You'd be waiting a while with that. :)

Ah - must be one of the oh-so-important differences then! It works on Windows just fine :P

Although I am using the borland compiler too so maybe that's doing something. I feel so dirty :(

---

### Post by snova on 2008-10-09
usleep() counts in milliseconds. Perhaps Windows just has different names for everything. No wonder cross platform applications require such careful configuration. It'd be quite a bug to use the wrong one!

---

### Post by roccivic on 2008-10-10
Great, that worked! Thank you!

Rouslan

---

### Post by roccivic on 2008-10-10
> **snova said:**
> usleep() counts in milliseconds. Perhaps Windows just has different names for everything. No wonder cross platform applications require such careful configuration. It'd be quite a bug to use the wrong one!

usleep actually counts microseconds,
msleep counts in milliseconds

:)

Rouslan

---


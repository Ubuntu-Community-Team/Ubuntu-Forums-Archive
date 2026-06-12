---
title: "Noobie Question about DeTab"
date: 2008-07-17
forum: Programming Talk
---

### Post by British0zzy on 2008-07-17
I don't know if this question is too 'beginner' to ask in this forum, but I have a problem I can't diagnose.
I'm writing a program that removes tabs from the input and replaces it with the correct number of spaces. It's giving me odd results, which I can't quite figure out why. If you could look at this short program and give me some pointers, it'd be greatly appreciated.

```
#include <stdio.h>

#define TABLENGTH 4

main()
{
    int n; /* Position of cursor relative to tab stops */
    int c;
    
    n = TABLENGTH;  /* Setting n to TABLENGTH is functionally equivalent to setting it to zero, but will make calculations easier */
    while ((c=getchar()) != EOF) {
        if (n > TABLENGTH)  /* When the cursor reaches a tab stop, reset the position. */
            n = 1;  /* Should this be n = n - TABLENGTH? */
        if (c != '\t') {
            putchar(c);
            if (c == '\n')
                n = TABLENGTH; /* A newline resets the cursor to 'zero' */
            else
                ++n;
        }
        else {
            for (c = 0; c < n; ++c)
                putchar(' ');
            n = TABLENGTH;  /* Tabs reset cursor to 'zero' */
        }
    }
    return 0;
}
```

---

### Post by British0zzy on 2008-07-18
I might not of explained what kind of tab behavior I wanted clearly. I am assuming there are fixed tab stops every *n* columns. So if I the input is "12'\t'34", the output should be "12**34". Or if I typed "12345'\t'6", the output should be "12345***6". (The *'s are spaces and '\t' is obviously a tab.)

I am fairly confident that the problem with the code is in lines 14-20. I have an earlier version of the program which runs fine, except that *n* is incorrect when '\n' is typed (newline resets the cursor position). I reset *n* when '\n' is typed, but I seem to get weird behavior now.

Any ideas??

(btw, the earlier version of the program is the same as posted, but with lines 16, 17, 18, and 20 deleted.)

---

### Post by WW on 2008-07-18
n is the "position of the cursor relative to the tab stop", or, in other words, the number of characters that have been printed since the last tab.  So, when a tab is encountered, you should print TABLENGTH-n spaces (not n spaces).  An exception is when then tab is encountered when n==TABLENGTH.  Presumably this should print TABLENGTH characters, not zero characters.

You may have found it easier to use n=TABLENGTH when you reset n, but I didn't.  Here's a slightly modified version.  (Change FILLCHAR to ' ' in the final version.)
```

#include <stdio.h>

#define TABLENGTH 4

#define FILLCHAR '_'

main()
{
    int n; /* Position of cursor relative to tab stops */
    int c;

    n = 0;  
    while ((c=getchar()) != EOF) {
        if (n == TABLENGTH)  /* When the cursor reaches a tab stop, reset the position. */
            n = 0;
        if (c != '\t') {
            putchar(c);
            if (c == '\n')
                n = 0; /* A newline resets the cursor to 'zero' */
            else
                ++n;
        }
        else {
            int k;
            int numspaces = TABLENGTH - n;
            for (k = 0; k < numspaces; ++k)
                putchar(FILLCHAR);
            n = 0;  /* Tabs reset cursor to 'zero' */
        }
    }
    return 0;
}

```

By the way, "It's giving me odd results,..." and "I seem to get weird behavior now" may be true statements, but they are not very helpful.  In the future, try to explain why your output is not what you expect in a little more detail.

---

### Post by British0zzy on 2008-07-18
Thank you. Is there any good rule of thumb for selecting input text to test a program? I think that was my hardest challenge in trying to diagnose the problem.
Sorry about my vague description of the output, but I really couldn't find a pattern in the way it was outputting text. I didn't know how else to explain what it was doing except that it wasn't correct. I'll try to post some of the tested input and post the actual and desired output.
Again, thanks for the help. It's been bugging me for days.

---


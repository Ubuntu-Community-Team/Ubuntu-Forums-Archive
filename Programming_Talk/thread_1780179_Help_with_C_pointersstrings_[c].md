---
title: "Help with C pointers/strings [c]"
date: 2011-06-11
forum: Programming Talk
---

### Post by cdiem on 2011-06-11
I have been trying to make some small programs to get better with using memory in C. Can you please help me spot my errors in the following code (it should ideally reverse a string and print it):

```

#include <stdio.h>
#include <string.h>
#include <stdlib.h>

main()
{
    char test[] = "awe";
    char *reversed;
    int i;

    if ((reversed = (char *) malloc (strlen(test) - 1)) == NULL)
        printf("Bad allocation");

    for (i = strlen(test) - 1; i > 0; i--)
        *reversed++ = test[i];
    *reversed++ = '\0';

    //rewind the pointer a few addresses back, to the beginning:
    *reversed = *reversed - strlen(test);
    printf("%s", reversed);

    //free(reversed); <-- results in funny errors. 
}

```

Also, when I add a "free(reversed);" at the end, there are some funny errors. Should "free" be called after malloc in this case?

---

### Post by r-senior on 2011-06-11
In your example, strlen("awe") is 3. Then you allocate strlen("awe") - 1 bytes of memory for the reversed string, i.e. 2 bytes. Are you sure that's right?

Also, when you "rewind the pointer", are you absolutely sure you are rewinding the pointer?

---

### Post by r-senior on 2011-06-11
Sorry, double post.

---

### Post by cdiem on 2011-06-11
Thanks! I was able to redo the code and it seems to work. Does the pointer point automatically to the beginning of some memory block after the "malloc" thing, or do I have to say e.g.:

char text_holder[50];
reversed = text_holder;

to make it point to a beginning of some memory segment?

```

#include <stdio.h>
#include <string.h>
#include <stdlib.h>

main()
{
    char test[] = "awe";
    char *reversed;
    char text_holder[80];
    reversed = text_holder;
    int i;

    for (i = strlen(test) - 1; i > 0; i--)
        *reversed++ = test[i];
    *reversed++ = '\0';

    printf("%s", text_holder);
}

```

I'm not sure if I need the text_holder array (sorry, my questions are of a beginner in C).

---

### Post by cgroza on 2011-06-11
It seems the only use of text_holder is to initialize the reversed*.

---

### Post by r-senior on 2011-06-11
I'm not clear why you have abandoned malloc when you were almost there? :confused:

When you use malloc(), yes the pointer points to the start of a block of memory. Just a couple of things to be careful of though:

1. The memory from malloc is uninitialised - it could contain garbage. If you populate it all (or at least up to a string terminator), that's OK.

2. You shouldn't just ignore the fact that malloc() returned NULL, print a message and carry on.

For example, you may prefer to do something like this:

```

if ((ptr = malloc(len)) == NULL) {
        perror("malloc");
        exit(EXIT_FAILURE);
}

```

---

### Post by cdiem on 2011-06-11
> **r-senior said:**
> I'm not clear why you have abandoned malloc when you were almost there? :confused:

When you use malloc(), yes the pointer points to the start of a block of memory. Just a couple of things to be careful of though:

1. The memory from malloc is uninitialised - it could contain garbage. If you populate it all (or at least up to a string terminator), that's OK.

2. You shouldn't just ignore the fact that malloc() returned NULL, print a message and carry on.

For example, you may prefer to do something like this:

```

if ((ptr = malloc(len)) == NULL) {
        perror("malloc");
        exit(EXIT_FAILURE);
}

```

Thanks very much!
I have reworked the code to:

```

#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main(void)
{
    char test[] = "awe";
    char *reversed;
    int i;

    if ((reversed = (char *) malloc (strlen(test) + 1)) == NULL)
    {   
        perror("malloc");
        exit(EXIT_FAILURE);
    }   

//    *reversed = *reversed - (strlen(test) + 1);
//    while (*reversed++)
//        putchar(*reversed);

    for (i = strlen(test) - 1; i > 0; i--)
        *reversed++ = test[i];
    *reversed++ = '\0';

    printf("%s", reversed);
    return EXIT_SUCCESS;
}

```
But I'm not quite sure how I can go back to the correct memory address in order to print the "reversed" string. Is there some standard way of doing this? :)

---

### Post by BkkBonanza on 2011-06-11
If you are using malloc and the resulting string is to be a C style string then you must malloc an extra byte for the zero. ie. not strlen(test)-1 but strlen(test)+1

free should work but if you don't malloc enough bytes you may get some error when you free it and it's been corrupted.

use an initial ptr and an incr ptr so that you don't have to re-calc the initial ptr after. eg.

char *rev, *now;

rev = now = malloc(...etc

use now as ptr you scan with but then use rev as your final string

free only once though using rev (not now since it won't relate to correct allocation)

you may have had a free error if the ptr passed to free was not correct after you re-calc the initial value - hence, safer and faster to use init ptr.

lastly, if you count down with i from strlen -1 then you need to go right to zero, ie. >= 0 is needed as condition. as mentioned above you likely didn't count right so the free got a bad ptr after you re-calc'd the init ptr.

---

### Post by schauerlich on 2011-06-11
> **cdiem said:**
> But I'm not quite sure how I can go back to the correct memory address in order to print the "reversed" string. Is there some standard way of doing this? :)

Instead of changing "reversed", make another char *, say "s", initialize it to reverse's value, and then change "s" instead. "reversed" will still point to the beginning of the string.

---

### Post by cdiem on 2011-06-11
> **BkkBonanza said:**
> If you are using malloc and the resulting string is to be a C style string then you must malloc an extra byte for the zero. ie. not strlen(test)-1 but strlen(test)+1

free should work but if you don't malloc enough bytes you may get some error when you free it and it's been corrupted.

use an initial ptr and an incr ptr so that you don't have to re-calc the initial ptr after. eg.

char *rev, *now;

rev = now = malloc(...etc

use now as ptr you scan with but then use rev as your final string

free only once though using rev (not now since it won't relate to correct allocation)

you may have had a free error if the ptr passed to free was not correct after you re-calc the initial value - hence, safer and faster to use init ptr.

lastly, if you count down with i from strlen -1 then you need to go right to zero, ie. >= 0 is needed as condition. as mentioned above you likely didn't count right so the free got a bad ptr after you re-calc'd the init ptr.

Awesome! It seems to work now. Thank you very much for all your helping and guidance!

```

#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main(void)
{
    char test[] = "awe";
    char *reversed, *now;
    int i;

    if ((now = reversed = (char *) malloc (strlen(test) + 1)) == NULL)
    {   
        perror("malloc");
        exit(EXIT_FAILURE);
    }   

    for (i = strlen(test) - 1; i >= 0; i--)
        *reversed++ = test[i];
    *reversed++ = '\0';

    printf("%s\n", now);
//    free(reversed);
//    free(now);
    return EXIT_SUCCESS;
}

```

---

### Post by r-senior on 2011-06-11
Does it work if you put the free() back in?

---

### Post by cdiem on 2011-06-11
> **r-senior said:**
> Does it work if you put the free() back in?

Nope, it says segmentation fault. I'm not sure why though :)

---

### Post by r-senior on 2011-06-11
You only need to free the pointer that points at the start of the block of memory you allocated, not both your pointers. Does it work if you do that?

---

### Post by cdiem on 2011-06-11
> **r-senior said:**
> You only need to free the pointer that points at the start of the block of memory you allocated, not both your pointers. Does it work if you do that?

Awesome! Yes, it does - if I leave the "free(now);" line. 

Thanks a lot - I wouldn't have been able to debug this at all.

---

### Post by cgroza on 2011-06-11
> **cdiem said:**
> Nope, it says segmentation fault. I'm not sure why though :)
Your second free() tries to delete memory already freed by the first free().

---

### Post by r-senior on 2011-06-11
> **cgroza said:**
> Your second free() tries to delete memory already freed by the first free().
I think the second free(), i.e. free(reversed), was freeing a pointer that was pointing at the end of the string.

---

### Post by psusi on 2011-06-11
Rather than try to manipulate the pointer back to its original value to free it, and getting that wrong, it would be wiser to simply keep the original around.

---

### Post by JupiterV2 on 2011-06-12
Now that you have an idea of what to look for, next time you get a segfault and it's not immediately obvious why you're getting one, try using gdb. The GNU debugger is your friend. Load your program with the command:
```
gdb ./my_program
```
... where ./my_program is the name of your application. From within gdb, run the following commands:

[LIST=1]
[*]run - start the program and execute until either the segfault occurs or the application exits normally
[*]bt or backtrace - will give you some information on what some of your variables contained and the stack trace of when the error happened.
[*]p <your_variable_name> or print <your_variable_name> - print the contents of a variable. Replace <your_variable_name> with the name of the variable to inspect, without the backets
[/LIST]

Also, pay attention to the backtrace your OS may have printed for you, if any. Sometimes it will report a 'double-free' if you try to free the same memory twice.

---

### Post by zobayer1 on 2011-06-12
Ah, as the thread is already here, I would just like to ask one more question.

Suppose, I have created a link list by dynamically allocating memory to each record. Now, just freeing the head should not release the total memory consumed by the linked list. Am I correct? Or C/C++ garbage collection technique is enough intelligent to sense which memory is of no use?

I am asking this because few months back, I was getting "Memory Limit Exceed" sort of result to a program, but I just added "delete head;" and surprisingly it passed. (Obviously when I remove them one by one also worked.)

Thanks in advance !

---

### Post by Barrucadu on 2011-06-12
I don't know about C++, but C has no automatic garbage collection, so you would have to free all the records.

---

### Post by cgroza on 2011-06-12
You have to go through your list and delete all the elements. C++ does not offer garbage collection. There are some garbage collectors but you would have to learn how to use them.

---

### Post by dwhitney67 on 2011-06-12
@ the OP:

The reason the rewinding of the pointer to the reversed string failed was due to a couple of reasons:

1.  You incremented the 'reverse' pointer one to many times; this would have sufficed:
```

*reverse = '\0';    /* note that the pointer is not post-incremented */

```

2.  You were dereferencing the pointer when you attempted the pointer arithmetic:
```

*reverse = *reverse - strlen(test);   /* BAD */

reverse = reverse - strlen(test);     /* GOOD */

```

At any rate, if you want to stick with the secondary pointer (called 'now'?), that is fine.

Here's a spin on your program:
```

#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main(int argc, char** argv)
{
    char*  test = NULL;
    size_t test_len = 0;
    char*  reversed = NULL;
    int    i;

    // verify command line arg string is present
    if (argc != 2)
    {
        fprintf(stderr, "Usage: %s <string>\n", argv[0]);
        exit(EXIT_FAILURE);
    }

    test = argv[1];
    test_len = strlen(test);

    // allocate memory for the reversed string
    if ((reversed = malloc(test_len + 1)) == NULL)
    {
        perror("malloc");
        exit(EXIT_FAILURE);
    }

    // reverse the string
    for (i = test_len - 1; i >= 0; i--)
    {
        *reversed++ = test[i];
    }

    // add terminating null to reversed string
    *reversed = '\0';

    // rewind the pointer of the reversed string
    reversed -= test_len;

    printf("reversed string: %s\n", reversed);

    // free allocated memory
    free(reversed);

    return EXIT_SUCCESS;
}

```

---

### Post by zobayer1 on 2011-06-12
> **cgroza said:**
> You have to go through your list and delete all the elements. C++ does not offer garbage collection. There are some garbage collectors but you would have to learn how to use them.

That's what I knew so far, and that's why I am wondering why my program passed... Because, just deleting the head pointer is of no use. Probably I will need to look inside it again.. However, when I delete head, there remains no active pointer to any other elements. Has g++ added something new?

---

### Post by cgroza on 2011-06-12
> **zobayer1 said:**
> That's what I knew so far, and that's why I am wondering why my program passed... Because, just deleting the head pointer is of no use. Probably I will need to look inside it again.. However, when I delete head, there remains no active pointer to any other elements. Has g++ added something new?

When you delete the head, you have no other way to access the other elements. If they were allocated on the heap, they are lost until the OS request them back, which is on program exit.

---

### Post by zobayer1 on 2011-06-12
> **cgroza said:**
> When you delete the head, you have no other way to access the other elements. If they were allocated on the heap, they are lost until the OS request them back, which is on program exit.

Ah, now it makes sense, I allocated them on the heap...
Thanks a lot :D

---


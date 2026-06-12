---
title: "writing a string from the command line to file in C"
date: 2010-06-16
forum: Programming Talk
---

### Post by blackcobra on 2010-06-16
This is what i have:

#include <stdio.h> 
int main() {
  FILE *file; 
  file = fopen("file.txt","a+"); 
  //Was thinking for or while loop using the getchar() function
  //what i'm trying to do here is scan a string from the command line to the file by looping
  fprintf(file,"%c", getchar());
  fclose(file);  
  return 0; 
}

---

### Post by -grubby on 2010-06-16
It's good practice to indent your code. If your code was already indented, the indentation got lost because you didn't use the [noparse][code][/noparse] tags.

That said, you should use scanf() instead of getchar() if you want to get the whole line at once. For example: scanf("%d", &some_int).

---

### Post by Some Penguin on 2010-06-16
The command line, as in a param passed to the program, or as in what's typed after the program is run (or piped in)?

---

### Post by blackcobra on 2010-06-16
> **Some Penguin said:**
> The command line, as in a param passed to the program, or as in what's typed after the program is run (or piped in)?

terminal, command prompt. Sorry if my terminology is wrong!

---

### Post by lisati on 2010-06-16
> **blackcobra said:**
> terminal, command prompt. Sorry if my terminology is wrong!
So you want to type something in when your program is running?

---

### Post by blackcobra on 2010-06-16
> **-grubby said:**
> It's good practice to indent your code. If your code was already indented, the indentation got lost because you didn't use the [noparse][code][/noparse] tags.

That said, you should use scanf() instead of getchar() if you want to get the whole line at once. For example: scanf("%d", &some_int).

I tried this with no success
declared the string
for(i=0; i<=10; i++){
fprintf(file,"%s", scanf("%s" &s[50]));
}
and 
for(i=0; i<=10; i++){
fprintf(file, scanf("%s" &s[50])); 
}

---

### Post by blackcobra on 2010-06-16
> **lisati said:**
> So you want to type something in when your program is running?

yep Exactly!

---

### Post by =CrAzYG33K= on 2010-06-16
```
#include <stdio.h>

int main()
{
char * input_str[10];
FILE *file;
file = fopen("file.txt","a+");
scanf("%s", &input_str);
fprintf(file, "%s", input_str);
fclose(file);

return 0;
}

```

This does it for me.. (an input string of 10 chars used)

**EDIT:**

Is this what you wanted?

---

### Post by blackcobra on 2010-06-16
> **=CrAzYG33K= said:**
> ```
#include <stdio.h>

int main()
{
char * input_str[10];
FILE *file;
file = fopen("file.txt","a+");
scanf("%s", &input_str);
fprintf(file, "%s", input_str);
fclose(file);

return 0;
}

```

This does it for me.. (an input string of 10 chars used)

**EDIT:**

Is this what you wanted?

Yep, Legend!

---

### Post by dwhitney67 on 2010-06-16
> **blackcobra said:**
> Yep, Legend!

I'm surprised nobody chimed in earlier to indicate that scanf() is the least desirable function to use to get string input from the terminal.

In CrAzYG33K example, what would happen if the user enters more than 10 characters on the input stream?  scanf() is not going to be graceful and only take the first 10... it will take them all until a newline is found in the stream (or stop when the program crashes).

The preferred function to use is fgets(), where the programmer can specify the maximum amount of characters they want this function to accept.

For instance:
```

...

char input[10];

printf("Enter a string: ");
fgets(input, sizeof(input), stdin);

...

```

---

### Post by schauerlich on 2010-06-16
The only problem is that scanf("%s") isn't very good at reading in a whole line of text, and will stop at the first whitespace. To read in the whole line, you should use fgets().

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define BUFF_LEN 256

int main()
{
  FILE *outf = fopen("foo.txt", "w");
  char buffer[BUFF_LEN] = {0};

  if (!outf)
    return EXIT_FAILURE;

  while (!ferror(stdin) && !ferror(outf)) {
    fgets(buffer, BUFF_LEN, stdin);

    if (!strcmp("q\n", buffer))
        break;

    fputs(buffer, outf);
  }

  fclose(outf);

  return EXIT_SUCCESS;
} // main()

```

---

### Post by blackcobra on 2010-06-17
Thats exactly what i was trying to do!

---

### Post by =CrAzYG33K= on 2010-06-17
> **dwhitney67 said:**
> I'm surprised nobody chimed in earlier to indicate that scanf() is the least desirable function to use to get string input from the terminal.

In CrAzYG33K example, what would happen if the user enters more than 10 characters on the input stream?  scanf() is not going to be graceful and only take the first 10... it will take them all until a newline is found in the stream (or stop when the program crashes).

The preferred function to use is fgets(), where the programmer can specify the maximum amount of characters they want this function to accept.

For instance:
```

...

char input[10];

printf("Enter a string: ");
fgets(input, sizeof(input), stdin);

...

```

Well, I had to come up with something quick and easy, importantly something that's easy for a newbie to understand. Having said that, I don't deny that my code was a bad example, it simply was. And thank a lot for being syntactically correct. I appreciate it! :p

---


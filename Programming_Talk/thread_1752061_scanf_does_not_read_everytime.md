---
title: "scanf does not read everytime"
date: 2011-05-07
forum: Programming Talk
---

### Post by mert_da on 2011-05-07
Hello!

I use scanf function on my C program. But scanf **sometimes** does not waits to read my characters from command line.

Many programmers told me that to use fflush(stdin) and fflush(stdout) every time before scanf line on code. But this does not worked for me. Also fflush is not on standart C. That's why i don't want to use it.

Can someone help me please ?

Thank you!

---

### Post by Arndt on 2011-05-07
> **mert_da said:**
> Hello!

I use scanf function on my C program. But scanf **sometimes** does not waits to read my characters from command line.

Many programmers told me that to use fflush(stdin) and fflush(stdout) every time before scanf line on code. But this does not worked for me. Also fflush is not on standart C. That's why i don't want to use it.

Can someone help me please ?

Thank you!

Can you show some code?

---

### Post by dwhitney67 on 2011-05-07
If I only had a penny for every time I've seen this question.

@ the OP:   Play with this code.
```

#include <stdio.h>

int main(void)
{
   char yes_no;

   printf("Answer y or n to reveal your personal fortune: ");
   scanf("%c", &yes_no);

   if (yes_no == 'y')
   {
      printf("On the stdin-stream, a newline still awaits you.\n");
      printf("Let's find it...\n");

      while (getchar() != '\n');

      printf("I found the newline!\n");
   }

   printf("bye!\n");

   return 0;
}

```

---

### Post by Tony Flury on 2011-05-07
Scanf (or fscanf) is fine if your input is guaranteed to be regular (i.e. same format in all cases.

For something like a command line i would use fget to get a line - and parse it "by hand".

---

### Post by nvteighen on 2011-05-07
You have to understand how stdio I/O works in C.

stdin and stdout are buffers for input and output, respectively. Whatever you input or output gets there before doing anything else. These buffers only hold stuff up to any '\n' character, so we usually say that I/O in C is line-buffered. Also, these buffers will be emptied only if the data in them is actually retrieved; if you don't get what's in them, the data will remain there.

Now, another thing you have to take in account is that all the stdio I/O functions actually operate on stdin and stdout, not on the real input/output. E.g. when you perform a scanf(), all scanf() does is to look up if something is there at stdin to retrieve. If nothing is found (stdin is empty), the user gets prompted, but not because of scanf(), but rather because of the system (If you redirect stdin to a normal file, no prompt would appear... btw, that's what fscanf does).

Generally, stdout doesn't give too much trouble because output is usually guarranteed to be retrieved by the shell or by whatever is used as output device.

The issue is stdin. In a nutshell: always keep in mind that 1) stdio input functions actually just get what's stored in stdin, 2) that the user is prompted only when stdin is found to be empty and 3) characters are removed from stdin when read from it. So, the challenge is to be sure that stdin will be empty whenever you want your program to ask the user for input. The easiest and most portable way is to "flush" stdin by asking for input again until the '\n' is found and store the unused data into a "garbage" buffer (getline is the best, but it's GCC-specific... fgets can be helpful though).

---


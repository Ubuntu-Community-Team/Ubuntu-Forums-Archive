---
title: "[C/C++] popen: Wait for Subprocess to Finish"
date: 2012-06-14
forum: Programming Talk
---

### Post by dodle on 2012-06-14
I'm using [color=blue]popen[/color] to open a subprocess, but I don't know how to get the program to wait until the process finishes to continue. I've searched the forum and googled "c popen wait" but can't find an answer. The [color=blue]system[/color] command works for this but I have been warned not to use it.

[php]#include <stdio.h>

int main()
{
  popen("sleep 4 && echo done! 2>&1", "r");
  printf("Subprocess finished.\n");
  
  return 0;
}[/php]

Is there a way to wait for [color=blue]popen[/color] to finish, or is there a better way to open a subprocess?

**----- Solved -----**

Ah, figured it out:

[php]#include <stdio.h>

int main()
{
  FILE* test = popen("sleep 4 && echo done! 2>&1", "r");
  pclose(test);
  printf("Subprocess finished.\n");
  
  return 0;
}[/php]

However, I'm having an issue getting popen to print the output of the process to stdout.

---

### Post by Bachstelze on 2012-06-14
Have you read the manual for popen()?

---

### Post by dodle on 2012-06-14
Sorry Bachstelze, I think I edited my post while you were doing yours.

I found the solution that I wanted, thanks to [this post]("http://www.linuxquestions.org/questions/programming-9/c-c-popen-launch-process-in-specific-directory-620305/#post3053479"):

[php]#include <stdio.h>

int main()
{
  FILE* test = popen("sleep 4 && echo done!", "r");
  if (test == NULL)
  {
    printf("FAIL!\n");
    return 1;
  }
  
  char buffer[1028];
  
  while (fgets(buffer, 1028, test) != NULL)
  {
    printf(buffer);
  }
  
  pclose(test);
  printf("Success.\n");
  
  return 0;
}[/php]

---


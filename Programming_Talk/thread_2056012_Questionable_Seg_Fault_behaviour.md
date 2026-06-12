---
title: "Questionable Seg Fault behaviour"
date: 2012-09-10
forum: Programming Talk
---

### Post by Amante56 on 2012-09-10
I'm not exactly a newcomer to C, but it has been a while. Lately I've been trying to connect C and MySQL, however I can't seem to get past this really weird hurdle...

So my end goal is to get user input for searching the database, but I can't get past the input because of constant Seg Faults. Any help is appreciated, thank you...

This code operates fine:
```

#include <stdio.h>
#include <string.h>

int main(void) {
    char buffer[30];
    
    printf("Input your name: ");
//    fgets(buffer, 10, stdin);
    scanf("%s", buffer);
    printf("\n\n%s is awesome", buffer);

//    comm = strcat("SELECT name FROM statistics WHERE name = '", buffer);
//    comm = strcat(comm,"'");
//    printf("%s\n",comm);
}
```This fails...
```
#include <stdio.h>
#include <string.h>

int main(void) {
    char *buffer;
    
    printf("Input your name: ");
//    fgets(buffer, 10, stdin);
    scanf("%s", buffer);
    printf("\n\n%s is awesome", buffer);

//    comm = strcat("SELECT name FROM statistics WHERE name = '", buffer);
//    comm = strcat(comm,"'");
//    printf("%s\n",comm);
```This doesn't either...
```
#include <stdio.h>
#include <string.h>

int main(void) {
    char *buffer;
    
    printf("Input your name: ");
    fgets(buffer, 10, stdin);
//    scanf("%s", buffer);
    printf("\n\n%s is awesome", buffer);

//    comm = strcat("SELECT name FROM statistics WHERE name = '", buffer);
//    comm = strcat(comm,"'");
//    printf("%s\n",comm);
}
```and bizarrely enough...

this does work:
```
#include <stdio.h>
#include <string.h>

int main(void) {
    char buffer[10];
    
    printf("Input your name: ");
    fgets(buffer, 10, stdin);
//    scanf("%s", buffer);
    printf("\n\n%s is awesome", buffer);

//    comm = strcat("SELECT name FROM statistics WHERE name = '", buffer);
//    comm = strcat(comm,"'");
//    printf("%s\n",comm);
}
```but a slight modification, not even touching the working parts, and it doesn't
```
#include <stdio.h>
#include <string.h>

int main(void) {
    char buffer[10], *comm;
    
    printf("Input your name: ");
    fgets(buffer, 10, stdin);
//    scanf("%s", buffer);
    printf("\n\n%s is awesome", buffer); /*It segfaults here*/

    comm = strcat("SELECT name FROM statistics WHERE name = '", buffer);
    comm = strcat(comm,"'");
    printf("%s\n",comm);
}
```Once again, any guidance is greatly appreciated...

---

### Post by Bachstelze on 2012-09-10
Your first strcat() is wrong because you are trying to write to a string literal.

---

### Post by Amante56 on 2012-09-10
Thanks, I guess that really was a problem, unfortunately it didn't solve the seg fault errors.

I'm getting seg fault no matter what I do, at this particular line:
```
printf("\n\n%s is awesome", buffer);
```

---

### Post by Bachstelze on 2012-09-10
No, it does not segfault here, it segfaults at the line after it.

---

### Post by Odexios on 2012-09-10
This code doesn't segfault to me:

[php]#include <stdio.h>
#include <string.h>
#include <stdlib.h>

#define STRING_BEGIN "SELECT name FROM statistic WHERE name = '"
#define STRING_END "'"

int main(void) {
  char buffer[10], *comm;
  int i;

  printf("Input your name: ");
  fgets(buffer, 10, stdin);

  printf("\n%s is awesome\n", buffer); /*It segfaults here*/

  return 0;
}
[/php]
Up to the printf part it's the same as yours; the segfault is later.

Look up how strcat works, it seems like you don't remember its prototype very well; besides, you haven't malloced comm. Lastly, if the name is shorter than 9 characters there's a newline in buffer you haven't removed.

---

### Post by Amante56 on 2012-09-10
Ok, I finally got what you meant, thanks by the way. Both of them are now pointer variables, but it still isn't working:

```
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main(void) {
    char *buffer;
    char *comm = "SELECT name FROM statistics WHERE name = '";
    buffer = (char *)malloc(25);    

    printf("Input your name: ");
    scanf("%s", buffer);
    printf("\n %s is awesome\n", buffer);

    comm = strcat(comm, buffer);
    printf("%s\n",comm);

    free(buffer);
}
```Seg Fault still occurs at strcat...

Although, does the destination string need to be larger? even though they're both pointers???

---

### Post by Odexios on 2012-09-10
May I write you a short program which does what I think you're trying to do?

I'm sure it'll be easier to understand what's wrong by confrontation.

[php]#include <stdio.h>
#include <string.h>
#include <stdlib.h>

#define STRING_BEGIN "SELECT name FROM statistic WHERE name = '"
#define STRING_END "'"
/*just shortcuts*/

int main(void) {
  char buffer[10], *comm;
  int i;

  printf("Input your name: ");
  fgets(buffer, 10, stdin);
  /*this is to remove the trailing newline*/
  for (i = 0; buffer[i] != '\0'; i++)
  {
    if (buffer[i] == '\n')
    {
      buffer[i] = '\0';
      break;
    }
  }
  printf("\n%s is awesome\n", buffer);


  comm = malloc(sizeof(char) * (strlen(STRING_BEGIN) +
                                strlen(buffer) +
                                strlen(STRING_END) + 1));
  /*you need to allocate space in comm to store the final string*/
  comm[0] = '\0';
  /*strcat adds to the first string the second string; the first argument
   must be a string, so the comm[0] = '\0' line. You could use strcpy the
   first time instead*/
  strcat(comm, STRING_BEGIN);
  strcat(comm, buffer);
  strcat(comm, STRING_END);
  printf("%s\n",comm);

  return 0;
}
[/php]

---

### Post by Amante56 on 2012-09-10
Ah, I understand. So the pointer that will hold the final value needs to have been allocated with enough memory to handle the total size. Well I suppose that makes sense. I guess I really have forgotten how to handle pointers...

In any case, thank you so much for the help.

---

### Post by Bachstelze on 2012-09-10
> **Amante56 said:**
> Ok, I finally got what you meant, thanks by the way. Both of them are now pointer variables, but it still isn't working:

You didn't actually change anything. ;) There is no difference between a pointer to a string literal and a string literal itself, they point to the same area in memory, and your problem was that you were trying to write to this memory area, which is read-only.

---


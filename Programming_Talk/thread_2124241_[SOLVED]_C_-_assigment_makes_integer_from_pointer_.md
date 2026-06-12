---
title: "[SOLVED] C - assigment makes integer from pointer without a cast warning"
date: 2013-03-10
forum: Programming Talk
---

### Post by usernamer on 2013-03-10
I know it's a common error, and I've tried googling it, looked at a bunch of answers, but I still don't really get what to do in this situation....
Here's the relevant code:
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main( int argc, char *argv[] )
{
    char path[51];
    const char* home = getenv( "HOME" );

    strcpy( path, argv[1] );

    path[1] = home;

    return 0;
}

```

-- there is more code in the blank lines, but the issue's not there (I'm fairly sure), so didn't see the point in writing out 100 odd lines of code.
I've tried some stuff like trying to make a pointer to path[1], and make that = home, but haven't managed to make that work (although maybe that's just me doing it wrong as opposed to wrong idea?)

Thanks in advance for any help

---

### Post by r-senior on 2013-03-10
path[1] is the second element of a char array, so it's a char. home is a char *, i.e. a pointer to a char. 

You get the warning because you try to assign a char* to a char.

Note also the potential to overflow your buffer if the content of the argv[1] argument is very long. It's usually better to use strncpy.

---

### Post by Christmas on 2013-03-10
You can try something like this:
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main( int argc, char *argv[] )
{
  char *path;
  const char *home = getenv("HOME");

  path = malloc(strlen(home) + 1);
  if (!path) {
    printf("Error\n");
    return 0;
  }
  strcpy(path, home);
  printf("path = %s\n", path);

  // if you want to have argv[1] concatenated with path
  if (argc >= 2) {
    path = malloc(strlen(home) + strlen(argv[1]) + 1);
    strcpy(path, argv[1]);
    strcat(path, home);
    printf("%s\n", path);
  }

  // if you want an array of strings, each containing path, argv[1]...
  char **array;
  int i;

  array = malloc(argc * sizeof(char*));

  array[0] = malloc(strlen(home) + 1);
  strcpy(array[0], home);
  printf("array[0] = %s\n", array[0]);

  for (i = 1; i < argc; i++) {
    array[i] = malloc(strlen(argv[i]) + 1);
    strcpy(array[i], argv[i]);
    printf("array[%d] = %s\n", i, array[i]);
  }
  // now array[i] will hold path and all the argv strings

  return 0;
}

```
Just as above, your path[51] is a string while path[1] is only a character, so you can't use strcpy for that.

---

### Post by usernamer on 2013-03-10
> **Christmas said:**
> You can try something like this:
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main( int argc, char *argv[] )
{
  char *path;
  const char *home = getenv("HOME");

  path = malloc(strlen(home) + 1);
  if (!path) {
    printf("Error\n");
    return 0;
  }
  strcpy(path, home);
  printf("path = %s\n", path);

  // if you want to have argv[1] concatenated with path
  if (argc >= 2) {
    path = malloc(strlen(home) + strlen(argv[1]) + 1);
    strcpy(path, argv[1]);
    strcat(path, home);
    printf("%s\n", path);
  }

  // if you want an array of strings, each containing path, argv[1]...
  char **array;
  int i;

  array = malloc(argc * sizeof(char*));

  array[0] = malloc(strlen(home) + 1);
  strcpy(array[0], home);
  printf("array[0] = %s\n", array[0]);

  for (i = 1; i < argc; i++) {
    array[i] = malloc(strlen(argv[i]) + 1);
    strcpy(array[i], argv[i]);
    printf("array[%d] = %s\n", i, array[i]);
  }
  // now array[i] will hold path and all the argv strings

  return 0;
}

```
Just as above, your path[51] is a string while path[1] is only a character, so you can't use strcpy for that.

Excellent point. I've basically fixed my problem by reading up on pointers again (haven't done any C for a little while, so forgot some stuff), and doing:
```
path[1] = *home;
```
the code doesn't moan at me when I compile it, and it runs okay (for paths which aren't close to 51 at least), but after reading what you read, I just wrote a quick program and found out that getenv("HOME") is 10 characters long, not 1 like I seem to have assumed, so I'll modify my code to fix that.

---

### Post by Christmas on 2013-03-10
Yes, getenv will return the path to your home dir, for example /home/user, but path[1] = *home will still assign the first character of home to path[1] (which would be '/').

---


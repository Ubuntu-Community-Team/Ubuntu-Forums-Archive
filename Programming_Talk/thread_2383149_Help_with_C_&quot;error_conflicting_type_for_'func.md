---
title: "Help with C &quot;error: conflicting type for 'function'&quot;"
date: 2018-01-21
forum: Programming Talk
---

### Post by frozenechoes on 2018-01-21
[SIZE=2]I have looked at several posts in an attempt to solve this problem, and every one I look at has a simple solution like "declare the function before you use it" or "match the types of the parameters in the declaration and the definition."
Both of these are already true for my program so I have become desperate and am turning to this forum.
Worst of all, **I have copied this entire program directly out of a "how-to C" book**, and double-checked it, and it doesn't even compile.
Please help :/

Here's my code:

[/SIZE][INDENT][SIZE=2][FONT=arial]#include <stdio.h>[/FONT]
[FONT=arial]#define MAXLINE 1000[/FONT]

[FONT=arial]int getline(char s[], int lim);[/FONT]
[FONT=arial]void copy(char to[], char from[]);[/FONT]

[FONT=arial]/* print longest input line */[/FONT]
[FONT=arial]int main() {[/FONT]
[FONT=arial]  int len;[/FONT]
[FONT=arial]  int max;[/FONT]
[FONT=arial]  char line[MAXLINE];[/FONT]
[FONT=arial]  char longest[MAXLINE];[/FONT]

[FONT=arial]  max = 0;[/FONT]
[FONT=arial]  while ((len = getline(line, MAXLINE)) > 0) {[/FONT]
[FONT=arial]    if (len > max) {[/FONT]
[FONT=arial]      max = len;[/FONT]
[FONT=arial]      copy(longest, line);[/FONT]
[FONT=arial]    }[/FONT]
[FONT=arial]  }[/FONT]
[FONT=arial]  if (max > 0) /* check if there was any lines at all*/[/FONT]
[FONT=arial]    printf("%s", longest);[/FONT]
[FONT=arial]  return 0;[/FONT]
[FONT=arial]}[/FONT]

[FONT=arial]/* getline: read a line into s, return length */[/FONT]
[FONT=arial]int getline(char s[], int lim) {[/FONT]
[FONT=arial]  int c, i;[/FONT]

[FONT=arial]  for(i = 0; i < lim - 1 && (c = getchar()) != EOF && c != '\n'; ++i) {[/FONT]
[FONT=arial]    s[i] = c;[/FONT]
[FONT=arial]  }[/FONT]
[FONT=arial]  if (c == '\n') {[/FONT]
[FONT=arial]    s[i] = c;[/FONT]
[FONT=arial]    ++i;[/FONT]
[FONT=arial]  }[/FONT]
[FONT=arial]  s[i] = '\0';[/FONT]
[FONT=arial]  return i;[/FONT]
[FONT=arial]}[/FONT]

[FONT=arial]/* copy: copy 'from' into 'to'; assume to is big enough */[/FONT]
[FONT=arial]void copy(char to[], char from[]) {[/FONT]
[FONT=arial]  int i;[/FONT]

[FONT=arial]  i = 0;[/FONT]
[FONT=arial]  while ((to[i] = from[i]) != '\0')[/FONT]
[FONT=arial]    ++i;[/FONT]
[FONT=arial]}
[/FONT][/SIZE][/INDENT]
[SIZE=2][FONT=arial]
Pretty simple, I thought. Here's the error after I type gcc -Wall longestline.c:

[/FONT][/SIZE][INDENT][SIZE=2][FONT=arial]longestline.c:4:5: error: conflicting types for ‘getline’[/FONT]
[FONT=arial] int getline(char s[], int lim);[/FONT]
[FONT=arial]     ^[/FONT]
[FONT=arial]In file included from longestline.c:1:0:[/FONT]
[FONT=arial]/usr/include/stdio.h:678:20: note: previous declaration of ‘getline’ was here[/FONT]
[FONT=arial] extern _IO_ssize_t getline (char **__restrict __lineptr,[/FONT]
[FONT=arial]                    ^[/FONT]
[FONT=arial]longestline.c:27:5: error: conflicting types for ‘getline’[/FONT]
[FONT=arial] int getline(char s[], int lim) {[/FONT]
[FONT=arial]     ^[/FONT]
[FONT=arial]In file included from longestline.c:1:0:[/FONT]
[FONT=arial]/usr/include/stdio.h:678:20: note: previous declaration of ‘getline’ was here[/FONT]
[FONT=arial] extern _IO_ssize_t getline (char **__restrict __lineptr,
[/FONT][FONT=arial]
[/FONT][/SIZE][/INDENT]
[SIZE=2][FONT=arial]With my luck it will probably end up being something really dumb, or a typo. Or maybe a change between the version of C the book teaches ( C from '88?) and the current version on Ubuntu.
Thanks.[/FONT][/SIZE]

---

### Post by frozenechoes on 2018-01-21
Sorry, formatting got messed up when auto-indenting.

---

### Post by spjackson on 2018-01-21
getline is declared in stdio.h. 'man getline' says
```

ssize_t getline(char **lineptr, size_t *n, FILE *stream);

       Both  getline() and getdelim() were originally GNU extensions.  They were
       standardized in POSIX.1-2008.

```
A solution is to rename your function - e.g. my_getline.

---

### Post by frozenechoes on 2018-01-21
Thanks. A friend of mine suggested renaming it "gettline" and it compiled. I was simultaneously angry and relieved.

---


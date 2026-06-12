---
title: "no effect of indent command"
date: 2010-11-02
forum: Programming Talk
---

### Post by tapas_mishra on 2010-11-02
Following is the code
```
#include <stdio.h>
struct key
{
  char *word;
  int count;
} keytab[] =
{
  "auto", 0,
    "break", 0, "case", 0, "char", 0, "const", 0, "continue", 0, "default", 0,
/* ... */
"unsigned", 0, "void", 0, "volatile", 0, "while", 0};

int
main ()
{
  char s[] = { 'a', 'e', 'i', 'o', 'u', '\0' };
  int d;
  d = s[0] - '0';
  printf ("%d", d);
}
```

I did 
```
indent -kr temp.c
```
there seemed no effect on indentation of code.
Then I tried 
```
indent -gnu temp.c
```
Still it looks like
```
#include <stdio.h>
struct key
{
  char *word;
  int count;
} keytab[] =
{
  "auto", 0,
    "break", 0, "case", 0, "char", 0, "const", 0, "continue", 0, "default", 0,
/* ... */
"unsigned", 0, "void", 0, "volatile", 0, "while", 0};

int
main ()
{
  char s[] = { 'a', 'e', 'i', 'o', 'u', '\0' };
  int d;
  d = s[0] - '0';
  printf ("%d", d);
}
```

and then I tried 
> indent -linux temp.c
```

#include <stdio.h>
struct key {
    char *word;
    int count;
} keytab[] = {
    "auto", 0,
        "break", 0, "case", 0, "char", 0, "const", 0, "continue", 0,
        "default", 0,
/* ... */
"unsigned", 0, "void", 0, "volatile", 0, "while", 0};

int main()
{
    char s[] = { 'a', 'e', 'i', 'o', 'u', '\0' };
    int d;
    d = s[0] - '0';
    printf("%d", d);
}
```
I do not see any noticeable difference in any of the three methods I tried.Am I doing some thing wrong?

---

### Post by Queue29 on 2010-11-02
Use the -o outfile flag. Also iirc there's -w which will overwrite the source files.

Otherwise it just prints the output to stdout.

---

### Post by matthew.ball on 2010-11-02
You might want to read [this]("http://en.wikipedia.org/wiki/Indent_style") then.

---


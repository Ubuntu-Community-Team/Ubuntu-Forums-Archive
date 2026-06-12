---
title: "[C] check if string1 ends in string2"
date: 2009-04-12
forum: Programming Talk
---

### Post by roccivic on 2009-04-12
Hi all,

I'm having some hard time trying to implement a piece of code into my program. I have a function that returns a pointer to a string containing a filename. I then would like to check if this string ends in ".foo" and if it does, swap the extention to ".bar".

Should be something along the lines of:
```
char   *filename;

filename = function_that_fetches_the_filename();

if (filename ends in ".foo") {
    remove ".foo";
    append ".bar";
}
```

Many thanks for any help in advance.
Rouslan.

---

### Post by scourge on 2009-04-12
> **roccivic said:**
> Hi all,

I'm having some hard time trying to implement a piece of code into my program. I have a function that returns a pointer to a string containing a filename. I then would like to check if this string ends in ".foo" and if it does, swap the extention to ".bar".

Should be something along the lines of:
```
char   *filename;

filename = function_that_fetches_the_filename();

if (filename ends in ".foo") {
    remove ".foo";
    append ".bar";
}
```

Many thanks for any help in advance.
Rouslan.

I don't have a compiler ready, but something like this:
```

int len = strlen(filename);
if (len >= 4) {
    char *pos = filename + len - 4;
    if (strcmp(pos, ".foo") == 0)
        strcpy(pos, ".bar");
}

```

---


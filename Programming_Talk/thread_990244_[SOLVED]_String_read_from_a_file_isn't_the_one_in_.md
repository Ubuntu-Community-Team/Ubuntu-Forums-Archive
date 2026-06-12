---
title: "[SOLVED] String read from a file isn't the one in the file???"
date: 2008-11-22
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-22
I use C.

This string:
> data/test.bmp
Will look like this:
> &#65533;?&#1975;&#65533;<&#1015;&#65533;?&#1975;&#65533;&#65533;&#65533;&#65533;=&#65533;.e#

With this code:
```

int line_max = 80;
char line[line_max];

char string[line_max];
strcpy( string, line );

// remove the endline character from string
string[strlen(string)-1] = '\0';

printf("%s\n", string);

```

Am I using wrong data types? How is this possible?

Edit: Solved myself.
When creating a string variable, it will be filled with garbage.
And I forgot to read the line from file before doing that part of code, lol.

---

### Post by nvteighen on 2008-11-22
Which leads us to the old saying: "Always initialize your memory".

---


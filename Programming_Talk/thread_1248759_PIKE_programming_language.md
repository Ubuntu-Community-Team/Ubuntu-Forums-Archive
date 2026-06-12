---
title: "PIKE programming language"
date: 2009-08-24
forum: Programming Talk
---

### Post by 7raTEYdCql on 2009-08-24
I need help with PIKE. I want to input integers directly in PIKE. I can input strings using the following syntax:
```

string name=Stdio.stdin->gets();
write(name);

```

But suppose if i want the variable name to hold a integer which is inputted by the user, how is this done. I haven't found this in the entire documentation. It seems like only strings can be given as input. And even if strings can be input, how do you convert the strings to integers.

The documentation mentions about sscanf, but i always seem to be getting compilation error. Can someone please help.

---

### Post by 7raTEYdCql on 2009-08-26
I figured this out myself, and this is for anyone who probably face this.
PIKE takes in input only as strings. To filter out required data from the strings we can use sscanf commands. And for printing integers etc, sprintf can be used. Check out the PIKE documentation.

Talking about the language, it is basically a C programming language with capabilities of handling big numbers. Which aren't so with normal C, therefore is pretty useful in coding competitions, considering it has a C/C++ type syntax. :)

---


---
title: "JAVA - how to check if user input is not an int value"
date: 2013-08-08
forum: Programming Talk
---

### Post by 7nQecEL on 2013-08-08
[COLOR=#000000][FONT=verdana]I'm trying to figure out how to check if user input is not an int value[/FONT][/COLOR]
```

[FONT=verdana][COLOR=#000000]Solved it

```
Line 25 is the first two line in that bit of code[/COLOR][/FONT]

---

### Post by r-senior on 2013-08-08
You need to check hasNextInt() *before* you attempt to use nextInt() on line 25.

HINT: You can use next() to skip to the next input token.

Are scan and sc both instances of Scanner? Or did you just mistype?

---


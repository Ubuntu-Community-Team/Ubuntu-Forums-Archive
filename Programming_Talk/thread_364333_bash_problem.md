---
title: "bash problem"
date: 2007-02-18
forum: Programming Talk
---

### Post by paca on 2007-02-18
I can run

```
santa=( 1 2 3 )
``` and it works perfect, but when i run it in a script i get the 
test.sh: 2: Syntax error: "(" unexpected

```
#!/bin/bash
santa=( 1 2 3 )
```

works on other computers, just not on mine :(

any ideas?

---

### Post by Arndt on 2007-02-20
> **paca said:**
> I can run

```
santa=( 1 2 3 )
``` and it works perfect, but when i run it in a script i get the 
test.sh: 2: Syntax error: "(" unexpected

```
#!/bin/bash
santa=( 1 2 3 )
```

works on other computers, just not on mine :(

any ideas?

It seems from the error message that what's being run is a plain Bourne shell, not bash, but that's strange, since you do specify bash.

Do you know which shell you're running, where the command line works? Does it work to start /bin/bash interactively and the type the same thing?

Has something happened with how the shells are linked? Do "ls -l /bin/*sh*" and study the output.

---


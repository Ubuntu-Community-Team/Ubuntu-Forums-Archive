---
title: "when I over write a file in teminal it leave an old copy, why?"
date: 2012-01-13
forum: New to Ubuntu
---

### Post by REMIX8604 on 2012-01-13
Why is it, when I save and overwrite a file in the terminal it leaves a copy of the old file with a tilde after it? and is there a way to stop this? its becoming annoying to keep removing it.

> 

user@ubuntu:~/prog$ ls
  hello.c  main.c  makefile  world.c
user@ubuntu:~/prog$ gedit makefile #I edited and overwrite this file
user@ubuntu:~/prog$ ls
  hello.c  main.c  makefile  makefile~  world.c
user@ubuntu:~/prog$ rm makefile~ #why is this file here?



---

### Post by lisati on 2012-01-13
It's a backup copy, equivalent to the "bak" files in MS-DOS and Windows.

---

### Post by mcduck on 2012-01-13
The editor you are using is configured to save a backup copy before overwriting the original file. If you don't want that, then juts chage the editor's settings.

---


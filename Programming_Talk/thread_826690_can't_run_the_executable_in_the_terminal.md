---
title: "can't run the executable in the terminal"
date: 2008-06-12
forum: Programming Talk
---

### Post by kboy on 2008-06-12
hi, i made a simple 'hello world' program in anjuta, when i build it runs perfectly in the anjuta IDE, but when i try to run the executable file int the terminal it says:

bash: project1: command not found

(the file name is project1)

what is the problem? am i doing some thing wrong?

---

### Post by petterAn on 2008-06-12
Try ./project1

---

### Post by kboy on 2008-06-12
thanks, it worked :)

---

### Post by Joeb454 on 2008-06-12
It's because either:

1) You need to run ```
chmod +x ./project1
``` first (unlikely, but possible)

2) The bash prompt doesn't usually look in your current directory for the commands, so you need to prefix it with ./ &#8592; In this case that means "look in the current directory"

---

### Post by dtmilano on 2008-06-12
> 2) The bash prompt doesn't usually look in your current directory for the commands, so you need to prefix it with ./ &#8592; In this case that means "look in the current directory"

Strictly: PATH, in your shell, doesn't include the current directory (.), that's why you should add it to the command.

---


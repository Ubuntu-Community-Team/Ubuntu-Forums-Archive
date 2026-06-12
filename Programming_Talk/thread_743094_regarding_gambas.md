---
title: "regarding gambas"
date: 2008-04-02
forum: Programming Talk
---

### Post by poposick on 2008-04-02
hello 
im beginner in linux n gambas
i have one program that i create from c and one simple gui that i create with gambas. my purpose is, when i click the button then it will run my program.can i do that/?anyone?

---

### Post by pmasiar on 2008-04-02
Most people recommend Python for beginners, see sticky FAQ why and poll. Gambas is rarely used in Linux.

---

### Post by kalaharix on 2008-04-13
Have you given up trying to get Glade to work with Python yet? :)

Getting your C program to run from Gambas is easy-peasy: just use the shell command!

e.g. 
```
  SHELL "htmldoc --bodyfont Sans --outfile /home/c/Documents/tfc.pdf --webpage /home/c/Documents/tfc.htm" WAIT
  SHELL "lpr /home/c/Documents/tfc.pdf" WAIT 

```

This example converts an HTML file to pdf using the application htmldoc and then prints the pdf using lpr. All from within Gambas.

Gambas rocks:guitar:

---


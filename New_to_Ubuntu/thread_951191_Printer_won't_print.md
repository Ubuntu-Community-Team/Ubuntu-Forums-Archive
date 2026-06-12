---
title: "Printer won't print"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by Haruki-kun on 2008-10-17
I have an Epson Stylus C92. As is the usual procedure, I just plugged it in until the system told me it was installed and ready to use. Unfortunately, I send something to print and all the printer does is take push out blank papers.

The Printer in question works when using Windows, so I'm fairly sure it's not broken. Also, I tried using a different printer elsewhere, (A C67) and it worked perfectly well.

What should I do to make this one work? Is there a driver or something I'm missing?

---

### Post by Haruki-kun on 2008-10-18
*poke*

No help at all?

---

### Post by cariboo on 2008-10-18
Have you gone to System-->Administration-->Printing, to make sure your printer is set up properly?

Jim

---

### Post by Haruki-kun on 2008-10-18
OK, I just did, but I managed nothing. I deleted it and reinstalled it, but the result was the same.

I can't help but notice, though, the printer is Epson Stylus C97, but when I installed it, the system installed it using the C88 driver. Could that be the problem?

---

### Post by plucky on 2008-10-18
> I have an Epson Stylus C92.> I can't help but notice, though, the printer is Epson Stylus C97


Which one is it?


If it is a C92,then this is what the [Openprinting database](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_C92) says about it.Could not find C97 in the database.


Good Luck

---

### Post by Haruki-kun on 2008-10-18
It's a C92, sorry, it was a typo.

---

### Post by sneeks on 2008-10-18
is this a duel boot system,but even if it is should not make any difference,when you load the printer in ububtu it will give you some options,as to what to print to,well something like that,try the different options till one works for you.

---

### Post by randreu on 2008-11-12
Hi, I Had the same issue. The problem is that by default, the driver assigned is 'Epson Stylus C88'. Changing it to 'Epson Stylus C79' should do the trick (worked for me).

---


---
title: "Catastrophe! - KNotify Printing Error"
date: 2011-08-07
forum: Programming Talk
---

### Post by etdsbastar on 2011-08-07
Hello Friends,

I am having this unknown error while programming with Gambas, using a webbrowser component to design the printing screen. 

The command** WebBrowser1.Print(True)**

gave a print window successfully. Prints ok when I press Print just after. But, When I try to make the Preview checkbox and then press the print button an awkward error window comes up (screenshot attached).

Same Error Comes directly with the command

The command** WebBrowser1.Print(False)**

Please help

---

### Post by etdsbastar on 2011-08-08
bump... anyone please help

---

### Post by Arndt on 2011-08-08
> **etdsbastar said:**
> Hello Friends,

I am having this unknown error while programming with Gambas, using a webbrowser component to design the printing screen. 

The command** WebBrowser1.Print(True)**

gave a print window successfully. Prints ok when I press Print just after. But, When I try to make the Preview checkbox and then press the print button an awkward error window comes up (screenshot attached).

Same Error Comes directly with the command

The command** WebBrowser1.Print(False)**

Please help

I don't know what Gambas is, but is it perhaps the case that when you print to file (or preview), some special code of yours is meant to be run, whereas it now looks as if you call the ordinary print command with an empty printer name.

---

### Post by etdsbastar on 2011-08-08
Gambas is a VB like programming language under ubuntu. 

**G**ambas **A**lmost **M**eans **Bas**ic

Please help.

---


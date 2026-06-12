---
title: "editing code in Ubuntu Quickly"
date: 2011-06-24
forum: Programming Talk
---

### Post by tubunu on 2011-06-24
Hello,

I would like to ask for some guidance to point me in the right direction to do more research. I'm beginning with simple GUI design in Quickly and while I already know how to create a window with simple buttons in Python and GTK, I feel I'm at a loss when it comes to editing the files in Quickly. 

Q1
Do I need to leave the Quickly files intact (and only add my code on top of it) or can I delete them altogether and add what I need there? I must say browsing through that code in Quickly files is more confusing than actually writing my own from scratch, but if I do that, will my GUI in glade be preserved?

Q2
Is there a possibility to enable the source code for the buttons, combos, etc that I add to show up in Quickly files so that I can link them to functions in Python? Or do I need to "add" them again in the code that I write?

Sorry for such basic questions, but I feel I can't make any progress if I don't find the answers. Thanks in advance.

---

### Post by kaspar_silas on 2011-06-24
What exactly is Quickly? Do you have a link?

Is it a IDE or a text editor. I am sort of intrigued but google is not a  great help for something called "Quickly".

---

### Post by Bucky Ball on 2011-06-24
[http://www.google.com.au/#hl=en&q=quickly+programming&oq=quickly+programming&aq=f&aqi=g-v1&aql=undefined&gs_sm=e&gs_upl=27926l29461l0l11l10l0l6l6l0l295l670l1.1.2l4&bav=on.2,or.r_gc.r_pw.&fp=e32681dc5aaedc19&biw=1366&bih=596](http://www.google.com.au/#hl=en&q=quickly+programming&oq=quickly+programming&aq=f&aqi=g-v1&aql=undefined&gs_sm=e&gs_upl=27926l29461l0l11l10l0l6l6l0l295l670l1.1.2l4&bav=on.2,or.r_gc.r_pw.&fp=e32681dc5aaedc19&biw=1366&bih=596)

Just be specific with your googling, first link says it all ... ;)

---

### Post by tubunu on 2011-06-24
Sorry, I didn't include a link to [Quickly]("https://wiki.ubuntu.com/Quickly"). It's an application that helps to develop Ubuntu applications fast or "quickly". But I'm stuck with my questions in the first post... ;) Thanks all.

---

### Post by tubunu on 2011-06-26
I've just found out while doing my research that Ubuntu Quickly version 11.04 (natty) is a much better start than the version I was using on Lucid Lynx, which lacked some features.

---

### Post by kaspar_silas on 2011-07-01
> **Bucky Ball said:**
> [http://www.google.com.au/#hl=en&q=quickly+programming&oq=quickly+programming&aq=f&aqi=g-v1&aql=undefined&gs_sm=e&gs_upl=27926l29461l0l11l10l0l6l6l0l295l670l1.1.2l4&bav=on.2,or.r_gc.r_pw.&fp=e32681dc5aaedc19&biw=1366&bih=596](http://www.google.com.au/#hl=en&q=quickly+programming&oq=quickly+programming&aq=f&aqi=g-v1&aql=undefined&gs_sm=e&gs_upl=27926l29461l0l11l10l0l6l6l0l295l670l1.1.2l4&bav=on.2,or.r_gc.r_pw.&fp=e32681dc5aaedc19&biw=1366&bih=596)

Just be specific with your googling, first link says it all ... ;)

I am, I was just unlucky :-( My history shows I tried:
"quickly ide"
"quickly program"
"quickly gui"
"quickly qt alternative"
"quickly ubuntu code"
then I got bored. "Quickly" by itself would have worked as it turns out.

Looks interesting. Sorry can't help OP. Still at least you got a bump.

---

### Post by oedipuss on 2011-07-01
Q1 : You can modify and/or delete some quickly generated files that you don't need. For instance, if you don't need an 'about' dialog, you can delete the .py and ui files for it, and of course remove any imports in other files or interfaces so they don't look for it. I don't know if it's frowned upon but it works :P
It's best not to edit some parts the main file, but I believe that is documented in comments.

Q2 : glade won't export as code. (or maybe it will but not usable with quickly, I'm not sure). You just create what makes sense in glade, and assign function names to signals from there too ( there's a signals tab ). Then you create functions with the same name as the name you entered in glade, with appropriate parameters, and it will automatically connect. 
If you want to code some gtk stuff manually, you can create a container (a hbox or whatever, even the main window might do) in glade, then get it inside your code and add stuff to it. There are some examples of getting widgets by name in the main quickly file, look for self.builder.get_object('objectname') .
Similarly you can connect signals to functions manually by getting the widget.

---


---
title: "Print sees all the network printers"
date: 2014-05-27
forum: New to Ubuntu
---

### Post by PABlanche on 2014-05-27
Hi,

I have 2 network printers installed via "printers - localhost", but when I select "print" in several softwares (not all of them), it displays nearly all the network printers in the building (more than 20).

This happens with document viewer, firefox, thunderbird,...

This does not happen with LibreOffice.

I am currently using Ubuntu 14.04 but this was like this way before.

I don't even know where to start with this. Any help welcome.

Thanks,
-- 
Pierre

---

### Post by deadflowr on 2014-05-27
Open "Printers" and right click on one of your printers and select set as default.

---

### Post by PABlanche on 2014-05-27
I sure did have a default printer. But why do I have to see the 20+ printers that are not installed? It is a pain each time I have to select another one (names are not obvious).

---

### Post by deadflowr on 2014-05-27
Why are selecting anything if you have a default printer?
Just hit print in the printer dialog box.

Edit: perhaps you have setting somewhere that allows you to see the other printers.
Shouldn't be much of a problem though, as long as you have one set as default.

Are all the other printers the same type/model or something?

---

### Post by PABlanche on 2014-05-28
It is more annoying than a problem, I have 10 laserjets, 5 colorprinters, and 5 names such as NPIF75NBD ???

Trangely enough, I do not see all the printers (there are probably more than 50)

I would like to find that setting that allows to see these other printers and unselect it.

---

### Post by deadflowr on 2014-05-28
Perhaps look at the cups interface
```
localhost:631
```
input the above into any browser's url.

I'm sure something in there will give you a clue.

---

### Post by PABlanche on 2014-05-28
Screen capture of the problem in attachment:
3 printers installed
50+ printers on the network
20 printers available when printing from software.

localhost:631 give me access to the 3 printers installed. I didn't see any obvious option.

---


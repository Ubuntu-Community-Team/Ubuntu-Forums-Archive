---
title: "Is there any problem if I install two mathematical packages in ubuntu?"
date: 2014-03-21
forum: New to Ubuntu
---

### Post by arroy_0209 on 2014-03-21
Perhaps a stupid question, but I need to make sure that there will not be any problem if I install two different open source mathematical softwares in ubuntu 12.04. It is known that in windows, one can not have two antiviruses active at the same time. Is there any need to check compatibility of the two packages in case I run both simultaneously (a remote possibility though)?

---

### Post by grahammechanical on 2014-03-21
Does mathematical software work in a similar fashion to anti-virus software? Or do they work more like spreadsheets and word processing and accounting software?

Personally, I would not worry about running two spreadsheet programs at the same time. Or two word processor programs at the same time. I have even run two web browsers at the same time. Why would there be problem?

---

### Post by bapoumba on 2014-03-21
Could you please state which math applications you are talking about ?

---

### Post by arroy_0209 on 2014-03-22
I have sagemath (old version 4.8) installed and planning to install maxima in ubuntu12.04.

---

### Post by bapoumba on 2014-03-22
I've had a look at both their FAQ, but I am not a specialist :)
They both have mailing lists, I think the best thing to do is ask them directly.

---

### Post by sotiris2 on 2014-03-22
One needs to consider that anti-virus programs in windows need to act in ways that a virus/rootkit would (aka power-grab), so an anti-virus program will think the newer one is a virus and try to deny it access (and vice-versa). 

Now in regards to mathematical packages I doubt they have either the means to detect other mathematical programs or the privileged status AV have to interfere, especially in Linux. So I don't think you 'll have any problem except maybe if they have conflicting dependencies (one needing lib package v4+ and the other only older than v4) but then you wouldn't even be able to install them.

---

### Post by bapoumba on 2014-03-22
^ is sort of what I was thinking. I was even willing to install both of them and see, but looks like maxima has to be compiled from sources. Not much time this WE..

---

### Post by Impavidus on 2014-03-22
When one of the programs is a fork of the other (like libreoffice/openoffice) or such kind of relation, there is the possibility that both use the same paths and filenames for incompatible files (settings, libraries). Otherwise this is very unlikely.

---


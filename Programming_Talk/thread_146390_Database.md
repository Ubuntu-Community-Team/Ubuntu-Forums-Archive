---
title: "Database"
date: 2006-03-18
forum: Programming Talk
---

### Post by Jimmy_r on 2006-03-18
I'm thinking about writing a program for handling sales/cash registers/orders etc. I will probably write it in python and/or C++.
Can anyone point me to a good database for handling the product data(Barcodes/names/prices/stock etc)?

Also, i will probably use qt for the gui(for C++ and a good IDE/GUI builder). Any input on this?
Although the software will be licensed under the GPL, if i manage to get it working quite good, there might be some small local companies willing to buy it(in fact it will be eventual modifications/adaptions/installations/support they will actually be paying for as the software will be open source). 
As I understand it, the open source version of qt4 allows me to sell software made with it(without paying trolltech), both to X11, mac and windows users, as long as the software is open source. Is that correct?

---

### Post by thumper on 2006-03-19
The good thing about PostgreSQL is its licence - you can pretty much do what you want with respect to selling a product that uses it.  

It also (apparently) has C++ classes for talking to it.

---

### Post by LordHunter317 on 2006-03-19
If the application is meant to be freestanding, Firebird or SQllite are embedded.  The former likely being preferred over the latter at least from a DB POV.

---

### Post by Jimmy_r on 2006-03-20
Thanks for the suggestions. Now the only question is if i will ever muster up enough courage to get this started... Oh, well, even if it turns out crap, it will at least give some experience... :D

---

### Post by mlind on 2006-03-20
I'd go for postgreSQL too. You should check HypersonicSQL too, it's what OpenOffice
uses as its backend. HypersonicSQL offers useful in-memory database too, which
is useful for testing environment.

---


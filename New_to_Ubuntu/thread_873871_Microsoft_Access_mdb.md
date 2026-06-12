---
title: "Microsoft Access mdb"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by sno&#623;&#654;uou&#592; on 2008-07-29
Hi,

I need to open a Microsoft Access database file on ubuntu.

it is .mdb format but OOo does not recognize it and google.com/linux has no info.

Any help as this is for an assignment that I need to pass my college course :S

---

### Post by ace007 on 2008-07-29
Your google skills need work, first result I got...

[http://mdbtools.sourceforge.net/](http://mdbtools.sourceforge.net/)

---

### Post by sno&#623;&#654;uou&#592; on 2008-07-29
URL of the google search?

And thanks!

---

### Post by SunnyRabbiera on 2008-07-29
Also there are other tools, like installing libmdbodbc in the repositories.

---

### Post by sno&#623;&#654;uou&#592; on 2008-07-29
> **SunnyRabbiera said:**
> Also there are other tools, like installing libmdbodbc in the repositories.

I installed that how do I use it? Is it an add-on to openoffice.org?

---

### Post by SunnyRabbiera on 2008-07-29
that part I am unsure of, but experiment and install more packages related to the .mdb format.
I dont use that format myself so I cant give much advice.

---

### Post by OffAxis on 2008-07-29
If you're just after the data tables you can convert them to a mysql database using mysql tools.
[http://dev.mysql.com/downloads/gui-tools/5.0.html](http://dev.mysql.com/downloads/gui-tools/5.0.html)

---

### Post by sno&#623;&#654;uou&#592; on 2008-07-29
No, I need to edit the access database in openoffice.org base

Made the database at college, I go on holiday with my Laptop and ubuntu, get feedback and changes needed to do on the assignments, try to load it up and...

Oh shi-

So I really need this lol.

---

### Post by LowSky on 2008-07-29
Odd that no one thought to look on OO.org site I found on Google
[http://www.google.com/search?hl=en&q=open+Access+openoffice&start=10&sa=N](http://www.google.com/search?hl=en&q=open+Access+openoffice&start=10&sa=N)

heres the patch from Sun, its still in beta
[http://dba.openoffice.org/drivers/mdb/index.html](http://dba.openoffice.org/drivers/mdb/index.html)
OO.o3 will come with Access support built in
[http://download.openoffice.org/680/?intcmp=1461](http://download.openoffice.org/680/?intcmp=1461)

---

### Post by SunnyRabbiera on 2008-07-29
If you need to you can try the open office beta's out in wine (as I wouldnt install it the normal way in ubuntu)

---

### Post by Yannick Le Saint kyncani on 2008-07-29
Hi sno&#623;&#654;uou&#592;, if you install openoffice.org, it will pull it openoffice.org-base, the database component for openoffice.org.

Now if you search through synaptic for office and mdb, you will be given a result for openoffice.org-base, which in its description suggests installing mdbtools.

Hope it helps.

---

### Post by Vorian Grey on 2008-07-29
I just run Access 2003 in XP through VirtualBox. I know, I'm lazy. Plus, Base is lacking a lot of tools. A lot of advanced functions were missing the last time I tried it out.

---


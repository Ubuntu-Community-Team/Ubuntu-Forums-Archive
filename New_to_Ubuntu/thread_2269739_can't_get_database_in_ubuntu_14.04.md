---
title: "can't get database in ubuntu 14.04"
date: 2015-03-17
forum: New to Ubuntu
---

### Post by jaxom98 on 2015-03-17
Dell inspiron n5110. Hdd upgraded to 1Tb, rest is factory.
OS win7/ ubuntu 14.04.1 ,new installation
skill level: beginner
I tried to open my database template, and the database would not work at all.
I am using the default office package that comes with 14.04
I am calling up office,libre office,which brings up a window offering "openfile" , "templates" and "create"
under "create " are: Writer document,Calc spreadsheet,Impress presentation, Draw drawing, Math formula , Base database.
writer , calc , impress , draw , and math all work,ie they bring up a window of the relevant template. 
Base, however does not respond.Single click or double click, makes no difference, base database will not go to the database template window. What is going wrong, is there a broken file ,a dummy entry , or what???

---

### Post by steeldriver on 2015-03-17
I think the libreoffice-base component is not installed by default - you can install it via the Software Center, or from the command line using 

```

sudo apt-get install libreoffice-base

```

---

### Post by newb85 on 2015-03-17
steeldriver is correct.  Most of libreoffice is installed by default, but Base is not.  You can install from the command line, as steeldriver instructed, or you can find it in the Software Center and install from there.  The result is identical.

---

### Post by jaxom98 on 2015-03-19
Hello steeldriver , I used the software centre to download the database program last night. It worked text book perfect.  
thank you for your help.

---


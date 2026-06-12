---
title: "how to edit files"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by karaju on 2008-04-22
Hello
I am totally new to Ubuntu and I do not know programming.  While configuring network through ethernet card, I was guided to enter some strings of text and numbers in a file.  When I opened Terminal to edit "/etc/network/interfaces", some text file opens.  But unfortunately, I do not know how to edit the file or to be precise, I do not know how to insert text and save the file.  Most of the guides presumes that users are conversent with editing files.  I think a guide on basics would be of great help for persons like me.

Any help?  Thanks in advance.

---

### Post by anaconda on 2008-04-22
You can use eg. gedit for editing those files.. gedit is easy graphical program, and if you can use ANY editor(eg. word, ooffice) you can use gedit.

Just type (in terminal)
```
sudo gedit /etc/network/interfaces
```

eg. vi or nano can both be quite difficult editors for new users..

---

### Post by Humph on 2008-04-22
Open a terminal window (Applications -> Accessories -> Terminal)

Then type:

sudo gedit /etc/network/interfaces

You will then be able to edit the file pretty much like Notepad in Windows using the arrow keys, etc.

When you're finished click "Save" and you're done.

EDIT: Bah! beaten to it!

---

### Post by Iowan on 2008-04-22
**gksudo** might work better for **gedit**.
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by billgoldberg on 2008-04-22
> **Iowan said:**
> **gksudo** might work better for **gedit**.
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

It's true that gksudo is preferred to sudo for graphical apps but in this case (with gedit) it doesn't make any difference (talking from experience).

---

### Post by arguellodw on 2008-04-22
I might also add (from experience) that when editing configuration files, be sure to create a backup copy first.  =)

---

### Post by Oldsoldier2003 on 2008-04-22
> **billgoldberg said:**
> It's true that gksudo is preferred to sudo for graphical apps but in this case (with gedit) it doesn't make any difference (talking from experience).

Ever try sudoedit? It is a "recommended" practice (in the man pages) for editing of configuration files, but OMG its a mess... unless of course you are a Vi fan in which case its just another way to get the same result.

---


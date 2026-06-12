---
title: "Can't Find MySQL after downloading"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by JacquesPotter on 2011-10-29
I've donwloaded MySQL to my computer and now I can't find it to use it. I have no idea where to start. I would like to be able to create a desktop icon for it once I find it so I don't have to go crazy looking for it each time. Can anyone help???? I'm use to using MS Access. Am I on a dream thinking that I will be using a similar product and that I will be able to transfer over the database that I have in Access? Please help.

---

### Post by garyed on 2011-10-29
If its installed & you set a password when you installed it you could open up a terminal & try:
```

mysql -u root -p

```
It should ask you for a password if its installed.
You may need to substitute your 'username' for 'root'.

---

### Post by aura7 on 2011-10-29
Try mysql --help 

if it is install it should show you a list of commands that you can use with it.

---

### Post by alco75 on 2011-10-29
If you want to create your own shortcut and need to know where it's actually installed, try running **which mysql** in a terminal, which should give you the path.

I install LAMP (Linux, Apache, MySQL, PHP) with **sudo tasksel install lamp-server** and MySQL on Oneiric is in **/usr/bin/mysql**.

MySQL database dumps are plaintext files with a .sql extension that use SQL syntax to create tables and insert data. I don't know about MS Access, but it's not very likely that you'd be able to import an MS Access database straight into MySQL without going through some conversion process beforehand, I wouldn't have thought.

---

### Post by JacquesPotter on 2011-10-29
OK, these all did something but not quite what I'm looking for. Isn't there a GUI that I can use to create databases with similar to MS Access? I've been told by a friend that I can just import the data from MS Access straight to MySQL. All I need is the data from my MS Access database that I can then put into OpenOffice Spreadsheet. So, I guess what I'm asking is: How do I access the GUI for MySQL and create an icon on my desktop to use it? Please remember I am not that familiar with using the code in terminals.

---

### Post by Miljet on 2011-10-29
I'm guessing that what you are looking for is something like OpenOffice.org.dadabase, or if you are running 11.10, libreoffice.database.

---

### Post by JacquesPotter on 2011-10-29
> **Miljet said:**
> I'm guessing that what you are looking for is something like OpenOffice.org.dadabase, or if you are running 11.10, libreoffice.database.

That sounds like it might work. Where do I find it and download it?

---

### Post by wojox on 2011-10-29
Look in Software Center for base.

---


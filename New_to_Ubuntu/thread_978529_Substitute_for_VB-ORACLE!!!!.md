---
title: "Substitute for VB-ORACLE!!!!"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by bobigeorge on 2008-11-11
Hello friends..

I am looking for a good substitute for VB-ORACLE in Ubuntu. Pls suggest me some alternatives.

Thanks in advance.

---

### Post by Tony Flury on 2008-11-11
Try Python and mysql 

Bear in mind that VB is very MS specific and you will need to relearn how do to windows, buttons and Python is not VB.

what ever combination you eventually choose it will have a learning curve - some steeper than others.

---

### Post by bobigeorge on 2008-11-11
Thank you Tony..

Can you lead me to a tutorial or paper showing how to install and basic tutorial. I like to learn new languages...

---

### Post by Tony Flury on 2008-11-11
You will probably find that Python is already installed - try the command "python" from the terminal.

Tutorials 

For Python : 

[http://www.google.co.uk/search?hl=en&q=Python+Tutorial&meta=](http://www.google.co.uk/search?hl=en&q=Python+Tutorial&meta=)

take your pick of tutorials :-) but I am using 

[http://docs.python.org/tutorial/](http://docs.python.org/tutorial/) as my main source.

As for mysql : 

[http://www.devshed.com/c/a/Python/Database-Programming-in-Python-Accessing-MySQL/](http://www.devshed.com/c/a/Python/Database-Programming-in-Python-Accessing-MySQL/)

You also want to look at Guis SDKs etc (they don't come native to Linux) 

The main two (as far as I can tell are : 

Tkinter (uses TCL) - [http://www.pythonware.com/library/tkinter/introduction/](http://www.pythonware.com/library/tkinter/introduction/)

and

pyGTK (uses GTK+) -  [http://www.pygtk.org/](http://www.pygtk.org/)


Also look at the Sticky posts in the Programming Talk forum which has a lot of links to tutorials.

---

### Post by AnimalMagic on 2008-11-11
Mono has a VB compiler 
[http://monodevelop.com](http://monodevelop.com)

---

### Post by directhex on 2008-11-11
Yeah... vbnc and System.Data.OracleClient.dll, both in the repos..... If you're good, your code might already run unmodified via Mono. Or at least the porting effort would be minimal. You could learn to replace your code one component at a time rather than doing it all in one go.

---


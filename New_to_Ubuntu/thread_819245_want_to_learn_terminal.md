---
title: "want to learn terminal"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by gurkhali69 on 2008-06-05
Hi everyone!!
Im NSS Grg,an engineering student. I have been following using Ubuntu for a year n using it regularly since a couple of months. To use do all the works in Ubuntu its not dat easy without knowing to use terminal. So I was wondering could learn Ubuntu terminal from this forum. Thank you

---

### Post by Bodsda on 2008-06-05
we could point you to every man page under the sun. but maybe it would help if you told us what you need to do and we'll tell you how to do it

;~)

---

### Post by kpkeerthi on 2008-06-05
[http://www.linuxcommand.org](http://www.linuxcommand.org)

---

### Post by Bodsda on 2008-06-05
These may be usefull aswell

[http://bash-hackers.org/wiki/doku.php]("http://bash-hackers.org/wiki/doku.php")

[http://wooledge.org:8000/BashGuide]("http://wooledge.org:8000/BashGuide")

IRC (Xchat is a popular client)

server = irc.freenode.net 
channel #bash

---

### Post by didac on 2008-06-05
Do you want to learn terminal itself? Do in a terminal:

```
man xterm | col -b > ~/Desktop/TerminalManual
```

Or do you want to do what you can type in a terminal? Any program installed in any directory called bin or sbin, which is in your path, like /bin /sbin /usr/bin /usr/sbin /usr/local/bin etc.

If you don't remember the full name, type the first letters and give a tab for autocompletion. If you have used that command before, type 

```
!fs
```

and ENTER and the bash history will give you the last instance. If you don't know the switches for that program, type 

```
whatevertheprogramiscalled --help 
```

or type 

```
man whatevertheprogramiscalled
```

or 

```
info whatevertheprogramiscalled 
```

to get the manual for that program.

Is that what you need?

---

### Post by ptempel on 2008-06-05
My favorite book on shell scripting is "Unix Shell Programming" by Kochan and Wood:

[http://www.amazon.com/Unix-Shell-Programming-Stephen-Kochan/dp/0672324903/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1212667099&sr=8-1](http://www.amazon.com/Unix-Shell-Programming-Stephen-Kochan/dp/0672324903/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1212667099&sr=8-1)

You can use this on any Unix derivative (not just Ubuntu).  Recently bought the sed & awk book from O'Reilly:

[http://www.amazon.com/sed-awk-2nd-Dale-Dougherty/dp/B00007FYIJ/ref=sr_1_1?ie=UTF8&s=books&qid=1212667524&sr=1-1](http://www.amazon.com/sed-awk-2nd-Dale-Dougherty/dp/B00007FYIJ/ref=sr_1_1?ie=UTF8&s=books&qid=1212667524&sr=1-1)

to round out the library.  It also can't hurt to have a book on the vi editor:

[http://www.amazon.com/Learning-Editor-6th-Arnold-Robbins/dp/1565924266/ref=sr_1_1?ie=UTF8&s=books&qid=1212667592&sr=1-1](http://www.amazon.com/Learning-Editor-6th-Arnold-Robbins/dp/1565924266/ref=sr_1_1?ie=UTF8&s=books&qid=1212667592&sr=1-1)

since its a good editor and is on every Unix box in some form or another.  There are sites with vi cheat sheets.  Just do a search for it.  If you like emacs, then there should be tons of materials for it as well.

---

### Post by powerpleb on 2008-06-05
> **gurkhali69 said:**
> Hi everyone!!
Im NSS Grg,an engineering student. I have been following using Ubuntu for a year n using it regularly since a couple of months. To use do all the works in Ubuntu its not dat easy without knowing to use terminal. So I was wondering could learn Ubuntu terminal from this forum. Thank you

This is what I did: 
[http://www.linux.org/lessons/](http://www.linux.org/lessons/)

---

### Post by dracayr on 2008-06-05
> **ptempel said:**
> My favorite book on shell scripting is "Unix Shell Programming" by Kochan and Wood:

[http://www.amazon.com/Unix-Shell-Programming-Stephen-Kochan/dp/0672324903/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1212667099&sr=8-1](http://www.amazon.com/Unix-Shell-Programming-Stephen-Kochan/dp/0672324903/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1212667099&sr=8-1)

You can use this on any Unix derivative (not just Ubuntu).  Recently bought the sed & awk book from O'Reilly:

[http://www.amazon.com/sed-awk-2nd-Dale-Dougherty/dp/B00007FYIJ/ref=sr_1_1?ie=UTF8&s=books&qid=1212667524&sr=1-1](http://www.amazon.com/sed-awk-2nd-Dale-Dougherty/dp/B00007FYIJ/ref=sr_1_1?ie=UTF8&s=books&qid=1212667524&sr=1-1)

to round out the library.  It also can't hurt to have a book on the vi editor:

[http://www.amazon.com/Learning-Editor-6th-Arnold-Robbins/dp/1565924266/ref=sr_1_1?ie=UTF8&s=books&qid=1212667592&sr=1-1](http://www.amazon.com/Learning-Editor-6th-Arnold-Robbins/dp/1565924266/ref=sr_1_1?ie=UTF8&s=books&qid=1212667592&sr=1-1)

since its a good editor and is on every Unix box in some form or another.  There are sites with vi cheat sheets.  Just do a search for it.  If you like emacs, then there should be tons of materials for it as well.

I agree. Books are the best way to learn how to use the shell

dracayr

---

### Post by Duck2006 on 2008-06-05
Another good book is Linux Cookbook

---

### Post by 7raTEYdCql on 2008-06-05
I found this good link about the terminal.
It will surely be helpful to get started with the terminal.
It helped me i am sure it will help you.
[http://www.rgregory.net/linux/how-to.html](http://www.rgregory.net/linux/how-to.html)

---

### Post by pedro_orange on 2008-06-05
I very much recommend this guy here Chris Lasher.

He's made a good few videos here (All about 8-10 mins long each) about really simple BASH tasks like copying/processes/adding/deleting.

REALLY worth the time to watch it if you're new to the Bourne again shell!
[http://showmedo.com/videos/series?name=pQZLHo5Df](http://showmedo.com/videos/series?name=pQZLHo5Df)

---

### Post by mm3gss on 2008-06-05
Once you get the hang of the terminal the skys the limit!

Best thing you can do though is become competent with the basics i.e. *cp* and *mv* etc then just keep breaking things. The better you break something the more you learn trying to fix it! :p

---


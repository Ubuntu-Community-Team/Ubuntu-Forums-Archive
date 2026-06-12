---
title: "Where is installed application?"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by Arphahat on 2008-06-08
I wanted to see if an app that I have been using in Windows was available, and it seems that it is.  I was going to download and install FreeMind, but it discovered that it was already registered in the Package Manager.  So, I marked it as "to be installed" and clicked apply.  It appeared to install.

So, where is it?  It isn't under applications, and I even rebooted thinking it would show up after that.  If I go to "Add/Remove" under applications, it isn't listed as a choice there, either.  

Any help is appreciated.  

Thanks,
Andy

---

### Post by dmj99 on 2008-06-08
Just sort of guessing here . . . but I've found that some programs don't install a menu item for themselves.  Might try looking in the bin folder for its main program file.  Also might try synaptic; right click on the program and click the installed files tab.  That will show you the location of all files the program installed.  Should be one called freemind which would start the program.  Hope this helps.

---

### Post by jeffus_il on 2008-06-08
> **Arphahat said:**
> I wanted to see if an app that I have been using in Windows was available, and it seems that it is.  I was going to download and install FreeMind, but it discovered that it was already registered in the Package Manager.  So, I marked it as "to be installed" and clicked apply.  It appeared to install.

So, where is it?  It isn't under applications, and I even rebooted thinking it would show up after that.  If I go to "Add/Remove" under applications, it isn't listed as a choice there, either.  

Any help is appreciated.  

Thanks,
Andy
Open a terminal and type the program name at the command prompt (normally in lower case)
You can also type```
 which <programname>
```
to find out where the program is located

---

### Post by Arphahat on 2008-06-08
Thanks!  That runs the program.

Is there a way to get the program to appear in the applications list?  It is inconvenient to have to run it via the terminal.

Thanks,
Andy

---

### Post by Fedz on 2008-06-08
It's rare it happens but, when it does I found going to Ubuntu > Applications > Add and Remove puts it there ;-)

On a secondary note however I have seen once it put in system > preferences.

---

### Post by ism. on 2008-06-08
> **Fedz said:**
> It's rare it happens but, when it does I found going to Ubuntu > Applications > Add and Remove puts it there ;-)

On a secondary note however I have seen once it put in system > preferences.

more specifically, system>preferences>main menu> then click the new item tab and enter in the name the terminal command and your other needs

-ism.

---


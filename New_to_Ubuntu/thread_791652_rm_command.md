---
title: "rm command"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by abraxas334 on 2008-05-12
This has probably been asked many times before but i can't seem to find the answer.
When using the rm command how do u always get a promt whether u want to remove something or not rather than having to put rm -f everytime.
Did one of these stupid wildcard things and lost a lot of Data :(, i guess it had to happen at some point!

Thanks for all the help!

---

### Post by Virtual_Ron on 2008-05-12
rm -i  will make it interactive.  Is that what your asking?

---

### Post by Monicker on 2008-05-12
Put this line at the bottom of either /etc/bash.bashrc or in /home/username/.bashrc
```

alias rm='rm -i'
```

Log out and log back in.

That will cause you to get prompted when removing files, even if you use a wildcard.  If you specifically use -f though, you still will not get prompted.

/etc/bash.bashrc is system wide, and /home/username/.bashrc is obviously user specific.

---

### Post by alzie on 2008-05-12
the rm MAN page is at [http://www.ss64.com/bash/rm.html](http://www.ss64.com/bash/rm.html)

It sounds like you are looking for rm -i to prompt you before removal.

Check the link for more.  I hope this helps you

---

### Post by Oldsoldier2003 on 2008-05-12
ack! yes aliasing rm to rm -i would do the trick but would drive me insane in a matter of an hour or less :)

---

### Post by Monicker on 2008-05-12
> **Oldsoldier2003 said:**
> ack! yes aliasing rm to rm -i would do the trick but would drive me insane in a matter of an hour or less :)

It would bug me too.  One down side to aliases is that you may forget a command is actually an alias, which could lead to unexpected problems if you go to work on a system which does not have the aliases which you set up.


EDIT:  The more I think it about it, the OP should probably just get in the habit of manually specifying -i.

---

### Post by scorp123 on 2008-05-12
rm -i    ... "i" as in "interactive". Also you could easily find out yourself by looking at the manual ;)
```
man rm
```

---

### Post by scorp123 on 2008-05-12
> **alzie said:**
> the rm MAN page is at [http://www.ss64.com/bash/rm.html](http://www.ss64.com/bash/rm.html) What do you need that web link for? Just open a terminal and read the manual on your local system ;) ```
man rm
```

---


---
title: "Recent Documents in Ubuntu?"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by faraz_k86 on 2008-11-19
I know that I have worked on a .odt file today in open office and im sure that I have saved it but I dont know where??

In windows we had this recent documents list that kept the list of 10 most recent files opened.

Any idea how i can accomplish this in ubuntu?

thankx

---

### Post by perlluver on 2008-11-19
Click on Places, then you can find recent documents down at the bottom of that list.

---

### Post by mjwhitfield on 2008-11-19
Places -> Recent Documents (bottom of the menu)

---

### Post by rampageoberon on 2008-11-19
in terminal do the following

```
find ~/ -atime -1 | grep -i "odt"
```

Hope that helps.

If you know the name of the file do

```
sudo updatedb
locate <file>
```

---

### Post by faraz_k86 on 2008-11-19
Thanks guys.

but would some one please explain what this command means, like atime?? and -1?? and what is grep?? and why not -2 instead of -1.??
> find ~/ -atime -1 | grep -i "odt"

Thanks

---

### Post by rampageoberon on 2008-11-19
Okay the -atime means check for access times. and the -1 means less than 1 day ago, you can off course use -2 for less than 2 days ago.

So -atime -1 means accessed less than 1 day ago. Now grep prints lines matching a pattern.

Check the manual page for a more comprehensive explanation

```
man find
man grep
```

hope that helps

---


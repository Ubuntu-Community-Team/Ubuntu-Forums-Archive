---
title: "edit file"
date: 2012-03-02
forum: New to Ubuntu
---

### Post by bilboubu on 2012-03-02
If I have a file called hello.tbl 
which contains text:

"123456#  789"


how could I delete the 789 using the cat command?

---

### Post by winh8r on 2012-03-02
You wouldn't. 
You would just run:

```
gedit hello.tbl
```

edit the file to what you want and then click on save.

---

### Post by papibe on 2012-03-02
> **winh8r said:**
> You wouldn't.
+1

But if your concern is to delete the pattern using command line tools, there are a few options.

Easy: use a command line editor like nano or vi. For example:
```
nano hello.tbl
```
If you are looking for other command line tools, you can use 'sed':
```
sed 's/789//g' hello.tbl > newhello.tbl
```
Note that the latter removes all occurrences of the pattern '789', but does not modify hello.tbl. Instead, it creates a new file (newhello.tbl).

Hope that helps, and tell us if you need more tips.
Regards.

---


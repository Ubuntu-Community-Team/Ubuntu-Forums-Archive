---
title: "how do a launch a local file?"
date: 2012-07-23
forum: New to Ubuntu
---

### Post by degarb on 2012-07-23
I am in so and so directory and want to execute a file in that dir in terminal.  As I recall, I cannot type that program name, rather need path to program.

Else is it ./programname  ?

I cannot think how to word a search,

---

### Post by Grenage on 2012-07-23
> **degarb said:**
> Else is it ./programname

Bingo.  If it's not working, make sure it's executable:

```
chmod +x *filename*
```

---

### Post by codemaniac on 2012-07-23
> **degarb said:**
> I am in so and so directory and want to execute a file in that dir in terminal.  As I recall, I cannot type that program name, rather need path to program.

Else is it ./programname  ?

I cannot think how to word a search,

If  you are not sure about the location of the file you want to execute , just do a find .

```
find */path/to/look/for* -name "*file_name*" -print
```

---

### Post by yuvraj23 on 2012-07-23
Simple way : Right click on the file,go to properties, click on permissions tab and check 'mark this file as executable'.. click on apply to save your changes.. now click on file and select 'execute' to execute it..

---


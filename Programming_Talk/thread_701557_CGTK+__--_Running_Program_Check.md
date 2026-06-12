---
title: "C/GTK+  -- Running Program Check"
date: 2008-02-19
forum: Programming Talk
---

### Post by Naveen Chandran on 2008-02-19
In GTK+ How do I check if a particular program is running or not? If Not then start the program...

How do I do it? :confused:

---

### Post by pedro_orange on 2008-02-19
I wouldn't know how to do it directly from the code in linux. In windows you can check a string against a list of running applications which is stored in an object. I'm sure there must be a similar solution.

You could do a long work-around that ran the ps -C "appname" shell command and see if it returned any information. 

```
string = system("ps -C appname")
```

I'm sure there would be a better method though.

---


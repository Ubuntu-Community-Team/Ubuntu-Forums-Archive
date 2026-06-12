---
title: "[SOLVED] Chain input in Python"
date: 2008-09-19
forum: Programming Talk
---

### Post by davidcaiazzo on 2008-09-19
I know in python that a input ends with a new line(when the user hits enter). I was wondering if it is possible chain inputs like c++ does. For example:
```

//c++
string first, last;
cout<<"What is your name(first and last)?";
cin>>first>>last;

```

In python however I have to do this:
```

#Python
print "What is your first name?"
first=raw_input()
print "What is your last name?"
last=raw_input()

```

Is there anyway to chain input?

---

### Post by pmasiar on 2008-09-19
```

#Python
first, last = raw_input("What is your first and last name?").split()

```
 8-)

---

### Post by davidcaiazzo on 2008-09-19
Thank you!

---


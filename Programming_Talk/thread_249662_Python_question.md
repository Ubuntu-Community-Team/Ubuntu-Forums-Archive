---
title: "Python question"
date: 2006-09-02
forum: Programming Talk
---

### Post by Somenoob on 2006-09-02
Is there any sort of python class/library that can write programs that can be runed with web browsers?

---

### Post by Note360 on 2006-09-02
I think you are looking for one of the many web api's for python.


You can choose from:
zope
psycho
django
twisted 
and many others

---

### Post by Somenoob on 2006-09-02
> **Note360 said:**
> I think you are looking for one of the many web api's for python.


You can choose from:
zope
psycho
django
twisted 
and many others

Is there any native type that ships with python? if so, is it supported by the most popular web browsers(IE, Firefox, Opera)?

---

### Post by ynef on 2006-09-03
You're really asking the wrong kind of question -- applications that run on the server don't care what browser the user happens to use to view the result.

To make a native CGI program, all you really need to do is set up the web server software to allow you to use Python. Once this is done, you can simply follow the steps in a suitable tutorial such as this: [http://www.cs.virginia.edu/~lab2q/](http://www.cs.virginia.edu/~lab2q/)

---


---
title: "python import problem (different versions of python)?"
date: 2007-05-13
forum: Programming Talk
---

### Post by gatoruss on 2007-05-13
I have a (hopefully not) dumb question...

I have been playing around with python.  I wrote a script that sends an smtp email. 

Here is the link that I found explaining how such a script could be written [http://www.thinkspot.net/sheila/article.php?story=20040822174141155](http://www.thinkspot.net/sheila/article.php?story=20040822174141155)

As you see it imports a module as follows:  "import smtplib".

From the terminal, it works fine.  I then played around with tkinter, and I got it to work from a GUI as well.

However,  I then tried playing around with wxpython and  when I try to send the email thru the wxpython created GUI, I get an error message telling me that usr/lib/python2.4/smtplib has some sort of problem. 

I have looked around in my /usr/lib directory, and there is an smtplib in a python2.4 directory and one in the python2.5 directory.

Why am I getting this error in wxpython, but not tkinter and the terminal?  Could it be that in the latter cases, the smtplib in python2.5 is being imported, while wxpython is importing the smtplib from python2.4?

---

### Post by JTorres176 on 2007-05-13
Use the hasbang trick, at the top of your file, use this

```

#!/usr/lib/python2.4

```

or whichever version number.

---

### Post by gatoruss on 2007-05-14
tried that.

The Tkiter script works fine if I add 

```
#!/usr/lib/python2.4
```

The wx-python script shows the above erro message is i add

```
[CODE]#!/usr/lib/python2.4
```

and tells me it cannot find module wx if i add

```
[CODE]#!/usr/lib/python2.5
```

Not I had been using the following as the "hash trick statement"

```
[CODE]#!/usr/lib/env python
```

---


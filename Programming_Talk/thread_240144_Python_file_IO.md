---
title: "Python file IO"
date: 2006-08-20
forum: Programming Talk
---

### Post by christhemonkey on 2006-08-20
I am trying to figure out how to do file Input/output,

I have worked through lots of tutorials online, 
and all the ones that mention file IO only mention the basic howto do it:
```
file_open = file("bla.txt")
file_open.write("\n\tbla")
file_open.close()

```
That would open a file (or you can use file_open = open("bla.txt", "w")

And to read one:
```
in_file = open("bla.txt","r")
text = in_file.read()
in_file.close()

```


But, what if i want to open a file and find a specific option, for example,
if i want to find a specific option in a configuration file, and then just alter its value?

Or if i want to open a file and save it with the time+date?

Does anyone have a good example of fileIO in python?


(sorry for the very lengthy post)

Chris.

---

### Post by dabear on 2006-08-20
well, there are many classes builtin to handle config-files like [the ConfigParser](http://docs.python.org/lib/module-ConfigParser.html) module, but you could also just read the whole contents to a string object and use the find method, or even the replace method.

If you wanna rename a file, you could always use something like
```

import time, os

name= 'myfile'

os.rename(name, '%s-%s' %(name, time.time()))



```

---

### Post by christhemonkey on 2006-08-20
Cheers, i shall get back to you if i have any issues :D

---


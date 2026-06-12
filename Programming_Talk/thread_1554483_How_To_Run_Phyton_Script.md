---
title: "How To Run Phyton Script ?"
date: 2010-08-16
forum: Programming Talk
---

### Post by SadisticParadox on 2010-08-16
Hi everyone,Im pretty new to both Ubuntu and Phyton programming. 
Its been 2 days since I started.

I read some tutorials and articles about phyton, so I tried to execute my first phyton script.

The thing is, I write the codes
```
 print " hello world "
```and save it as **file.py**.

How am I supposed to run this script ?

---

### Post by Queue29 on 2010-08-16
By running it through a python interpreter. There's a few ways to do this. You could open up a terminal in the directory of your file.py file and type "python file.py", or you could type it into IDLE, etc.

---

### Post by worksofcraft on 2010-08-17
at command prompt you can type

```

python file.py

```

You can also specify the interpreter in a comment on the first line of script:

```

#!/usr/bin/python
print 'Greetings oh great one, your wish is my command!'

```

don't forget to give execute permission to your script//
```

chmod +x file.py
./file.py

```

Ka pai (Enjoy)

---


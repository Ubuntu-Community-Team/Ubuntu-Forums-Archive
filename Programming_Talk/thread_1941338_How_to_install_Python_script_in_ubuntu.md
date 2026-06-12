---
title: "How to install Python script in ubuntu ?"
date: 2012-03-15
forum: Programming Talk
---

### Post by prismctg on 2012-03-15
I want to install simple "hell0 world" script in ubuntu 11.10 . and i also want to run this python script via terminal , like this 
```
prism@spiral:~$ example 
hello world
```  ....

---

### Post by CynicRus on 2012-03-15
[http://ubuntuforums.org/showthread.php?t=1386221]("http://ubuntuforums.org/showthread.php?t=1386221")

---

### Post by codemaniac on 2012-03-15
```
#!/usr/bin/python

print "Hello World !!"
```
1.put the above codelet in a file hello.py .
2.make it executable .
```
chmod a+x hello.py
```
3.run in a terninal 
```
./hello.py
```

---


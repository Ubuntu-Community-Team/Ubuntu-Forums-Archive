---
title: "geting started with python"
date: 2009-03-25
forum: Programming Talk
---

### Post by shahin on 2009-03-25
Greetings-
    I am just starting with python.  I have a simple program as follows:
sansari@thunder:~/programming/python$ more toggle.py 
#!/usr/bin python
name = raw_input('what is your name?\n')
print 'Hi', name

I have made it executable as you can see ...

@thunder:~/programming/python$ ls -al
total 16
drwxr-xr-x 2   4096 2009-03-25 11:43 .
drwxr-xr-x 3   4096 2009-03-25 11:22 ..
-rwxr--r-- 1     20 2009-03-25 11:21 hello.py
-rwxr--r-- 1     76 2009-03-25 11:42 toggle.py

When I try to run it, I get the following error:

@thunder:~/programming/python$ ./toggle.py 
bash: ./toggle.py: /usr/bin: bad interpreter: Permission denied
@thunder:~/programming/python$ sudo ./toggle.py 
sudo: unable to execute ./toggle.py: Permission denied
@thunder:~/programming/python$

---

### Post by elCabron on 2009-03-25
try

```
#!/usr/bin/python
```

instead of

```
#!/usr/bin python
```

---

### Post by sujoy on 2009-03-25
better yet
```
#!/usr/bin/env python 
```

because you never know where some other distro or user might have python installed ;)

---

### Post by shahin on 2009-03-25
It worked. Thanks
@thunder:~/programming/python$ sudo ./toggle.py 
[sudo] password for : 
what is your name?
Ubuntu Rocks 
Hi Ubuntu Rocks 
@thunder:~/programming/python$

---

### Post by simeon87 on 2009-03-25
> **shahin said:**
> It worked. Thanks
@thunder:~/programming/python$ sudo ./toggle.py 
[sudo] password for : 
what is your name?
Ubuntu Rocks 
Hi Ubuntu Rocks 
@thunder:~/programming/python$

You shouldn't use sudo for this.. it's only needed when the program requires certain permissions (like moving files to certain directories) - this is just a basic program which can run without sudo.

---

### Post by shahin on 2009-03-25
Thanks:-)

---

### Post by stevescripts on 2009-03-25
A quick little ref for linux file permissions:  [http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)

You dont always want to be using sudo to run your scripts ... ;)

Hope you find this useful.

Steve

---

### Post by shahin on 2009-03-26
Thanks.  I'll review it.

---


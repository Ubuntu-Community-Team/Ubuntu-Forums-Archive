---
title: "Python Versions Installed / Environment Path"
date: 2019-03-14
forum: Programming Talk
---

### Post by SBFree on 2019-03-14
Newb questions, thanks for patience. Just starting with Python. My /etc directory has folders called:
[INDENT]python
python2.7
python3
python3.6[/INDENT]
Does this mean I have multiple versions installed? If so, how do I start one over the other?

What do I have to set to get my interpreter to look in a particular directory for my *.py files?
Thanks in advance.
s

---

### Post by freemedia2018 on 2019-03-14
You have Python 2.7 and Python 3.6 installed. Since most people use Python3, You're probably going to use the following as the top line in your Python scripts:

```
#!/usr/bin/env python3
```

If the script is for Python 2:

```
#!/usr/bin/env python2
```

Not sure what you mean when you talk about setting up your interpreter. You can run python, python2 or python3 from the command line to open the interpreter. If you're using IDLE, I haven't used that in a while and don't use it much. It is common for people to have 2 versions of Python installed-- the latest version 2 available and the latest version 3 available.

---

### Post by SBFree on 2019-03-14
Thank freemedia2018!
That helps resolve my questions about versions. What I meant by "setting up your interpreter" was how do I get it to look in the directory where my hello.py file resides? If I start the interpreter with "python hello.py" it tells me the file/directory does not exist. If I explicitly put in the entire path like "python /home/documents/python/hello.py" it runs. Is this a python interpreter setting or Linux environment variable that I have to change to get the interpreter to look in the directory where my file is?
thanks again.
s

---

### Post by freemedia2018 on 2019-03-15
> **SBFree said:**
> If I start the interpreter with "python hello.py" it tells me the file/directory does not exist. 

What you want to do is put that #!/usr/bin/env line i showed you as the top line in hello.py:

```
#!/usr/bin/env python2
print "\x1b[1;33mhello, world!\x1b[m"
```

Then set it to executable from the command line: (or your file manager)

```
chmod 755 hello.py
```

Then copy it to a folder in your path:

```
echo $PATH
```

That will show you the folders in your path.

Alternatively... you could just say:

```
python /path/to/hello.py
```

Where /path/to is the path for the folder that hello.py is in.

---


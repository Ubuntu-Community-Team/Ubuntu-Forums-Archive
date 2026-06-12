---
title: "File I/O Error (Python)"
date: 2009-02-20
forum: Programming Talk
---

### Post by randomd1 on 2009-02-20
Hi. I'm relatively rusty to programming, I took a 2 year hiatus (formerly javascript, php, visual basic, html, css, etc. mostly web based). I only did light programming with python and after about 30 minutes of scraching my head I can't figure out why this won't work.
```

def safe_input (text):
  x = str(raw_input(text))
  return x
file_location = safe_input("File Location?")
file1 = open(file_location,"r+b")

```
Every time I try to run this I get an error that the file or directory does not exist. I know the directory and file exist. Does anyone know how to fix this? Thanks in advance.

---

### Post by snova on 2009-02-20
The snippet itself works just fine.

Some ideas:

1) Does the path you input contain a tilde (~)? Python doesn't expand them, the shell does.

2) Is it a relative path? Keep in mind that the file will be opened from its CWD (Current Working Directory), so if the path doesn't exist *relative to that directory*- it won't work.

Also, safe_input() is redundant- raw_input() returns a string already.

---

### Post by randomd1 on 2009-02-21
Alright, thanks but more problems.
```

import sys, os
print 'sys.argv[0] =', sys.argv[0]
pathname = os.path.dirname(sys.argv[0])
print 'path =', pathname
print 'full path =', os.path.abspath(pathname)
file_location = raw_input("File location?")
x = open(file_location,"rb")
print x.read()
y = open(os.path.abspath(pathname)+"/"+"new","wb")
y.write(x.read())
y.close()
y = open(os.path.abspath(pathname)+"/"+"new","rb")
print y.read()

```
I am in directory /home/user1/pydocs
This code returns the file x's data and will create the file "new"; however, it will not write data to the file. Am I doing something wrong?

---

### Post by WW on 2009-02-21
After executing the command
```

print x.read()

```
the file x is at the end of the file.  When you use x.read() again in
```

y.write(x.read())

```
the second call the x.read() returns an empty string, because x is at the end of the file.  Instead, you could change those lines to something like
```

contents = x.read()   # Save the contents of the file.

```
and
```

y.write(contents)

```

---

### Post by nvteighen on 2009-02-21
> **WW said:**
> After executing the command
```

print x.read()

```
the file x is at the end of the file.  When you use x.read() again in
```

y.write(x.read())

```
the second call the x.read() returns an empty string, because x is at the end of the file.  Instead, you could change those lines to something like
```

contents = x.read()   # Save the contents of the file.

```
and
```

y.write(contents)

```
Or you can rewind using x.seek(0).

---

### Post by TomB19 on 2009-09-03
How can I expand the tilde top open a file relative to the user's home dir?

---

### Post by unutbu on 2009-09-03
[PHP]
import os.path
os.path.expanduser('~')[/PHP]

---

### Post by TomB19 on 2009-09-03
Brilliant!

2 minute response...  lol!

Thank you, unutbu.  :guitar:

---


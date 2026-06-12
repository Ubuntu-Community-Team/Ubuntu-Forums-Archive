---
title: "Interesting Python Problem"
date: 2008-10-11
forum: Programming Talk
---

### Post by cmkrause on 2008-10-11
I am working on a Python Application as part of my science fair project.  Interestingly enough, everything was working fine until suddenly I starting getting the following error:
```
Traceback (most recent call last):
  File "testing with socket.py", line 1, in <module>
    import socket
  File "C:\Python25\lib\socket.py", line 174, in <module>
    Return a new socket object connected to the same system resource."""
  File "C:\Python25\lib\socket.py", line 219, in _socketobject
    self._rbufsize = bufsize
  File "<string>", line 3, in <module>
AttributeError: type object '_socket.socket' has no attribute 'ioctl'

```

The *socket* module is being imported when I am import the *ftplib* module.

I tried an incredibly simple use of the *socket* module (see below) and I get the same error.
```

import socket

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.bind(('modwest.com', 50007))
s.listen(1)
conn, addr = s.accept()
print 'Connected by', addr
while 1:
    data = conn.recv(1024)
    if not data: break
    conn.send(data)
    conn.close() 

```

Also the simple testing simple and my main script work great on my Ubuntu box.  Any ideas of how to fix it in Windows?  I know it is a bit odd, but often times it is more convenient to program in Windows since I have multiple monitors setup and then run the code on my Ubuntu server.

Thank you all for your help,
Chris

PS:  This is my first post.  I have used this site for over a year helping me solve my problems, and now I finally need some more individualized help.  Thanks for this great community and great OS.

---

### Post by slavik on 2008-10-12
an updated version of pyrhon or some such?!

---

### Post by cmkrause on 2008-10-12
> **slavik said:**
> an updated version of pyrhon or some such?!

I was thinking about trying to do something like that, but it was all working fin until that one time when it just stopped working.  Also I looked at the socket.py folder in [python root]/lib/ and the file on my ubuntu server and windows machine are identical.  that is a bit strange that one works and the other doesn't.

---

### Post by slavik on 2008-10-12
I probably should've typed out my entire thought ... maybe the Python socket library was updated or something and the attribute removed? I am not Python expert my any means ... I would try to hit up the Python::socket docs and see if ioctl is listed as deprecated. That is my best guess.

---

### Post by cmkrause on 2008-10-12
> **slavik said:**
> I probably should've typed out my entire thought ... maybe the Python socket library was updated or something and the attribute removed? I am not Python expert my any means ... I would try to hit up the Python::socket docs and see if ioctl is listed as deprecated. That is my best guess.

I haven't been able to find *ioctl* in any documentation.  Even on my linux box, that keyword isn't in the socket.py file.

---

### Post by cmkrause on 2008-10-12
Hey everybody I figured out the problem.  I had named a file socket.py for some reason and it was in the same directory as the scripts I was trying to run.  Once I got rid of that file it works great.  Thanks for the suggestions.

---

### Post by slavik on 2008-10-12
notice the last line of the error you posted, I think that is the cause of your problem (but it doesn't explain why you had errors crop up all of the sudden, unless something changed).

can you try to reboot the box and then try your code again?

I am really shooting in the dark here. Someone with actual Python experience should chime in. :)

---


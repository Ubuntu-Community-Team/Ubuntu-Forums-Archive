---
title: "Problems with Python 2.7 (on bpython)"
date: 2012-07-20
forum: New to Ubuntu
---

### Post by antigoneinvicta on 2012-07-20
I'm trying to write a script in gedit to execute in bpython (the interpreter I downloaded on Ubuntu). From everything I've read, this should be a simple task, but it seems no matter what I do, I can't get anything but an error message. 

- On the first line of my script, I put "#!/usr/bin/python"
- In bpython, I've tried entering the command a dozen different ways, from "(scriptname).py" to  "/home/(myname)/Documents/(scriptname).py" all to no avail
- I've tried using "chmod +x (scriptname).py
- When I do any of the above, I get the following message: 
Traceback (most recent call last):
      File "<input>", line 1, in <module>
NameError: name '(whateverthefirstwordis)' is not defined

Interestingly, I tried going to my /usr/ folder... I can find /usr/bin/, but in /bin/ there's no folder named "python." I tried creating it, but I was denied access permission (even though I'm the Admin of my computer...)

By the way, this is what my script looks like (super simple, I know... ) :

#!/usr/local/bin/python

print 'The Bright Side of LIfe...'

I'm at my wit's end... Can anyone give me ideas of what to do?

---

### Post by thatguruguy on 2012-07-20
> **antigoneinvicta said:**
> I'm trying to write a script in gedit to execute in bpython (the interpreter I downloaded on Ubuntu). From everything I've read, this should be a simple task, but it seems no matter what I do, I can't get anything but an error message. 

- On the first line of my script, I put "#!/usr/bin/python"
- In bpython, I've tried entering the command a dozen different ways, from "(scriptname).py" to  "/home/(myname)/Documents/(scriptname).py" all to no avail
- I've tried using "chmod +x (scriptname).py
- When I do any of the above, I get the following message: 
Traceback (most recent call last):
      File "<input>", line 1, in <module>
NameError: name '(whateverthefirstwordis)' is not defined

Interestingly, I tried going to my /usr/ folder... I can find /usr/bin/, but in /bin/ there's no folder named "python." I tried creating it, but I was denied access permission (even though I'm the Admin of my computer...)

By the way, this is what my script looks like (super simple, I know... ) :

#!/usr/local/bin/python

print 'The Bright Side of LIfe...'

I'm at my wit's end... Can anyone give me ideas of what to do?

Have you tried the following?
```
python (scriptname).py
```

---


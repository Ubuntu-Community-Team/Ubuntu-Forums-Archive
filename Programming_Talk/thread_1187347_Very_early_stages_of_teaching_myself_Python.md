---
title: "Very early stages of teaching myself Python"
date: 2009-06-14
forum: Programming Talk
---

### Post by gnotis on 2009-06-14
To start, I have not been trained at all in programming. I'm trying to teach myself from scratch, which hasn't been easy. If there is anything that I'm missing the point on or needs to be added, please do so. Right now I have a fairly limited scope of understanding.

I understand that Python is an interpreted language as opposed to a compiled language. 

The first part of a program imports modules. Modules are reusable pieces of code that perform some function. An example is the Time module. This means every time I need to find the time, I don't need to rewrite code to do so. I can do this, for example:
```
strftime("%a, %d %b %Y %H:%M:%S +0000", gmtime())
```I can define functions that are like mini modules I can reuse in my own code.

I'm stuck on classes. Can someone give me a brief layman terms definition?

I have on my local network, my main computer and two Linux based clients. The clients need to be updated regularly. I need to telnet in, shut down a process, delete two files, FTP replacement files and then restart the process. I've been told it would be easier to write a bash script to do this, but I'd like to learn to program.

I have an example from [Pydocs]("http://%5BURL%5Dhttp://www.python.org/doc/2.6/library/telnetlib.html?highlight=telnet#module-telnetlib%5B/URL%5D"):
```

import getpass
import sys
import telnetlib

HOST = "localhost"
user = raw_input("Enter your remote account: ")
password = getpass.getpass()

tn = telnetlib.Telnet(HOST)

tn.read_until("login: ")
tn.write(user + "\n")
if password:
    tn.read_until("Password: ")
    tn.write(password + "\n")

tn.write("ls\n")
tn.write("exit\n")

print tn.read_all()
```I change the HOST variable, save the code, and make it executable. When I run it, nothing happens. When I select "run in terminal" nothing happens. When I run it in IDLE, it seems to work. Is there something I need to add to the code to make it run in terminal? If it does and there is a syntax error, will it show that in the terminal?

Sorry for the rudimentary questions, I'm just struggling. Does anyone live in central Florida that wants to make a few extra bucks and tutor me?

---

### Post by Tony Flury on 2009-06-14
> **gnotis said:**
> ...

I'm stuck on classes. Can someone give me a brief layman terms definition?

ok - a class is a way of storing data and functionality in one place - it is a concept called encapsulation, which is part of OOP (object oriented programming).

The idea is that by placing all the data and functionality together you can do a number of things : 
[LIST]
[*]Keep all internal data private
[*]Define very clear interfaces to your functionality
[/LIST]
You also get great stuff like inheritance, which allows you to take an already defined class and extend it while keeping the orginal code exactly the same, and in the extension class you only need to change the bits that are different.
Wikipedia is a great resource for the above concepts.

> **gnotis said:**
> 
I have on my local network, my main computer and two Linux based clients. The clients need to be updated regularly. I need to telnet in, shut down a process, delete two files, FTP replacement files and then restart the process. I've been told it would be easier to write a bash script to do this, but I'd like to learn to program.

I have an example from [Pydocs]("http://%5BURL%5Dhttp://www.python.org/doc/2.6/library/telnetlib.html?highlight=telnet#module-telnetlib%5B/URL%5D"):
```

import getpass
import sys
import telnetlib

HOST = "localhost"
user = raw_input("Enter your remote account: ")
password = getpass.getpass()

tn = telnetlib.Telnet(HOST)

tn.read_until("login: ")
tn.write(user + "\n")
if password:
    tn.read_until("Password: ")
    tn.write(password + "\n")

tn.write("ls\n")
tn.write("exit\n")

print tn.read_all()
```I change the HOST variable, save the code, and make it executable. When I run it, nothing happens. When I select "run in terminal" nothing happens. When I run it in IDLE, it seems to work. Is there something I need to add to the code to make it run in terminal? If it does and there is a syntax error, will it show that in the terminal?


Add 
```

#!/usr/bin/python

```
As the first line of your file - and make sure it is executable - that will be you can run it from the terminal or by clicking it.
Without that line, linux does not know how to execute the file.

---

### Post by gnotis on 2009-06-14
Tony, Thanks for the info. 

Here's some code that I think would qualify for the "What makes bad code" thread, but this is my first program ever and here it goes.
```
#!/usr/bin/python

import sys
import telnetlib
import time
from ftplib import FTP

HOST = raw_input("What is the IP of the DB? ")
user = raw_input("Enter your remote account: ")
pwd = raw_input("Enter your password: ")
tn = telnetlib.Telnet(HOST)

tn.set_debuglevel(2)
tn.read_until("login: ")
tn.write(user + "\n")
time.sleep(2)
tn.write(pwd + "\n")
time.sleep(2)
print tn.read_very_eager()
tn.write("killall rqcamd\n")
time.sleep(2)

ftp = FTP(HOST)
ftp.login(user, pwd)
ftp.retrlines('LIST')
time.sleep(1)
ftp.ChangeRemoteDir("/var/etc/plimgr/cams")
ftp.retrlines('LIST')
time.sleep(1)

tn.write("rqcamd\n")
time.sleep(2)
print tn.read_very_eager()
time.sleep(10)

```I searched for a way to pause a bit to give time for the remote box to react, but it looks ugly and I assume there's a better way of doing it. Would I use Telnet.read.until()? What if I'm not sure of what the client will return?

Also, I found many examples of how to change directory and download/upload files, but I just became more confused. All the info from [here]("http://www.python.org/doc/2.6/") works, but I find many examples that are not defined by that document. For example the line```
ftp.ChangeRemoteDir("/var/etc/plimgr/cams")
``` I found on the web, but it doesn't work. Is there a place I can find complete info on the methods for the modules? Can methods be defined as needed? Does that even make sense?

If I needed to change file permissions, can I do```
FTP.sendcmd(chmod 755 /some/path thebinary)
```

I'm pretty excited that I got it to connect, shutdown the process, and restart the process. I'm on my way! Thanks for the help.

---

### Post by Tony Flury on 2009-06-15
Well done on your first script. I have never used the ftp module, but you are looking at the best site (docs.python.org).

With regards to changing remote direction there are two things : 

I think you should be using

ftp.cwd

According to the reference material : [http://docs.python.org/library/ftplib.html](http://docs.python.org/library/ftplib.html) 

ftp.ChangeRemoteDir

does not exist.

You also need to know what your remote serves has set its ftp root to - for example (As far as I can remember this is how ftp works) : 

If the remote server has the root of the account set to : 
```

/var/etc/plimgr/

```

Then doing a 
```

cwd "/var/etc/plimgr/cams"

```

Will actually try to set the new directory on the remote folder to : 

```

/var/etc/plimgr/var/etc/plimgr/cams"

```

Which I guess is not what you want.

You might actually want to do :

```

cwd "cams"

```

---


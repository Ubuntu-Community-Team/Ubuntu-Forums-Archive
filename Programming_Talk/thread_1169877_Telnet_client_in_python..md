---
title: "Telnet client in python."
date: 2009-05-25
forum: Programming Talk
---

### Post by P=NP on 2009-05-25
Some background,

I'm just learning to program and wrote a small script:
```

#!/bin/bash
echo 'Change your MAC automatically!'
sleep .7
echo "Shutting down eth0"
sudo ifconfig eth0 down
sleep 2
sudo macchanger -A eth0
echo 'Bringing eth0 back up'
sudo ifconfig eth0 up
sleep 5
echo 'Bye!'
sleep 1.5

```If that looks very rudimentary, it is because it is. This is my first ever workable program that I wrote myself without having to look at examples from the internet. Obviously I have a long way to go. However I think I just had a programming epiphany! So this got me looking around the net for Bash scripting information. I came across an article that said if you can learn to string together a few commands in a Bash script, you can learn to program Python. How convenient - I wanted to learn Python anyway!  And this got me thinking...

I know the above takes a lot of things for granted. Like the device is "eth0" or that the package macchanger is installed. I think I would have needed to learn how to use grep and awk. I didn't really look too deep into it before the direction change. Anyway, I think I'm starting to get how it works. I have a local network with two clients that I have to telnet into on a regular basis, kill a process, delete two file, ftp replacements, restart the process, then end the session or reboot the client. I would like to automate this process. For now I would like to have this program run for only me so no user input is necessary for the IP's of the clients or the location of the files. In the future I would like to add that capability and also the capability to write to a file the names and permissions, time taken, etc... I shouldn't get ahead of myself.

My questions are:
1. What modules are required (I'm assuming a module is a reusable piece of code that provides some function - like opening a telnet session/protocol)

2. Could someone provide a basic outline for me? Not actual code, but something like:
```

shebang/and/stuff yeah
import somejunk
import somecoolstuff

#set variables
How to do stuff,etc

```Not actual code. Oh, and how would I go about finding out the syntax for each module?
Here's an example of some code, but it does some weird stuff and outputs two files that I can't open with anything, so needless to say it didn't teach me much.
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

```3. Is this too advanced for me? Please correct me or steer me in the right direction.

Thanks!

---

### Post by soltanis on 2009-05-25
I assume that when you say 'telnet', you mean you are starting a remote shell on another machine for the purposes of running the commands you said.

Let me introduce you to cron.

Cron automates tasks (like, hey, shell scripts) to do exactly what you said. It is a program that runs in the background, wakes up every minute, sees if it has something to do, executes whatever it has to do, emails you the output then goes back to sleep.

You can configure cron jobs (tasks for cron to execute) to run at specific times on specific days, or at specific intervals (it's pretty damn cool).

So since the tasks you said sound pretty boring and easily automated via shell script, you should go ahead and write a shell script to do them; move it to the remote machine, chmod/chown it, then write a cron job to execute at whatever times you like to take the boring out of computing.

This is not only the Unix way of doing things, but its also considerably easier than trying to write a telnet-compatible program to do what you said.

[http://en.wikipedia.org/wiki/Cron](http://en.wikipedia.org/wiki/Cron)

---

### Post by P=NP on 2009-05-26
Thank you for the reply and advice.

*you mean you are starting a remote shell on another machine for the purposes of running the commands you said.*

Exactly. And I know it would be easier to write a simple script, but the purpose is to learn Python. Which is why I think this is a good starting point. I can start by hard coding the correct information to open the session and login then add user input after. Maybe I'm wrong, but it seems to be perfect to learn on.

What I mean by learning syntax for each module. I would think there would be a standard but take this for example:
```

*class *telnetlib.Telnet([*host*[, *port*[, *timeout*]]])
```Is it ```
 telnetlib.Telnet(192.168.1.1, 21, 10)
```or
```
 telnetlib.Telnet([192.168.1.1] [21] [10])
```Or neither?

---

### Post by imdano on 2009-05-26
> **P=NP said:**
> What I mean by learning syntax for each module. I would think there would be a standard but take this for example:
```

*class *telnetlib.Telnet([*host*[, *port*[, *timeout*]]])
```Is it ```
 telnetlib.Telnet(192.168.1.1, 21, 10)
```or
```
 telnetlib.Telnet([192.168.1.1] [21] [10])
```Or neither?It's the former.  When a parameter to a function is shown in square brackets like that it means it's an optional argument.  The rest of the documentation provides more details about why that's the case
> Telnet represents a connection to a Telnet server. **The instance is initially not connected by default; the open() method must be used to establish a connection. Alternatively, the host name and optional port and timeout can be passed to the constructor, in which case the connection to the server will be established before the constructor returns. The optional timeout parameter specifies a timeout in seconds for the connection attempt (if not specified, the global default timeout setting will be used).**

---

### Post by NathanB on 2009-05-26
A simple Google search dug up this example:

[http://code.activestate.com/recipes/52228/](http://code.activestate.com/recipes/52228/)

---


---
title: "Python program crashes when it cannot connect to host"
date: 2005-12-11
forum: Programming Talk
---

### Post by darthsabbath on 2005-12-11
Hi, all,

I've recently begun work on my first real programming project... a console based email client with a UI based somewhat on Pine (a la Nano being based on Pico)... but with features closer to a standard email client like Thunderbird or Eudora... especially no need for an external agent such as fetchmail. Yeah, I know there's a million email clients, but damnit, I have an itch to scratch. ;-)

Well... I'm fairly new at this programming thing, and I may be missing something totally obvious here... well, let me explain first.

One of the modules I'm creating is a session manager that wraps around the Python implementations of POP3, IMAP, and SMTP to keep them all in one tidy place.  I barely have any code to show for it right now, at least in a useable form... it's just basically being built from the ground up... but take this portion from the POP3 manager... 

```

def ConnectHost(self):
        print "Connecting to host %s" % self.host
        self.session = POP3(self.host, self.port)
        print "Sending username %s" % self.login
        self.session.user(self.login)
        print "Login successful!\n Sending password!"
        self.session.pass_(self.pwd)
        print "Login complete!"

```

Please excuse the simple nature of this... I want to get the basics working before moving on.  Anyway.... Everything's all fine and dandy until, say I enter in an invalid hostname... then the program goes down the tubes:

```

Traceback (most recent call last):
  File "/home/pwm/pyne-project/pyne.py", line 9, in -toplevel-
    p.ConnectHost()
  File "/home/pwm/pyne-project/sessionmgr.py", line 15, in ConnectHost
    self.session = POP3(self.host, self.port)
  File "/usr/lib/python2.4/poplib.py", line 84, in __init__
    for res in socket.getaddrinfo(self.host, self.port, 0, socket.SOCK_STREAM):
gaierror: (-2, 'Name or service not known')

```

Obviously this won't do... is there any way to catch this?  I've looked into try/catch/except statements and am not sure how I would implement them in this situation.  I know there's a Python lib out there that would allow me to ping the host to make sure it's reachable, but Python also crashes on an invalid username or password....

```

Traceback (most recent call last):
  File "/home/pwm/pyne-project/pyne.py", line 9, in -toplevel-
    p.ConnectHost()
  File "/home/pwm/pyne-project/sessionmgr.py", line 19, in ConnectHost
    self.session.pass_(self.pwd)
  File "/usr/lib/python2.4/poplib.py", line 202, in pass_
    return self._shortcmd('PASS %s' % pswd)
  File "/usr/lib/python2.4/poplib.py", line 165, in _shortcmd
    return self._getresp()
  File "/usr/lib/python2.4/poplib.py", line 141, in _getresp
    raise error_proto(resp)
error_proto: -ERR invalid user name or password.

```

Any help would be appreciated on how I could catch these problems.... I don't even need a detailed explanation... if someone could point me to a solution I'd be happy to pursue it on my own.

Maybe I'm just being dense this weekend. :-)

Phil

---

### Post by amohanty on 2005-12-11
I would suggest each module handle its own errors, so that this:
> self.session = POP3(self.host, self.port)

should do the error handling for server connectivity, similarly for user authentication, the name validation should be handled by the:
> self.session.user(self.login)

which means in botch cases the POP3 class. I havent used it so cant help you there. Also you will have to go through the source/docs and find out what errors are raised by the methods you mentioned above and then:

> try:
  sess = POP3... 
  sess.user...
  sess.pass....
except ErrorRaisedByPOP2Ctor:
  print err
except ErrorRaisedBysession.user:
  print err
...
...
else:
  cleanup()

HTH

---

### Post by ow50 on 2005-12-11
[QUOTE=darthsabbath]Obviously this won't do... is there any way to catch this?  I've looked into try/catch/except statements and am not sure how I would implement them in this situation.[/QUOTE]
gaierror is explained [here](http://docs.python.org/lib/module-socket.html).

So, something like this might do:
```
import socket
(...)
try:
    self.session = POP3(self.host, self.port)
except socket.herror, detail:
    print (...)
except socket.gaierror, detail:
    print (...)
except socket.timeout, detail:
    print (...)
```

Catch every possible error and print an error message suitable for the error catched.

---

### Post by darthsabbath on 2005-12-11
Awesome... thanks for the help guys.  I was thinking it had to be something along those lines, but I'll be damned if I knew what. :-)

Phil

---


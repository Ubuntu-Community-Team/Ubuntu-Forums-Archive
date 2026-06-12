---
title: "[Python] POP3 and IMAP both don't connect"
date: 2009-09-03
forum: Programming Talk
---

### Post by fiddler616 on 2009-09-03
Hello,

I'm writing a program that involves sending and receiving emails.

For receiving them, the POP3 library seemed like the way to go. The Python documentation has the following example:

[PHP]import getpass, poplib

M = poplib.POP3('localhost')
M.user(getpass.getuser())
M.pass_(getpass.getpass())
numMessages = len(M.list()[1])
for i in range(numMessages):
    for j in M.retr(i+1)[1]:
        print j
[/PHP]

which I modified to
[PHP]import poplib
print "Connecting..."
M = poplib.POP3('pop.gmail.com', 995)#Gmail said that you had to specify port 995 for SSL
print "Connected to pop.gmail.com"
M.user("tsmacdonald@gmail.com")
M.pass_("<the password>")
print "User tsmacdonald authenticated."
numMessages = len(M.list()[1])
for i in range(numMessages):
    for j in M.retr(i+1)[1]:
        print j
M.quit()#The Python docs said the mail server would be tied up until quit() was called.
[/PHP]
And here's what happens:
```
$ python pop_simple.py 
Connecting...
^CTraceback (most recent call last):
  File "pop_simple.py", line 3, in <module>
    M = poplib.POP3('pop.gmail.com', 995)
  File "/usr/lib/python2.6/poplib.py", line 86, in __init__
    self.welcome = self._getresp()
  File "/usr/lib/python2.6/poplib.py", line 124, in _getresp
    resp, o = self._getline()
  File "/usr/lib/python2.6/poplib.py", line 106, in _getline
    line = self.file.readline()
  File "/usr/lib/python2.6/socket.py", line 404, in readline
    data = self._sock.recv(self._rbufsize)
KeyboardInterrupt

```
(it hangs at "Connecting...", and then I pres a button, and it throws all those errors.)

A similar thing happens with a more complex example I found online.

Forgetting about these forums, I was like "Well, POP is kind of old, and it's giving me problems. Why don't I just use IMAP?"

And it's the same:
[PHP]$ cat imap_simple.py && python imap_simple.py 
import imaplib
print "Connecting"
M = imaplib.IMAP4("imap.gmail.com", 995)
M.login("tsmacdonald", "<password>")
M.select()
typ, data = M.search(None, 'ALL')
for num in data[0].split():
    typ, data = M.fetch(num, '(RFC822)')
    print 'Message %s\n%s\n' % (num, data[0][1])
M.close()
M.logout()
Connecting
(I can type random things here, and nothing happens). Now I'm going to press Ctrl-C^CTraceback (most recent call last):
  File "imap_simple.py", line 3, in <module>
    M = imaplib.IMAP4("imap.gmail.com", 995)
  File "/usr/lib/python2.6/imaplib.py", line 184, in __init__
    self.welcome = self._get_response()
  File "/usr/lib/python2.6/imaplib.py", line 907, in _get_response
    resp = self._get_line()
  File "/usr/lib/python2.6/imaplib.py", line 1000, in _get_line
    line = self.readline()
  File "/usr/lib/python2.6/imaplib.py", line 241, in readline
    return self.file.readline()
  File "/usr/lib/python2.6/socket.py", line 404, in readline
    data = self._sock.recv(self._rbufsize)
KeyboardInterrupt
[/PHP]

So I'm beginning to think that it's something the matter with Gmail, not my Python, but am still thoroughly confused. What should I do?

Thanks.

---

### Post by steeleyuk on 2009-09-03
I am by no means a Python expert... I know a little about a little. But I think you just needed to add (line 3: _SSL):

```
import poplib
print "Connecting..."
M = poplib.POP3**_SSL**('pop.gmail.com', 995)#Gmail said that you had to specify port 995 for SSL
print "Connected to pop.gmail.com"
M.user("tsmacdonald@gmail.com")
M.pass_("<the password>")
print "User tsmacdonald authenticated."
numMessages = len(M.list()[1])
for i in range(numMessages):
    for j in M.retr(i+1)[1]:
        print j
M.quit()#The Python docs said the mail server would be tied up until quit() was called.
```

When it connects though, it will spew out a lot of data.

---

### Post by steeleyuk on 2009-09-03
And here's my attempt at the IMAP version:

> import imaplib
print "Connecting"
M = imaplib.IMAP4_SSL("imap.gmail.com")
M.login("steeley.uk", "<pass>")
M.select()
typ, data = M.search(None, 'ALL')
for num in data[0].split():
    typ, data = M.fetch(num, '(RFC822)')
    print 'Message %s\n%s\n' % (num, data[0][1])
M.close()
M.logout()
print "Reached end"

Again, same _SSL portion of code. Python docs also say that if you don't specify a port, 993 is used as the standard IMAP4 over SSL. The app appears to connect (it hits the print statement at the end without error anyway).

Like I say, I don't know massive amounts about Python so someone else will likely have better suggestions. :)

---

### Post by fiddler616 on 2009-09-04
Thanks! Just using the POP3_SSL function instead of POP3 did the trick.

---


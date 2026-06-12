---
title: "twisted question"
date: 2009-04-13
forum: Programming Talk
---

### Post by NetSkay on 2009-04-13
hello...
im building an application with twisted framework for python... i currently want to add smtp to the application; all the smtp class is going to do is receive some data from a calling class/method then email to a bunch of email addresses...
im left with a bit of confusion here, since my application is already driven by twisted and i have invoked the reactor.run() method, can i still build the smtp class and call reactor.run(), would that interfere with the main loop that i already have going on... i know i can start a subprocess, but i do not wish to do so for various reasons...
my other option is not to use twisted for this simple smtp mailing but rather use python and a 3rd party smtp lib and implement deferreds/callbacks instead...

any advices are appreciated

---

### Post by snova on 2009-04-13
> **NetSkay said:**
> im left with a bit of confusion here, since my application is already driven by twisted and i have invoked the reactor.run() method,

On a side note, you usually shouldn't have to call reactor.run(), twisted.application does this along with a few other nice things (daemonization, logging setup). But for now...

> can i still build the smtp class and call reactor.run(), would that interfere with the main loop that i already have going on...

Probably. If the smtp class you are using uses blocking calls, then absolutely.

> i know i can start a subprocess, but i do not wish to do so for various reasons...

Twisted has a deferToThread() method which would also work, but you probably don't need to.

Have you considered twisted.mail? I don't know much about it, but in general it's easiest to use Twisted's functionality for something, since it'll integrate better.

---

### Post by NetSkay on 2009-04-13
you know, i did try twisted mail... but i never saw SSL module/attribute... so i cant really use twisted, rather ill use this really nice custom lib i found and do deferToThread on twisted...
if SSL does exist in twisted, someone slap me and tell me where to find it lol

thnx

---


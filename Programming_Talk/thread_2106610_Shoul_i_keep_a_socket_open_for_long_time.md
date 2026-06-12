---
title: "Shoul i keep a socket open for long time?"
date: 2013-01-19
forum: Programming Talk
---

### Post by nidzo732 on 2013-01-19
I have two computers on a network and some python programs running on them. Occasionally the programs will send some data to each other. There may be a long silence between individual messages. Should I keep an open socket all the time or create a new socket for every message?
Which of these is better:
This one
```

#keeps an open socket
s=socket(...)
s.connect(someAddress)
while True:
    s.send(someData)
    sleep(five minutes)

```
or this one
```

#creates a new socket for each individual communication
while True:
    s=socket(...)
    s.connect(someAddress)
    s.send(someData)
    s.close()
    sleep(five minutes)

```

---

### Post by bogustrumper on 2013-01-19
My read of this page: [http://docs.python.org/2/howto/sockets.html](http://docs.python.org/2/howto/sockets.html) makes it sound like you're ever-so-slightly better off closing the socket when you're done sending. 

Makes some intuitive sense to me... if the sending computer shuts off or gets disconnected by your cat/kid/housecleaner (or, more likely, crashes/hangs on some other line of code you've written and for some reason doesn't get to the normal garbage collection), the listening end could hang on their socket f it's still open. I'd doubt it'll matter too much beyond that, assuming you get the right behavior with both styles that you mentioned (ie, that there's not a noticeable overhead to opening the socket in the first place).

---


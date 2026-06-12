---
title: "question on code [twisted framework]"
date: 2010-09-15
forum: Programming Talk
---

### Post by mo.reina on 2010-09-15
just want to make sure i'm understanding this right...

main function:
```
.....
.....
for address in addresses:
        host, port = address
        get_poetry(host, port, got_poem, poem_failed)
.....
.....
```

get_poetry function:
```
.....
.....
from twisted.internet import reactor
factory = PoetryClientFactory(callback, errback)
reactor.connectTCP(host, port, factory)
.....
.....
```

is the following code creating one factory for each address?  i'd imagine so, since the get_poetry function is being called once for each address, but since i'm still learning the framework i´m not totally sure....

---

### Post by mo.reina on 2010-09-16
bump

---


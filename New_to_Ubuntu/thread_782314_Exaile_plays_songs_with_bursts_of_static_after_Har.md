---
title: "Exaile plays songs with bursts of static after Hardy install"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by 449 on 2008-05-04
How can I fix this? I don't have this problem with banshee or any other audio. Help would be greatly appreciated.

Thanks.

---

### Post by 449 on 2008-05-06
Anyone?

---

### Post by AndrewTheArt on 2008-05-06
Run it from the command line to get possible debug messages. Can't think of anything else specifically at the moment. Also, try Google-ing the problem.

---

### Post by 449 on 2008-05-10
> **AndrewTheArt said:**
> Run it from the command line to get possible debug messages. Can't think of anything else specifically at the moment. Also, try Google-ing the problem.

```
erik@erik-desktop:~$ exaile
Exaile 0.2.13
Created db for thread Thread-1
{'Thread-1': <sqlite3.Connection object at 0x8994cc8>}
Using multimedia keys from: gnome
Starting scan timer at 25.0
loading tracks...
Closed db for thread Thread-1
done loading tracks...
loading songs
Clearing tracks cache
Last playlist loaded
ReplayGain support initialized.
Exception in thread Thread-8:
Traceback (most recent call last):
  File "/usr/lib/python2.5/threading.py", line 486, in __bootstrap_inner
    self.run()
  File "/usr/share/exaile/xl/covers.py", line 96, in run
    ResponseGroup="ItemAttributes,Images")
  File "/usr/share/exaile/lib/ecs.py", line 340, in ItemSearch
    return pagedIterator(XMLItemSearch, argv, "ItemPage", 'Items', plugins)
  File "/usr/share/exaile/lib/ecs.py", line 217, in __init__
    dom = self.__search(** self.__arguments)
  File "/usr/share/exaile/lib/ecs.py", line 349, in XMLItemSearch
    return query(buildRequest(argv))
  File "/usr/share/exaile/lib/ecs.py", line 175, in query
    e = buildException(errors)
  File "/usr/share/exaile/lib/ecs.py", line 160, in buildException
    e = globals()[ class_name ](msg)
KeyError: u'ECommerceService.NoExactMatches'

Equalizer support initialized.
new thread created with A.F.I. - Decemberunderground
Amazon: cover thread started

```

---

### Post by ShodanjoDM on 2008-05-10
[https://bugs.launchpad.net/exaile/+bug/192086](https://bugs.launchpad.net/exaile/+bug/192086)

I'm running the 0.2.14 development version and I still have to disable the EQ.

---


---
title: "python urllib f.read() giving me trbl"
date: 2011-07-12
forum: Programming Talk
---

### Post by jerry01 on 2011-07-12
i've got a problem with python 3.1 using urllib

i can't seem to get the returned data into a string. i need to have something i can manipulate. could someone tell me how to go from "f.read()" to data or an array?

```
   f = urllib.request.urlopen(urlstr)
    print(f.read(5000))
    data=f.read()
    print(">>>>>"+str(data))

```b'<html>\r\n/var/web/servlet.ksh null 53.104891 \r\n</html>\r\n'
>>>>>b''

it's probably a basic question but i've already wasted a lot of time...
many thanks

---

### Post by Bachstelze on 2011-07-12
For starters, why are you calling read() twice? It probably does not do what you think.

---

### Post by jerry01 on 2011-07-12
found my own solution

as follows if anyone is interested...

```
    f = urllib.request.urlopen(urlstr)
    by= bytearray(f.read(100))
    data=by.decode("ascii")

```

---


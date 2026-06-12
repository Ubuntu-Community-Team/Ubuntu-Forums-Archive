---
title: "How to recursively delete all files with a specific file extension starting from??"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by inktri on 2008-09-23
how do you recursively delete all files with a specific file extension starting from a folder

i'm assuming the command has rm, -R, and *.<extension> but don't know for sure

thanks

---

### Post by kpkeerthi on 2008-09-23
```
find /where/to/search/from/ -iname "*.<extension>" -exec rm '{}' ';'
```

```
find /where/to/search/from/ -iname "*.<extension>" -ok rm '{}' ';'
```

The second command will prompt for confirmation before it is removed, for each file.

---

### Post by eentonig on 2008-09-23
First: Don't do this as root!!! Or not untill you're completly sure you did'nt make a fault in you're thinking and command.

next

> rm -vRI /PATH/TO/STARTING/POINT/*<extension>

-v for verbose
-R for recursive going down the stream
-I safety net, just so you know you can say no when something goes wrong.

I strongly advice to supply the explicit path to the location where you want to start the recursive rm, just to protect yourself from issuing the command below /etc because you forgot you just did an 'cd /etc' two commands ago.


What I always do when I need to issue a command with some options I'm not sure off

> man rm

---

### Post by eentonig on 2008-09-23
Actually kpkeerthi,

what's the difference between you're approach and mine, regarding safety and processing that is?

---

### Post by bonfire89 on 2009-09-09
I could go for knowing the difference :)

---

### Post by natuk on 2010-06-06
I think kpkeerthi's solution actually goes down to the sudirectories, whereas eentonig's solution seems to stay only on the specified directory.

---


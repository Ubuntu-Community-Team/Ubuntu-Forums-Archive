---
title: "Cut chars from the end of string to the dilimeter char?"
date: 2009-08-25
forum: Programming Talk
---

### Post by PryGuy on 2009-08-25
Good day, everyone!

The question is: I have a variable, it's an IP address. Say it's '192.168.0.1'. I want to cut characters counting backwards from the end of the string up to the '.' char. Is it possible to do it in pure bash?

I can't just cut a fixed number of characters, 'cause the length of the IP address can be different, eg. '192.168.0.1' and '10.215.215.10'.

Thank you in advance!

UPDATE! I have found the answer!!!
```
echo "192.168.0.1" | cut -d "." -f 1-3
```

---

### Post by DaithiF on 2009-08-25
Hi, you can do this directly in bash too, using a string replacement operator.  saves you spawning a new process.

```
myvar=192.168.0.1
result=${myvar%.*}
echo $result
192.168.0

```

---


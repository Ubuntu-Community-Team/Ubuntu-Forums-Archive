---
title: "touch"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by fmpfmpf on 2008-05-15
can some explain to me what the touch command is?
i did use man touch, and it says it changes the file timestamps.
what does that mean?

thank you

---

### Post by compwiz18 on 2008-05-15
```
cd /tmp
```
Change to the tmp directory to play with touch.

```
touch a-file
```
will create a file called a-file

```
touch an-existing-file
```
will update the modified and access times to now (ie, the computer keeps track of when you last modified and last accessed the file, and using touch will make that right now)

Hope that helps :KS

---

### Post by drs305 on 2008-05-15
touch will also allow you to change the date/time of a file to one of your choosing. The format would be:
```
touch -t CCYYMMDDhhmm.ss <file>
```
For example, to make the date of filename 0900 on May 15, 2008:
```
touch -t 200805150900 filename
```

You can learn more at:
```
man touch
```

---


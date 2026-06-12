---
title: "useing sleep command not working"
date: 2012-05-20
forum: New to Ubuntu
---

### Post by hookitup on 2012-05-20
so i want to make a command run at startup but wait about 20 seconds before it runs, the sleep command is not working for me idk, i type ```
sleep 20`s' command
``` and nothing seems to happen after 20 seconds, am i doing the command wrong?

---

### Post by billyseth on 2012-05-20
the default is already seconds, and a semicolon between the time and the command works...

```
sleep 20;command
```

should do the trick

---

### Post by Lisiano on 2012-05-20
Using ` means you want the output of something enclosed in `` to be expanded in the place of the command. For example
```
echo Current time is `date`
```
' is the same as " as in it's used to group stuff so it won't get interpreted as separate items.
Useful if you want to change to a directory containing a space(s)
```
cd '~/Pictures/Needs editing/May 15th/'
```
In your case, you musn't add either one of those. Also as billyseth pointed out, sleep defaults to seconds.

---

### Post by hookitup on 2012-05-20
oh sweet ok that totally did the trick with the simcollan , and ok thats great information guys, thanks for all the help.

---


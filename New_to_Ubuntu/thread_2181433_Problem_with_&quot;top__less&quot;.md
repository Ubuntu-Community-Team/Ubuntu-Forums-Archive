---
title: "Problem with &quot;top | less&quot;"
date: 2013-10-17
forum: New to Ubuntu
---

### Post by kevin_do2 on 2013-10-17
Hi all,
When I experienced the command "top | less", then quit, and type some random text before shell prompt, my input text in command line interface becomes invisible. Can anyone explain this?

---

### Post by steeldriver on 2013-10-17
Maybe some control characters in the top output are messing with your terminal settings? if you want to pipe top to less you should probably use the batch (-b) mode

```
top -b | less
```

see man top

```

       -b : Batch mode operation
            Starts  top in 'Batch mode', which could be useful for sending output from top to other programs or to a file.  In this mode, top will not accept input and runs
            until the iterations limit you've set with the '-n' command-line option or until killed.

```

---


---
title: "gmail scripting help"
date: 2013-01-22
forum: New to Ubuntu
---

### Post by rburkartjo on 2013-01-22
is there a way or a script to actually read your gmail in the terminal. i am using the following to check my gmail but it only list the emails i have i cant read them
#!/bin/bash
curl -u xxxx --silent "https://mail.google.com/mail/feed/atom" | perl -ne 'print "\t" if /<name>/; print "$2\n" if /<(title|name)>(.*)<\/\1>/;'
sleep 25

note xxxx is my user name.
tks

---

### Post by tgalati4 on 2013-01-22
You could set up a mailx account to pull mail from gmail and then read using mail.

```
man mailx
```

---


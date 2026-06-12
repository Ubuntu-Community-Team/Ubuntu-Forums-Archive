---
title: "cant send mail with sendEmail"
date: 2013-10-17
forum: New to Ubuntu
---

### Post by davidtuti2 on 2013-10-17
Hi,
I was trying to simple way to send mail from command line. 
I'm trying with sendEmail but I have error.
Could you help me please?
Many thanks and sorry for my english!

```
sendemail -f user@gmail.com -m 'hola' -t user@gmail.com -s smtp.gmail.com:587 -xu myaccount@gmail.com -xp password -o tls=yes



sendEmail[4741]: ERROR => Connection attempt to smtp.gmail.com:587 failed: IO::Socket::INET6: connect: connection refused
```

---

### Post by sanderj on 2013-10-17
Does it work with "-s smtp.gmail.com"?

And what does "ping6 -n smtp.gmail.com" tell you?


EDIT & PS:

I just saw the other threads which you started, in which you don't followup to advice given. If that happens in this thread, I'll put you on my ignore list; I prefer to spend my time on usefull threads. #justsaying

---

### Post by sanderj on 2013-10-18
... and ... welcome to my ignore list.

---


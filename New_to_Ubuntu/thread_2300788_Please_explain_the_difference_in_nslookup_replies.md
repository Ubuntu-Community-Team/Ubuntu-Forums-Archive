---
title: "Please explain the difference in nslookup replies"
date: 2015-10-28
forum: New to Ubuntu
---

### Post by papakota on 2015-10-28
Hello!
When I choose my ISP's nameserver and do this:
set q=ns
.
then in ADDITIONAL section I can see root servers IP's.
When I perform the same check on my BIND, I don't get to see the IP's.  Not like it really all that important, but I'm very curious as to why is  that!

---

### Post by SeijiSensei on 2015-10-29
Do you have [recursion]("http://www.zytrax.com/books/dns/ch2/index.html#recursive") enabled in named.conf?  
```

options {
          stuff

          recursion yes;
           
          more stuff
};

```
I suspect you have it disabled, or it is restricted by an allow-recursion directive.

---


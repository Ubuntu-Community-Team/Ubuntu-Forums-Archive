---
title: "How do i user std out in another command"
date: 2009-02-17
forum: Programming Talk
---

### Post by b-boy on 2009-02-17
Hi 

I would like to grep for a string and user the out put to grep for something else

my code is 
```
grep -i 1111 /var/log/messages|cut -d " " -f 2 
```

my std out is then 
```
10.3.2.1
```

now i want to user this (10.3.2.1) to grep in /var/log/messages again

I would like to do this in one command and I have to 1st find 1111

---

### Post by b-boy on 2009-02-17
ok i figured it out 

```
grep `grep -i 1111 /var/log/messages|cut -d " " -f 2` /var/log/messages
```

---


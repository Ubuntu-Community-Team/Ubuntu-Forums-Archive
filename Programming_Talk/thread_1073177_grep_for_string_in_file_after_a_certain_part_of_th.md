---
title: "grep for string in file after a certain part of the file"
date: 2009-02-18
forum: Programming Talk
---

### Post by b-boy on 2009-02-18
Hi guys

I want to search for a sting in /var/log/messages but I want to look for the work after a specified time onwards

So what I want is to look for ubuntu in /var/log/messages but only look after 10:00 anything before 10:00 must be ignored

how can i do this

---

### Post by geirha on 2009-02-18
```
awk '/ubuntu/ {if ($3 >= "10:00:00") print}' /var/log/messages
```

---


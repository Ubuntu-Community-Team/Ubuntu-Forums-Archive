---
title: "grep date order"
date: 2012-08-09
forum: New to Ubuntu
---

### Post by Kevin McCready on 2012-08-09
Hi Guys
I did an advanced search on the forum for a tile with 'grep date order' but got no result.

So I was hoping someone could help me with the command to display these results by date order and display the date the file was last altered.

ls /home/k/Documents |grep -i 'cancer'

---

### Post by papibe on 2012-08-09
Hi Kevin McCready.

The option -t sorts by mod time, and -r reverse it.

For instance:
```
ls -lt
```
Tell us how it goes.
Regards.

---

### Post by Kevin McCready on 2012-08-09
thanks, that worked. though I guess processing time is longer by placing it in the ls command rather than the grep command. When I ran the command the fan came on, which normally tells me CPU is working hard

---


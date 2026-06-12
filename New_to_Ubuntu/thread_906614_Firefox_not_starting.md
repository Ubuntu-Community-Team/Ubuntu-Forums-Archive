---
title: "Firefox not starting"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by Jshinply on 2008-08-31
Occasionally when I try and open Firefox, I will see "Starting Firefox Web Browser" down on the task bar, and then that disappears, and Firefox never actually opens.

However, when I type "ps -e | grep firefox" into terminal, there was a process started.  Any ideas as to why no browser comes up?

---

### Post by alienexplorers on 2008-08-31
Its probably an old process stuck there. Just Kill the process and wait 10 seconds and reload firefox.

---

### Post by Jshinply on 2008-08-31
> **alienexplorers said:**
> Its probably an old process stuck there. Just Kill the process and wait 10 seconds and reload firefox.

I have tried killing all the processes first.  No luck :(

---

### Post by Line on 2008-08-31
my habit from the early windows days is to uninstall/install :D
sudo apt-get remove firefox
sudo apt-get install firefox

---

### Post by arulkandhan on 2011-03-27
Line's solution is by far the best.... no non-sense.... Best solution bro! Thank you!!

---


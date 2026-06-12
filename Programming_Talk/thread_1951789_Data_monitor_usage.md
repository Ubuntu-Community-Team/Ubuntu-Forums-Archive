---
title: "Data monitor usage"
date: 2012-04-03
forum: Programming Talk
---

### Post by masterjoda on 2012-04-03
Hello, because I don't have unlimited internet access I would like to make a script that would start every time I connect to the some network and monitor how much data I have downloaded/uploaded and to memorize it in some text file for later statistics.

---

### Post by SuperCamel on 2012-04-03
The Netmonitor screenlet does something very similar to what you described. I'm sure it's code would give you a few good pointers.

---

### Post by masterjoda on 2012-04-03
Thanks

---

### Post by ofnuts on 2012-04-04
> **masterjoda said:**
> Hello, because I don't have unlimited internet access I would like to make a script that would start every time I connect to the some network and monitor how much data I have downloaded/uploaded and to memorize it in some text file for later statistics.
See /proc/net/dev. It's a quite simple matter to parse the info you need from that file.

---


---
title: "Synaptic Error: E: dpkg was interrupted"
date: 2013-02-10
forum: New to Ubuntu
---

### Post by yasink on 2013-02-10
>> The problem is not repeated when I opened the Synaptic after 5 minutes.

This is there error I get when I try to open Synaptic Package Manager. I am an absolute beginner.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by ibjsb4 on 2013-02-10
Just do what it said.
[URL="https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal"]
Open a terminal[/URL] and enter:

```
sudo dpkg --configure -a
```

---


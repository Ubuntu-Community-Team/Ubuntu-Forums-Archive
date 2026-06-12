---
title: "Python execution"
date: 2012-06-06
forum: Programming Talk
---

### Post by ki4jgt on 2012-06-06
Does Python read scripts dirctly from the harddrive or from memory?

---

### Post by raja.genupula on 2012-06-06
yeah you have to change to the directory where you got the script and if you have custom modules make sure that those modules are also in correct path .

---

### Post by MG&amp;TL on 2012-06-06
> **ki4jgt said:**
> Does Python read scripts dirctly from the harddrive or from memory?

Initially, yes. Once the script has been loaded though, it continues in memory until it dies.

---

### Post by Lux Perpetua on 2012-06-06
> **ki4jgt said:**
> Does Python read scripts dirctly from the harddrive or from memory?I'm guessing you're confused about something on a deeper level, so I suggest trying to ask your question in a different way.

---

### Post by ki4jgt on 2012-06-06
> **MG&TL said:**
> Initially, yes. Once the script has been loaded though, it continues in memory until it dies.

> **Lux Perpetua said:**
> I'm guessing you're confused about something on a deeper level, so I suggest trying to ask your question in a different way.

Dumb question. If I had thought about it it would have been obvious. Python based server programs wouldn't have the resources to reread the program every time they had to execute something facepalm.

---

### Post by Bachstelze on 2012-06-06
> **MG&TL said:**
> Initially, yes. Once the script has been loaded though, it continues in memory until it dies.

Unless paging or something like that happens... But of course the paging would happen on the Python process, not on the script *per se*.

---


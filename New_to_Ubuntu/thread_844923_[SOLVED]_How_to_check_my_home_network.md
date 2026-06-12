---
title: "[SOLVED] How to check my home network?"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by peakshysteria on 2008-06-30
Is there a way to see if there are people trying to hack into my network? And if i find out that someone are trying to get in how do I get rid of them? For some time back I had a friend over which ran a command which showed everyone trying to get in. And he got a hit. Then got rid of the intruder. I've tried to google but as a n00b I can't find anything.

---

### Post by iaculallad on 2008-06-30
> **peakshysteria said:**
> Is there a way to see if there are people trying to hack into my network? And if i find out that someone are trying to get in how do I get rid of them? For some time back I had a friend over which ran a command which showed everyone trying to get in. And he got a hit. Then got rid of the intruder. I've tried to google but as a n00b I can't find anything.

Try Ubuntu's built-in terminal commands:

```
lsof -i -n -P
netstat -plntu

```
Or, install nmap

```
sudo apt-get install nmap
```

Then:

```
sudo nmap -sS -sV 127.0.0.1
```

---

### Post by peakshysteria on 2008-06-30
Nice. Thanks man. Just in time before breakfast :) I like to keep it simple so those first commands seems to be enough for now anyway. All looks good. If people have other tips n' trick they are welcome.

---


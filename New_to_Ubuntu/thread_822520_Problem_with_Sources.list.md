---
title: "Problem with Sources.list"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by Beatbreaker on 2008-06-08
i just got this error in the synaptic package manager:

> Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

what's going on?

---

### Post by Joeb454 on 2008-06-08
Click Applications > Accessories > Terminal, and then run the following commands 1 line at a time.

```
cat /etc/apt/sources.list > ~/Desktop/sources.txt
```Please upload this as an attachment in another post :)

THEN, run ```
sudo apt-get update
sudo apt-get install -f
```

---

### Post by bumanie on 2008-06-08
Post the output of > cat /etc/apt/sources.list

---

### Post by Beatbreaker on 2008-06-14
I've wacked it into a pastebin - check it out

[http://pastebin.com/f367ee9a3](http://pastebin.com/f367ee9a3)

many thanks

---

### Post by Beatbreaker on 2008-06-16
bump

---

### Post by forestpixie on 2008-06-16
Looks ok at first glance but can you open a terminal and run

```
sudo apt-get update
``` and post the output here please

---


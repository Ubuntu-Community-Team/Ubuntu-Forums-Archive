---
title: "Bash for loop to run commands from a text file."
date: 2014-06-10
forum: New to Ubuntu
---

### Post by bjforesthowell on 2014-06-10
I’m trying to write a for loop that looks at a list of hosts in a text file then runs a series of commands from another text file named with the ip of the host and the file extension.txt.

For example, in the hosts.txt file I would have the following…

```
192.168.1.1
192.168.3.1
192.168.2.197
```

Etc… etc… etc...

In another directory I would have files named as follows with a different set of commands that I wanted to run on each host…

```
192.168.1.1.txt 192.168.3.1.txt 192.168.2.197.txt
```

So if host 192.168.1.1 exists in hosts.txt it runs the commands in 192.168.1.1.txt against that host. What would be the easiest vehicle in order to get this accomplished if it isn’t the for loop?

---


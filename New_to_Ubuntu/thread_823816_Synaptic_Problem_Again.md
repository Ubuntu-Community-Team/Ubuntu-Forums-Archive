---
title: "Synaptic Problem Again"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by bern1939 on 2008-06-09
From a previous post I wish to say that I am unable to open from System/Admin the following:

Partition Editor
Software Sources
Synaptic Manager

However _**I can open**_ Synaptic from the terminal. The following is what I get at the terminal prior to the package opening:

bernard@bernard-desktop:~$ sudo synaptic
sudo: unable to resolve host bernard-desktop

Now the question is: What does the last line indicate & how might it be corrected??

What command is reqd. to install Synaptic again?

Thanks

Bern

---

### Post by Cypher on 2008-06-09
Try these commands in the terminal
```

echo $display

```
then try
```

xhost +

```
and now try opening the offending applications again..

---

### Post by bern1939 on 2008-06-09
bernard@bernard-desktop:~$ echo $display

bernard@bernard-desktop:~$ xhost +
access control disabled, clients can connect from any host
bernard@bernard-desktop:~$ 

No change to opening I'm afraid.

Bern

---


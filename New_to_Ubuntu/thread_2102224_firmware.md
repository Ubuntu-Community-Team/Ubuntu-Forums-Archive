---
title: "firmware"
date: 2013-01-06
forum: New to Ubuntu
---

### Post by Michael James Downey on 2013-01-06
how do discover firmware on ubuntu  PC. I uderstand thre is a character in front of shw where do i find character

---

### Post by iMac71 on 2013-01-06
> **Michael James Downey said:**
> how do discover firmware on ubuntu  PC. I uderstand thre is a character in front of shw where do i find characterperhaps do you mean lshw? If so, the right syntax is```
sudo lshw
```

---

### Post by audiomick on 2013-01-06
That will give you a very long output. There are a couple of ways of reducing it a bit. Look at the man page for some info

```
man lshw
```

---

### Post by Terl on 2013-01-06
> **Michael James Downey said:**
> how do discover firmware on ubuntu  PC. I uderstand thre is a character in front of shw where do i find character

We can probably help you faster if we knew what you might be trying to find out?  Are you having trouble with something specific, or a piece of hardware not being recognized that you think should be?

---

### Post by Abhinav Kumar on 2013-01-07
> **audiomick said:**
> That will give you a very long output. There are a couple of ways of reducing it a bit. Look at the man page for some info

If you want to see a particular class of hardware say network, you could type in a terminal
```
sudo lshw -C network
```
If you want to see all of them, try
```
sudo lshw | more
```
:)

Abhinav

---


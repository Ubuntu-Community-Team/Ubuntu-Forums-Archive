---
title: "[SOLVED] Problem with installing amarok"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by shadowber on 2008-08-24
when i try to install amarok in synaptic, i get the message that it depends on libpq5, which depends on libldap2 (>=2.1.17-1) which is not installable.... I use it on my laptop, and would appreciate any help on how to install it on my desktop, thanx.

---

### Post by shadowber on 2008-08-24
bump

---

### Post by Elfy on 2008-08-24
Can you post your sources list please and the output from the command 

```
cat /etc/apt/sources.list
sudo aptitude install amarok
```

---

### Post by hopkinsjeni on 2008-08-24
I had problems installing Amarok as well. Do you have a split hard-drive? I have both windows and ubuntu and found that is was a lack of space on my hard-drive (after much confusion I must say) and found deleting the unnecessary sound programs solved the problem.

---

### Post by Northsider on 2008-08-24
Amarok doesn't come pre-installed?  I'm using Kubuntu so many it just comes with that and not Ubuntu.

---

### Post by Elfy on 2008-08-24
Yea - it's kubuntu by default

@shadowber - try to install libldap

```
sudo apt-get install libldap-2.4.2
```

---

### Post by shadowber on 2008-08-24
> **forestpixie said:**
> Can you post your sources list please and the output from the command 

```
cat /etc/apt/sources.list
sudo aptitude install amarok
```
sudo aptitude install amarok
worked for me, thanx.

---

### Post by Elfy on 2008-08-24
Ok - great, not sure why synaptic caused a problem there - although I usually install it with apt-get,

Could you mark thread solved please.

---

### Post by henry87 on 2008-08-27
I have a problem in running amarok. It installed properly but it gives some wierd error when I try running it. First it says dcop server isn't running. I ran dcopserver manually in terminal. This time it said amarok couldn't find sound engine plugins. Help!!! By the way I'm an absolute beginner.

---


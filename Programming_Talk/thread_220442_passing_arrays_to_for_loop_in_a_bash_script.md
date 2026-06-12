---
title: "passing arrays to for loop in a bash script"
date: 2006-07-21
forum: Programming Talk
---

### Post by ssalman on 2006-07-21
Hi, I’m trying to setup a firewall blocking certain websites through a bash script using iptables based on [this ]("https://help.ubuntu.com/community/IptablesHowTo")iptables howto.

for each blocked website I'm using the command:


```
iptables -A OUTPUT -d www.website.com -j DROP
``` 
  
Now I have many websites in a list file "block.list", and would like to have the script pass them one by one in a for loop... How would I accomplish that in a bash script?

something of the general form below:
```
for x in ???block.list???
do
    iptables -A OUTPUT -d $x -j DROP;
done

```

---

### Post by fabiand on 2006-07-21
Hey,

a sample:

```

BLOCKLIST="google.com slashdot.org"

for SITE in $BLOCKLIST;
do
  iptables ..... $SITE;
done;
```

---

### Post by kabus on 2006-07-21
> Now I have many websites in a list file "block.list", and would like to have the script pass them one by one in a for loop...

Why not a while loop?

```
while read site; do 
    something $site
done <block.list
```

---

### Post by ssalman on 2006-07-21
> **kabus said:**
> Why not a while loop?

```
while read site; do 
    something $site
done <block.list
```

Excellent, it worked, thanks a lot!

BTW -- do you know a good tutorial on bash scripting? and do you know how to break a single script command line into several lines for editing purposes, thanks!

---

### Post by kabus on 2006-07-22
> **ssalman said:**
> 
BTW -- do you know a good tutorial on bash scripting?


These two are essential reading:

[http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html)
[http://tldp.org/LDP/abs/html/index.html](http://tldp.org/LDP/abs/html/index.html)

> **ssalman said:**
> 
 and do you know how to break a single script command line into several lines for editing purposes, thanks!

Add a \ at the point were you want to break up the line.

---

### Post by ssalman on 2006-07-22
Thanks, kabus for all your help.

---


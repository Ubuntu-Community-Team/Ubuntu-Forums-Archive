---
title: "[SOLVED] NMap Explain"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by phoenix_abhi on 2008-05-25
How the NMap works in Ubuntu ? What is the use of it, I heard that it is for scanning the open ports, is it possible to close the open ports using NMap ?

I have installed it by apt-get, but where I will find it in my computer? I can not see any launcher for it ? 

:confused:

---

### Post by spiderbatdad on 2008-05-25
nmap is a command line program. You can install nmap-fe a graphical frontend installs a launcher in the main menu.

---

### Post by Joeb454 on 2008-05-25
You should be aware that some governments see Nmap as an illegal utility.

I think there's talk of the UK passing law against its use :( Still, I don't use it anymore after I finished setting up my server ;)

---

### Post by phoenix_abhi on 2008-05-25
> **spiderbatdad said:**
> nmap is a command line program. You can install nmap-fe a graphical frontend installs a launcher in the main menu.
 I do not under stand, what is that ?

It is not illegal here

---

### Post by Monicker on 2008-05-25
> **phoenix_abhi said:**
> I do not under stand, what is that ?

It is not illegal here

[http://nmap.org/book/man.html]("http://nmap.org/book/man.html")

[http://nmap.org/zenmap/]("http://nmap.org/zenmap/")


Zenmap is now the official gui for nmap.  Its also in the Ubuntu repos for Hardy.

---

### Post by phoenix_abhi on 2008-05-25
But after installing where it goes ? There is no launcher available ? I do not know how to create one .

---

### Post by Monicker on 2008-05-25
> **phoenix_abhi said:**
> But after installing where it goes ? There is no launcher available ? I do not know how to create one .

Nmap is a command line application.

Applications -> Accessories -> Terminal


```
nmap -h
```

If you want a gui front end for nmap, install zenmap.

---

### Post by bwhite82 on 2008-05-25
Like all good network testing tools, NMAP can be used for nefarious activities as well. It is primarily a tool used for gathering information. The man page has a lot of information:

> man nmap

---

### Post by phoenix_abhi on 2008-05-25
by this command nmap -h help shows up in terminal. But I have installed zenmap. I can not find it in my application or system menus.

---

### Post by bwhite82 on 2008-05-25
Hit ALT+F2 and type: zenmap into the box, click run.

---

### Post by t0p on 2008-05-25
> **phoenix_abhi said:**
> by this command nmap -h help shows up in terminal. But I have installed zenmap. I can not find it in my application or system menus.

If you want to run a program, typing its name into terminal will start it.

---

### Post by phoenix_abhi on 2008-05-25
My own scan shows all 1714 ports closed. conn-refused. Am I secure ?

---

### Post by bwhite82 on 2008-05-25
> **phoenix_abhi said:**
> My own scan shows all 1714 ports closed. conn-refused. Am I secure ?

Thats how Ubuntu comes by default and it is pretty secure that way. No ports open == no ports available for exploitation.

---

### Post by unutbu on 2008-05-25
When I run
```

world@peace:~% nmap -T Aggressive -A -v localhost
world@peace:~% nmap -T Aggressive -A -v peace
```

The output is different, even though (I thought) peace and localhost were the same. localhost shows CUPS and MySQL ports are open, while peace has them closed.
How can this be?

---

### Post by Monicker on 2008-05-25
mysql and cups only listen on localhost by default.  What does peace resolve to?

```
host peace
```

---

### Post by unutbu on 2008-05-25
Ah. peace resolves to 192.168.1.46,
while localhost is 127.0.0.1.

---


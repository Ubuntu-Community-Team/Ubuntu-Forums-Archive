---
title: "The Bare Essentials"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by robertwhittaker on 2008-04-29
Just a quick question that will probably solicit a longer answer...

How do I make sure that I only have installed what I want to have installed?

If I install something using apt-get is there any easy way to compile a list of all the install applications and their uses?

Many thanks
Rob

---

### Post by aheckler on 2008-04-29
Umm, what you could do is go through the Add/Remove Programs application and see what's checked and what isn't.

Or if you want something *really* detailed, this will output a list of ALL installed packages to your desktop:

```
dpkg --get-selections > ~/Desktop/packages.txt
```

---

### Post by Monicker on 2008-04-29
> **robertwhittaker said:**
> Just a quick question that will probably solicit a longer answer...

How do I make sure that I only have installed what I want to have installed?

If I install something using apt-get is there any easy way to compile a list of all the install applications and their uses?

Many thanks
Rob

From a terminal:

```
dpkg -l
```


That will show all the installed packages on your system, along with a brief description of it.

---

### Post by robertwhittaker on 2008-04-29
> **Monicker said:**
> From a terminal:

```
dpkg -l
```


That will show all the installed packages on your system, along with a brief description of it.

I was wondering if either of you (or someone else) could help me further

I've attached a list of all the packages

How do I determine what I require and what I don't?

I'm on a relatively new installation and have been experimenting with what I could do with Linux/Ubuntu

I don't want to end up with a load of things I'll never use again

Many thanks
Rob

---

### Post by aheckler on 2008-04-29
Well Ubuntu ships with some software, but it is essentially a "bare bones" system. As long as you don't go installing random programs, then you should be OK.

---

### Post by robertwhittaker on 2008-04-29
> **aheckler said:**
> Well Ubuntu ships with some software, but it is essentially a "bare bones" system. As long as you don't go installing random programs, then you should be OK.

I'll leave it then and just watch what I install in the future as I start to use Ubuntu more

Thanks for helping though
Rob

---

### Post by sailor2001 on 2008-04-29
go to your package manager (synaptics) and click 'status' 'installed'

---

### Post by eriqjaffe on 2008-04-29
If you **really** want to ensure a bare-bones installation...

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---


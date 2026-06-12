---
title: "[SOLVED] Update question"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by Primefalcon on 2008-06-24
I went to check for updates to Ubuntu today, and today I have an update that's greyed out, I don't exactly know what that means.

Here's a screenshot
[IMG]http://img47.imageshack.us/img47/8011/updatefi1.png[/IMG]

---

### Post by Primefalcon on 2008-06-24
I checked synaptic and there is an update so I guess I'll just do it through that, but why the grey out? is there an update bug?

---

### Post by talsemgeest on 2008-06-24
It means that your computer can not install the update.

Do you have unsupported updates ticked in your sources?

---

### Post by Primefalcon on 2008-06-24
is says theres unresolved dependancies but , there was no packages listed under broken..... what do I do?

---

### Post by Primefalcon on 2008-06-24
no just important and recommended

---

### Post by gtdaqua on 2008-06-24
On the terminal type this to repair any broken installations:

```

sudo apt-get install -f

```

and then try:

```

sudo apt-get update
sudo apt-get upgrade -f

```

---

### Post by Primefalcon on 2008-06-24
> **gtdaqua said:**
> On the terminal type this to repair any broken installations:

```

sudo apt-get install -f

```

and then try:

```

sudo apt-get update
sudo apt-get upgrade -f

```
nope didn't work

---

### Post by gtdaqua on 2008-06-24
> **Primefalcon said:**
> nope didn't work

Pl post the output of those commands. It will be helpful. 

Also pl post whats in your "/etc/apt/sources.list"

```

cat /etc/apt/sources.list

```

---

### Post by Primefalcon on 2008-06-24
ok I uninstalled and went to install tghe latest and now I'm getting this

oggconvert:
  Depends: python-central (>=0.6.7) but 0.6.5ubuntu1 is to be installed


I checked that package and it says 0.6.5 is the latest one :-S

So I think I found the problem

---

### Post by Primefalcon on 2008-06-24
So I guess I have to wait now till a newer version of python is released lol

---

### Post by Dutch70 on 2008-06-24
I have the same problem! Would you mind posting what the problem was and the solution?

Update: The python-central update came through for me today, and the originally greyed out update (oggconvert) was able to go through.

---

### Post by Primefalcon on 2008-06-24
I see python is released now myself, so I updated that, so I guess the only problem with that was the oggconvert was updated before the python central was....

well that definitely solves the problem I'm gonna mark this as solved since that python central update solved the problem

---

### Post by avtolle on 2008-06-24
A general note to anyone reading; if the update is grayed out, that usually means it cannot be installed until one or more dependencies are updated, too. Just "cool your jets", and in time, all will work out.

---

### Post by Primefalcon on 2008-06-24
yeah I've been using ubuntu for about 7-8 months, and thats the firs time that's happened to me

---


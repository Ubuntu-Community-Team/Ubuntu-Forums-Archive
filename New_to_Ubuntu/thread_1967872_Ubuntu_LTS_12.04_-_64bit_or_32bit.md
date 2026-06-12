---
title: "Ubuntu LTS 12.04 - 64bit or 32bit?"
date: 2012-04-28
forum: New to Ubuntu
---

### Post by georgy1 on 2012-04-28
Hello!

Why is recommended to install the 32bit version? 
And why is the Ubuntu LTS 12.04-CD available in 32bit only?

I'd rather install by a CD, but my PC is 64bit. - 
What is better for me - 
to download the 64bit version on an external harddisc or to install by the 32bit-CD?

georgy1 ... :???:

---

### Post by Monotoko on 2012-04-28
Hi georgy1,

The main difference is the amount of memory you can use at once, if you have less than 3.2GB of RAM you can go for 32 or 64 (if your CPU supports it) and it won't make much difference. Otherwise, go for 64bit and you'll feel the difference in speed and performance, once you have more than 4GB of RAM the other features of the 64bit architecture start to show.

There's a nice list of the features/advantages and disadvantages of both here: [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by Rodney9 on 2012-04-28
Go to [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
and click the 'Choose Your Flavour' select 64bit.

Rodney

---

### Post by Zukaro on 2012-04-28
I'd assume the 32bit version is recommended because most programs are made for 32bit operating systems (currently anyways).  If your computer is 64bit you should use the 64bit version (I think so anyways).  I tried to use the 32bit version on my 64bit machine and it wouldn't run; but the 64bit version runs fine.

So if you have a 64bit machine go with the 64bit OS, and if you have a 32bit machine go with the 32bit OS.  I'm pretty sure the 64bit version will run 32bit programs just fine, so it doesn't really make much of a difference (not sure though).

---

### Post by PhantomTurtle on 2012-04-28
I started using the amd64 version of Ubuntu 12.04 and it works great. This is the first time I have ever used an amd64 version of Ubuntu. I have only 3.4GB RAM and it works great. I would recommend 64-but if your processor supports it.

---

### Post by naggu on 2012-04-28
Sorry to hijack but I am not sure which version I downloaded and installed. How do I check I got 32 or 64-bit ?

---

### Post by Monotoko on 2012-04-28
Hi naggu, just hit ctrl+alt+T and type "uname -p"

It will give you a string, in there will be "x86_64" (64 bit) or i586 (or something similar - which means 32 bit)

---

### Post by Cavsfan on 2012-04-28
This is the hundredth+ time this has been asked. If you have a 64 bit machine, select 64 bit OS.
This thread will be merged with the other mega thread asking the same question.

Sorry it is so confusing! I have a 64 bit machine and have both windows 7 and Ubuntu 64 bit for over three years now.
It works great!

---

### Post by georgy1 on 2012-04-28
> **Monotoko said:**
> 
There's a nice list of the features/advantages and disadvantages of both here: [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

:-D ... Thank You for this prompt help

---

### Post by Cavsfan on 2012-04-28
Enter this in a terminal and it will return either 32 or 64.

```
getconf LONG_BIT
```

---

### Post by georgy1 on 2012-04-28
> **Rodney9 said:**
> Go to [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
and click the 'Choose Your Flavour' select 64bit. 

@ All - Thanks for this discussion - I've got it!

;)

---


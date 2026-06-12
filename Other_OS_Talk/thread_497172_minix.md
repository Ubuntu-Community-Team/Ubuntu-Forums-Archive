---
title: "minix"
date: 2007-07-09
forum: Other OS Talk
---

### Post by mr.farenheit on 2007-07-09
i have an old crappy notebook with low system specs and was thinking about giving the MINIX OS a try. anybody have any comments?

---

### Post by bread eyes on 2007-07-10
Don't waste your time.

---

### Post by kevCast on 2007-07-10
I don't know a lot about Minix besides it uses a microkernel apposed to a monolithic kernel. If the specs are low on your laptop, you could just do a barebones install Ubuntu install.

[http://www.psychocats.net/ubuntu/minimal]("http://www.psychocats.net/ubuntu/minimal")

---

### Post by jrusso2 on 2007-07-10
Give it a try but don't expect to be able to do much with it.  There are not many applications for it. And not many drivers

---

### Post by mips on 2007-07-10
Depends on what you want to do with the laptop. What are the specs of the laptop ???

I would try something else before going down the minix road as you cant really do that much with it. More educational than anything else if you ask me.

---

### Post by angryfirelord on 2007-07-10
I tried minix, but I couldn't figure out how to load the GUI (startx didn't work). Not to mention that there's no wireless drivers, 3D drivers, applications, etc.

If you want something lightweight, use a basic Debian install and apt-get only what you need.

---

### Post by mr.farenheit on 2007-07-10
bummer a lot of negative feedback. guess i'll try something else

---

### Post by LaRoza on 2007-07-11
Zenwalk is a great OS for a computer with low specs. I installed it on a computer with 64 MB of RAM, fine.

---

### Post by init1 on 2007-07-13
> **mr.farenheit said:**
> bummer a lot of negative feedback. guess i'll try something else
Yeah, I tried to install it, but it didn't recognize my hard drive. That's pathetic...

---

### Post by angryfirelord on 2007-07-13
> **init1 said:**
> Yeah, I tried to install it, but it didn't recognize my hard drive. That's pathetic...
Hard to believe that Tanenbaum still doesn't like Linux. Here's a very old, but interesting flamewar between him and Torvalds: [http://www.oreilly.com/catalog/opensources/book/appa.html](http://www.oreilly.com/catalog/opensources/book/appa.html)

---

### Post by kellemes on 2007-07-20
> **mr.farenheit said:**
> bummer a lot of negative feedback. guess i'll try something else

Rather silly to follow the crowd don't you think? You're a sheep, or what?

Use Minix on a VM to get a feel, although the current version of Minix is not ready for production as far as I know.

---

### Post by jonaOS on 2007-07-20
Dudes you're all losers, minix3 is so easy to install specially in low specs machines. Currently I'm running it in Debian Etch 4.0r0 with qemu. If you want GUI then install it with packman command, without sources installation would require only 408 Mb of hard disk. I think it's a good way to bring to life some old computers that nobody use. I don't want to hurt your feelings with the losers thing...
Chau, learn some spanish it's the future!

---

### Post by mips on 2007-07-21
> **jonaOS said:**
> Dudes you're all losers

Hmm, another l33t hacker calling other names.

---

### Post by NumberOne on 2007-07-21
You should give "Puppy" a look see.

---

### Post by angryfirelord on 2007-07-22
> **jonaOS said:**
> Dudes you're all losers, minix3 is so easy to install specially in low specs machines. Currently I'm running it in Debian Etch 4.0r0 with qemu. If you want GUI then install it with packman command, without sources installation would require only 408 Mb of hard disk. I think it's a good way to bring to life some old computers that nobody use. I don't want to hurt your feelings with the losers thing...
Chau, learn some spanish it's the future!
Yes, but what about package management? Number of packages? I usually recommend something like Puppy, DSL, or Debian for old machines.

---

### Post by init1 on 2007-07-22
Edit:
I've got Minix running on my laptop now. It's rather interesting, but not very practical yet.

---

### Post by init1 on 2007-11-10
> **angryfirelord said:**
> Yes, but what about package management? Number of packages? I usually recommend something like Puppy, DSL, or Debian for old machines.
There aren't may packages yet, and the package manager doesn't remove packages.

---

### Post by SunnyRabbiera on 2007-11-10
> **angryfirelord said:**
> Hard to believe that Tanenbaum still doesn't like Linux. Here's a very old, but interesting flamewar between him and Torvalds: [http://www.oreilly.com/catalog/opensources/book/appa.html](http://www.oreilly.com/catalog/opensources/book/appa.html)

well from what I have heard they have reconciled a bit over the last few years, the argument was mainly over minix not being open up until now, but with Minix now under GPL its changing its tune.
I heard linus was going to backport his stuff to minix too thanks to its new open license.

---

### Post by uwishurockedthishxc on 2007-11-11
puppy linux or damn small linux would be better options imho

---

### Post by dsiembab on 2008-05-15
I know this is an old thread, but after reading th flamewar between the two it seems to me that a microkernel would be the way to go, but everything always looks good on paper, When linux first started out it didn't have all the repositories that it does now and syaing that I know minix is about as old as linux, it just doesn't have the same following. I am just basically going to try minix, on my computer i have no fear. It's not that minix doesnt like linux it's that they have two different opinions on the matter of operating system architecture.

---


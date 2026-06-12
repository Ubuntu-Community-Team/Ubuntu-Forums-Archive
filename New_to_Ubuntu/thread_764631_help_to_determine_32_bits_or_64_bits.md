---
title: "help to determine 32 bits or 64 bits"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by timo_01 on 2008-04-24
hi all
i want to know if my computer is a 32 or 64 bits for future reference on downloading the right cd's.
Computer specs:

acer aspire 9300
AMD turion 64x2 mobile technology TL 50
(1.6 Ghz, 2 x 256KB l2 cache)
120 HDD
2 GB DDR2

If it's 64 bits,can i run a 32bit cd/programs in it?
thank you.

---

### Post by kpkeerthi on 2008-04-24
Your CPU is 64-bit. 

You can install [Ubuntu AMD64]("http://releases.ubuntu.com/releases/8.04/ubuntu-8.04-rc-desktop-amd64.iso") if you want to have all programs 64 bit. You cannot run 32 bit programs in a pure 64-bit environment (Exception! 32 bit flash has been hacked to work in 64-bit ubuntu as there is no native version available yet). There is no native 64-bit Sun Java plugin available yet. 

You can also install [Ubuntu i386]("http://releases.ubuntu.com/releases/8.04/ubuntu-8.04-rc-desktop-i386.iso"). Then all your packages will be 32 bit. You cannot run 64-bit programs in a 32-bit environment.

---

### Post by frup on 2008-04-24
Both 64 and 32bit should work although 64bit should be better for tasks like encoding etc. 64bit should have no problems and 32bit like flash are trivial to get working.

---

### Post by nbv4 on 2008-04-24
In my experience, you should just go with 32 bit. I've been using various 32bit and 64bit ubuntu's for the past few years, and let me tell you, the 32 bit ones give me way less headaches.

With a 64bit distro, many things will work, but every once in a while, you'll come across a library or something that only works in 32 bit, causing crap to break.

Some time in the future, 64bit will become standard, and it'll get a lot better, but until that day, stick to 32bit, unless you're running a server or something and can really use the extra performance.

---

### Post by hyper_ch on 2008-04-24
there are only a few things left where 32bit is still recommended.. flash and java can be made work on 64bit...

depending on what you need/want go with 64bit

---

### Post by misfitpierce on 2008-04-24
64 bit Ubuntu works fine for me. Java and Flash work perfectly. Never a problem since Ubuntu 7.10. 8.04 has given me 0 problems as well.

---

### Post by timo_01 on 2008-04-24
> **misfitpierce said:**
> 64 bit Ubuntu works fine for me. Java and Flash work perfectly. Never a problem since Ubuntu 7.10. 8.04 has given me 0 problems as well.

thank you all for your support..
well,i think am going to give 64bit a try......

---

### Post by FredB on 2008-04-24
> **kpkeerthi said:**
> Your CPU is 64-bit. 

You can install [Ubuntu AMD64]("http://releases.ubuntu.com/releases/8.04/ubuntu-8.04-rc-desktop-amd64.iso") if you want to have all programs 64 bit. You cannot run 32 bit programs in a pure 64-bit environment (Exception! 32 bit flash has been hacked to work in 64-bit ubuntu as there is no native version available yet). There is no native 64-bit Sun Java plugin available yet. 

WRONG ! There is now a java plugin for Mozilla Firefox with OpenJDK.

> You can also install [Ubuntu i386]("http://releases.ubuntu.com/releases/8.04/ubuntu-8.04-rc-desktop-i386.iso"). Then all your packages will be 32 bit. You cannot run 64-bit programs in a 32-bit environment.

And only using half of the power of your computer.

---

### Post by kpkeerthi on 2008-04-24
Ofcourse there is OpenJDK plugin (IcedTea project). But I think I mentioned **Sun** Java plugin in my post.
> There is no native 64-bit **Sun** Java plugin available yet.

---

### Post by Canis familiaris on 2008-04-24
Am I misktaken or can 32bit programs can run natively on x86-64 using chroot environment.

---


---
title: "Wine and Mono Question"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by jraulgp on 2011-11-01
Hello there, I'm new with Ubuntu, I'm trying to test a Aplication that relies on Dot.net Framework. (1, 2, 3.5 and 4). I don't even know if I can install Dot Net in Ubuntu, I've been reading I can install some versions using Wine, also that Mono is like the equivalent version of dot.net.
Bottom line I need dot.net frame work (all the versions) in order to run my application, so what can I do?
is Mono a equivalent?
 
I am using Ubuntu 10.04 LTS
 
Can I install dot net throug wine.
 
Any help really appreciatted.
 
Thanks

---

### Post by 11jmb on 2011-11-01
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2586](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2586)

It looks like 2.0 and earlier do pretty well on Wine, but later versoins do not.

Mono claims to support all versions up to 4.0, but I have heard mixed reviews, having never tried it myself.

---

### Post by Tarast on 2011-11-01
Mono is ok but it is nowhere near as good as ms visual studio, i am programming c# in mono but some console commands are not supported for example Console.ReadLine() would not work it doesnt read input from the user, there are also other ut if it is really big application that u building i am afraid you cant do it in linux you need windows platform to accomplish that

---

### Post by Mark Phelps on 2011-11-02
> **jraulgp said:**
> Hello there, I'm new with Ubuntu, I'm trying to test a Aplication that relies on Dot.net Framework.
Thanks

Then ... you should be doing that in Windows, not in Linux.

Let's say your test doesn't work right.  Is that a problem with your code? Or a problem with how well Wine emulates the Windows infrastructure?

In Linux, there's really no way to know for sure because some kind of emulation is required to run Windows programs.

Developers need to test their apps in their NATIVE environments -- that's the only way you'll know for sure that it works.

---

### Post by fantab on 2011-11-02
> **jraulgp said:**
> hello there, i'm new with ubuntu, i'm trying to **test a aplication** that relies on dot.net framework. (1, 2, 3.5 and 4).

> **mark phelps said:**
> then ... You should be doing that in windows, not in linux.

Let's say your test doesn't work right.  Is that a problem with your code? Or a problem with how well wine emulates the windows infrastructure?

In linux, there's really no way to know for sure because some kind of emulation is required to run windows programs.

**developers need to test their apps in their native environments -- that's the only way you'll know for sure that it works.**

+1.

---

### Post by jraulgp on 2011-11-02
Thanks all for you reply, 
I know my application runs in Windows, but I want to know if it can be implemented in Linux.
 
I will keep reading.
 
Thanks again.

---

### Post by Mark Phelps on 2011-11-02
> **jraulgp said:**
> Thanks all for you reply, 
I know my application runs in Windows, but I want to know if it can be implemented in Linux.

Using .Net?  Probably not.

If you want to write cross-platform apps, you need to look into programming languages and environment that span platforms.  Choosing one that is known to be Windows-specific is not a good start.

---


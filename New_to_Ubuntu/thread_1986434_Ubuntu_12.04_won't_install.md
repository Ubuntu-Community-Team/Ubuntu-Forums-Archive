---
title: "Ubuntu 12.04 won't install"
date: 2012-05-24
forum: New to Ubuntu
---

### Post by deported on 2012-05-24
So I am brand new to the whole Linux world and I decided I'd take a stab at using Ubuntu 12.04 as my OS for a new computer build. 

I made a LiveCD, inserted it into my optical drive, and changed the BIOS to read the Optical Drive first and reset my system. 

I can get Ubuntu to open to a page with the following selections: Try Ubuntu without installing, Install Ubuntu, Check disc for defects, Test memory, and Boot from first hard disk.

No matter what I choose, the screen blacks out for a few seconds and then shows nasty looking white and colored stripes across my monitor then my monitor cuts off. 

I hear that Linux users are the best computer users out there and so I'd really appreciate it if someone could help me solve my problem. Thanks! ::eek:

---

### Post by carl4926 on 2012-05-24
> I can get Ubuntu to open to a page with the following selections: Try  Ubuntu without installing, Install Ubuntu, Check disc for defects, Test  memory, and Boot from first hard disk.At here

try pressing F6
and select: nomodeset
hit enter

does that help

---

### Post by deported on 2012-05-24
You are a saint. 

If you don't mind me asking, why wouldn't it work before that and what does selecting nomodeset actually do?

But really, you are awesome. 

:guitar: <---You

---

### Post by lilmagnus on 2012-05-24
Welcome deported! We're here to help.

Have you run the "Check disc for defects". That will determine if you should burn another boot CD but at a slower speed.

Next, can you provide particuars about your computer? Model? Graphics card model and/or chipset?

EDIT: A little late to the party. Glad you got it working.

---

### Post by deported on 2012-05-24
Yeah, everything is up and running now but thanks for the reply anyway magnus.

Just curious, any idea if Ubuntu 12.04 can run Diablo 3? I just got the game and am considering adding it to this build if it will work.

---

### Post by carl4926 on 2012-05-24
Kernel modesetting is enable by default, it's there to help really

With KMS, a simple default policy is loaded into the kernel for initial  output setup, which means connected displays should go to their native  resolution as early as possible

But not all hardware (your graphics device) is so good with it
nomodeset turns it off and should get you to some kind of desktop to be able install the graphics driver

---

### Post by carl4926 on 2012-05-24
> **deported said:**
> Yeah, everything is up and running now but thanks for the reply anyway magnus.

Just curious, any idea if Ubuntu 12.04 can run Diablo 3? I just got the game and am considering adding it to this build if it will work.

Look here
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=13484](http://appdb.winehq.org/objectManager.php?sClass=application&iId=13484)

looks good

---

### Post by deported on 2012-05-24
Carl you are just full of useful information. lol

Thanks again for all the help, I really appreciate it. :)

---

### Post by carl4926 on 2012-05-25
> **deported said:**
> Carl you are just full of useful information. lol

Thanks again for all the help, I really appreciate it. :)
Enjoy

You are most welcome

---


---
title: "Problem installing programs"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by charlesdb on 2008-11-27
OK, I know this has been in an old thread - but as it was an old thread, I'd like to revive the question.  I've just installed Ubuntu 8.1 intrepid ibex via wubi on my Dell Vostro 200, xp professional service pack 3 32bit (having previously been getting an error message during boot up from an Ubuntu 8.0 CD). 
I tried to install the latest version of Opera and got a message wrong architecture i386. This also happened when I tried to install a couple of other programs.  I know the answer to the previous posts was 
"as far as I know opera is not available for 64bit.  As you can see in the error you tried to install the 32bit version of opera".

As I'm running on 32bit this answer does not apply to me.

Can you please help me.  And if it means adding some code somewhere, can you please be specific as to where to add it, on a step by step basis, as some answers skip vital steps, by assuming knowledge which new users do not have.  Thanks.

---

### Post by flanagan on 2008-11-27
Your post says you have XP 32-bit which is irrelevant here as long as you are trying to install under Ubuntu. Are you sure you have Ubuntu 32-bit and not 64-bit?

P.S.> In any case, try this:

[http://blog.isnotworking.com/2007/11/opera-9-on-ubuntu-with-amd64.html](http://blog.isnotworking.com/2007/11/opera-9-on-ubuntu-with-amd64.html)

---

### Post by charlesdb on 2008-11-27
Aha!  You may be right. I'll get back.

---

### Post by hyper_ch on 2008-11-27
I don't think there will be a 64-bit wubi install within a 32-bit winxp os...

how do you try to install opera?

---

### Post by charlesdb on 2008-11-27
OK, because I was having problems with Ubuntu 8.0 and the Dell Vostro machine, which seems quite common, I installed via Wubi.  I've now uninstalled this program and reinstalled Ubuntu 8.1 from a CD which was sent to me, the latest version.  I've been able to install Opera now without problems.
I'm not a tech person, although not bad with computers - and if problems are likely to occur because of the architecture within the download, I do think it would be a good idea for those responsible for offering the download, to make new users aware.
In any case, I'm happy now.

---

### Post by Paqman on 2008-11-27
> **charlesdb said:**
> 
As I'm running on 32bit this answer does not apply to me.


You can double-check whether you're running 32 or 64-bit by putting this into a terminal window:
```
uname -m
```

> **hyper_ch said:**
> I don't think there will be a 64-bit wubi install within a 32-bit winxp os...


There will actually. Wubi always downloads a 64-bit disk image if you have a chip that can run it.

---

### Post by Nitrosyncretic on 2008-11-27
I got the Wrong Architecture error while trying to install Skype just now. This is the second software package that's given me this error.

I just ran uname and got "x86_64" which I assume means I have the 64-bit install. I have a Dell Vostro 1500. I installed Ubuntu 8.10 with Wubi.

How do I resolve this? Do I have to uninstall my current 64-bit version of Ubuntu and install the 32-bit version? How would I do that with Wubi?

---

### Post by hyper_ch on 2008-11-27
install skype from the medibuntu repos.

---


---
title: "Im looking for a distro to learn from"
date: 2008-06-24
forum: Other OS Talk
---

### Post by MONODA on 2008-06-24
so far i have tried:Debian (I dont see the purpose of keeping year old packages in a distro, many times newer versions have less bugs.), Slackware (I dont see the point of having to install all software and deps manually), Arch (I love this and use it as my main distro), FreeBSD (could not detect the correct geometry on my laptop), netBSD (it just won install) and a few others I dont remember. What do you recommend that I try that I can learn from? thanks.

---

### Post by erginemr on 2008-06-24
I'd say Slackware or Gentoo as the two great teachers. Since you have ruled out Slackware, you should try Gentoo.

---

### Post by mips on 2008-06-24
Arch Linux.


[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)  Follow this to the letter and you will be ok.
[http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide](http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide)
[http://www.archlinux.org/](http://www.archlinux.org/)
[http://wiki.archlinux.org/index.php/Main_Page](http://wiki.archlinux.org/index.php/Main_Page)

---

### Post by sujoy on 2008-06-24
he is already using arch, and since he isn't particularly interested in slackware so i guess it comes to either gentoo , debian or LFS.

as for debian, use testing if you want recent versions of apps or debian unstable aka Sid if you want bleeding edge. debian is for everyone :)

---

### Post by atomkarinca on 2008-06-24
What about [OpenSolaris]("http://opensolaris.org/")?

---

### Post by eldragon on 2008-06-24
the missing question is: what do you want to learn?

---

### Post by MONODA on 2008-06-24
I was kind of expecting a reason why slackware's not having a package manager is a + lol... I have tried debian etch, lenny, sidux it wasnt much of a learning experience. I plan on trying LFS but not Gentoo, I dont want to wait 2 days for things to compile. But I will install CRUX which is like archgentoo :p. I am trying to find a way to get netbsd to install and freebsd to detect the corrent geometry for my drive. I really wanna try both out. But my dream distro is pretty much arch, the one thing I dont like is the linux kernel :p too many bugs for my liking.

---

### Post by maybeway36 on 2008-06-24
openSUSE is a good distro to try.

---

### Post by cardinals_fan on 2008-06-24
> **MONODA said:**
> I was kind of expecting a reason why slackware's not having a package manager is a + lol... I have tried debian etch, lenny, sidux it wasnt much of a learning experience. I plan on trying LFS but not Gentoo, I dont want to wait 2 days for things to compile. But I will install CRUX which is like archgentoo :p. I am trying to find a way to get netbsd to install and freebsd to detect the corrent geometry for my drive. I really wanna try both out. But my dream distro is pretty much arch, the one thing I dont like is the linux kernel :p too many bugs for my liking.
You learn about the system from handling package management yourself.  In any case, learning generally involves some pain.  An OS that "just works" isn't going to teach you much, is it?

EDIT: Whoa!  600th post!

---

### Post by RedSquirrel on 2008-06-24
> **MONODA said:**
> I plan on trying LFS but not Gentoo, I dont want to wait 2 days for things to compile. 

You'll be waiting for a while for things to compile with LFS too. That's the reason it's called Linux *From Scratch*. :)


> **MONODA said:**
> But my dream distro is pretty much arch, the one thing I dont like is the linux kernel :p too many bugs for my liking.

Do you mean the *Arch Linux* kernel? Have you tried compiling a custom kernel?

---

### Post by RedSquirrel on 2008-06-24
> **cardinals_fan said:**
> EDIT: Whoa!  600th post!

Congratulations! Now we wait for #666. :evil:

---

### Post by cardinals_fan on 2008-06-24
> **RedSquirrel said:**
> Congratulations! Now we wait for #666. :evil:
I'm possessed :twisted:

---

### Post by MONODA on 2008-06-25
> You'll be waiting for a while for things to compile with LFS too. That's the reason it's called Linux From Scratch.
yes I realize that but gentoo has a lot of stuff I will choose not to include in my installtion of LFS so it will take less time.
> Do you mean the Arch Linux kernel? Have you tried compiling a custom kernel? no I dont mean the arch linux kernel, arch uses the vanilla kernel. What I mean is that I am jealous of the MINIX 3 and NetBSD kernels :p

---

### Post by mikjp on 2008-06-25
> **MONODA said:**
> FreeBSD (could not detect the correct geometry on my laptop)- - - What do you recommend that I try that I can learn from? thanks.

You might try to learn to configure xorg used by FreeBSD. FreeBSD has great manuals to study and learn from, see the FreeBSD handbook:

[http://www.freebsd.org/doc/en/books/handbook/](http://www.freebsd.org/doc/en/books/handbook/)

You will find shorter articles here:

[http://www.freebsd.org/news/press.html](http://www.freebsd.org/news/press.html)

I especially liked Dru Lavignes articles. Just google her name!

Greetings,

Mikko

---

### Post by Twitch6000 on 2008-06-26
I think the question we need answered is what are you trying to learn?
If it is about Linux itself then Arch,Gentoo,Slackware,and LFS are all great choices.
If it about different environments then try different distros.

---

### Post by RedSquirrel on 2008-06-27
> **MONODA said:**
> yes I realize that but gentoo has a lot of stuff I will choose not to include in my installtion of LFS so it will take less time.

What are you planning to exclude?

---

### Post by Rotaj on 2008-06-27
If you want a distro to learn from, try [Kurumin]("http://translate.google.com/translate?u=http%3A%2F%2Fwww.gdhpress.com.br%2Fkurumin%2F&sl=pt&tl=en&hl=en&ie=UTF-8"). Probably won't learn anything new about linux, but you probably will learn a little Brazilian Portugese.:lolflag:

---

### Post by MisfitI38 on 2008-06-28
The best way to learn gnu/linux, imo, is to read the LFS book. 
*Using* it is more involved, but you may want to try that also. Reading it will give you a good overview of what the system is made of, and how it fits together into a whole.

---

### Post by basenvironment on 2008-06-30
> **MONODA said:**
> Debian (I dont see the purpose of keeping year old packages in a distro, many times newer versions have less bugs.)
so use lenny/sid and if you want something even more volatile add in the experimental repo and occasionally browse [http://incoming.debian.org/](http://incoming.debian.org/) to see what hot new stuff you might want to try

debian is whatever you make of it...

---


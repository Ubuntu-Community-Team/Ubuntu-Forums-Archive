---
title: "learn Linux programming"
date: 2008-08-14
forum: Programming Talk
---

### Post by ryclegman on 2008-08-14
Hello,

I was wondering if there was a program out on the internet or something that could teach you how to Program a Linux, create a distro and things like that.
I would like to learn but don't know where to start...

---

### Post by Kadrus on 2008-08-14
Ive posted on the other thread but here it goes anyway.
[RockLinux]("http://www.rocklinux.org/wiki/Main_Page"):ROCK Linux is a Linux distribution Build Kit.It was created for making your own Linux distributions.
[LinuxFromScratch]("http://en.wikipedia.org/wiki/Linux_From_Scratch"):Linux from scratch..read it
there is a tool that helps you create your own distro from an iso image,i forogt its name..i will post it later.

---

### Post by ryclegman on 2008-08-14
I have been looking for a while now and i dont think you can download rock linux?

---

### Post by lisati on 2008-08-14
> **ryclegman said:**
> I have been looking for a while now and i dont think you can download rock linux?

Check out [http://www.rocklinux.org/wiki/Download](http://www.rocklinux.org/wiki/Download)

---

### Post by Kadrus on 2008-08-14
found the program again..i forgot his name.
[Reconstructor.]("http://reconstructor.aperantis.com/")

---

### Post by pmasiar on 2008-08-14
> **ryclegman said:**
> a program out on the internet or something that could teach you how to Program a Linux, create a distro and things like that.
I would like to learn but don't know where to start...

0) Always start at wikipedia and google :-)

1) there is not such a thing as "program Linux". Linux is just a kernel of operating system, most of it's utilities provided by GNU. It consists of hundreds or thousands of packages, all written in different languages.

2) Google for "how to create a linux distro", you will found dozens of guides

3) you will need to become quite expert in Linux administration, which is orthogonal to programming IMHO.

---

### Post by ryclegman on 2008-08-14
when i go to download the rock linux i get "Can't find torrent file!"

---

### Post by jimi_hendrix on 2008-08-15
> **pmasiar said:**
> 0) Always start at wikipedia and google :-)

1) there is not such a thing as "program Linux". Linux is just a kernel of operating system, most of it's utilities provided by GNU. It consists of hundreds or thousands of packages, all written in different languages.

2) Google for "how to create a linux distro", you will found dozens of guides

3) you will need to become quite expert in Linux administration, which is orthogonal to programming IMHO.

for numbers 0 and 2 i have tried this many times and found nothing...this thread is a great help btw and i bookmarked it

sorry for thread hijacking but 1 question...besided the windows manager (gnome, kde, xfce etc) and packages they come with whats the difference between distros

---

### Post by Kadrus on 2008-08-15
> for numbers 0 and 2 i have tried this many times and found nothing...this thread is a great help btw and i bookmarked it
Maybe you didn't search correctly,Google never disappoint.

> besided the windows manager (gnome, kde, xfce etc)
Those are Desktop Environments

Each distro is designed for a specific purpose(well almost each one),they differ in installation,configuration,speed,compatibility,use,package management,and philosophy.

---

### Post by jimi_hendrix on 2008-08-15
> **Kadrus said:**
> Maybe you didn't search correctly,Google never disappoint.


Those are Desktop Environments

Each distro is designed for a specefic purpose(well almost each one),they differ in installation,configuration,speed,compaibility,use,package management,and philosophy.

no acually i searched before with the exact words pmaiser said

and with the installation configuration use package managment and compatabillity thing...my friend who got me on linux uses PC linux and when i look at his it looks exactly like kubuntu

---

### Post by Kadrus on 2008-08-15
Well it's because it uses KDE.doesn't mean it's like Kubuntu.
A desktop Environment is not an OS.

---

### Post by jimi_hendrix on 2008-08-15
i realize that but other then some things like programs it comes with (like i believe it had a program to browse internet connections) i didnt see a difference

---

### Post by Kadrus on 2008-08-15
Well if a program can work in one Linux distro,it can work with all distros(most likely)..
Download Gentoo for example,install it and use it,and you will see the difference between gentoo and ubuntu.
The best way to compare a distro to others,is to install it and try it yourself.
edit:
[http://wiki.archlinux.org/index.php/Arch_vs_Others](http://wiki.archlinux.org/index.php/Arch_vs_Others)
This is a comparison of arch linux with other distributions.

---

### Post by jimi_hendrix on 2008-08-15
if i install it then i either lose one of my partitions or i have to re partition my hard drive and im running out of room...any simpilar way?

---

### Post by Kadrus on 2008-08-15
Virtual Machine.

---

### Post by slavik on 2008-08-15
different distributions call different things different names and work differently.

Some of the differences between Debian and RedHat:
- the start up is different
- Debian: apache, RedHat: httpd
- Debian: apache virtual host config, a2ensite, etc., RedHat: the old (1.3) style of doing things (single config file, etc.)
- Debian: apt/dpkg, RedHat: yum/rpm -- THIS IS THE BIG ONE!!!
- patches for packages are different

---

### Post by Kadrus on 2008-08-15
> **jimi_hendrix said:**
> no acually i searched before with the exact words pmaiser said

Well these are a few results from googling:create your own linux distro
[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)
[http://www.rpath.com/corp/](http://www.rpath.com/corp/)
[http://www-128.ibm.com/developerworks/library/os-lfs/](http://www-128.ibm.com/developerworks/library/os-lfs/)
[http://hehe2.net/linuxhowto/create-your-own-linux-distro/](http://hehe2.net/linuxhowto/create-your-own-linux-distro/)
[http://linux.slashdot.org/article.pl?sid=05/06/06/0714200](http://linux.slashdot.org/article.pl?sid=05/06/06/0714200)
[http://www.linuxjournal.com/article/7233](http://www.linuxjournal.com/article/7233)
[http://distrowatch.com/table.php?distribution=byo](http://distrowatch.com/table.php?distribution=byo)
[http://www.informationweek.com/news/software/showArticle.jhtml?articleID=205917063](http://www.informationweek.com/news/software/showArticle.jhtml?articleID=205917063)
Everyone one of these links deal with this subject.

---

### Post by jimi_hendrix on 2008-08-15
ok last thing...virtual machine...how do you do that

also when i googled what he said i got a load of things pointing  me to LFS and i believe i need a book for LFS

---

### Post by Kadrus on 2008-08-15
go to the lfs website and read the documentations(it's there to help you figure out everything you need)
[http://ubuntuforums.org/showthread.php?t=582729](http://ubuntuforums.org/showthread.php?t=582729)
read this thread above.
You can run any OS(except OS X i think,unless it's hacked,hackintosh),in a virtual box,without messing with your partition,or dual booting.

---

### Post by pmasiar on 2008-08-15
> **jimi_hendrix said:**
> no acually i searched before with the exact words pmaiser said

and you found wikipedia articles, read them, tried to follow links, and still do not understand? Including "external links" at the bottom?

Then try [http://uncyclopedia.org/wiki/Linux](http://uncyclopedia.org/wiki/Linux) maybe that  would help you :-)

BTW it is 'pmasiar' ;-)

---

### Post by jimi_hendrix on 2008-08-15
sorry about that

---

### Post by jimi_hendrix on 2008-08-15
well in that uncyclopedia link i have not found the linux programing thing yet (i am still looking though) but i have found that tux is a traitor to the penguin race due to his betray of a penguin army during the great penguin war against barny...are you sure this is a valid source of facts?

---

### Post by Kadrus on 2008-08-15
No,just funny jokes.
Never take it seriously there.
> In Russia,Linux installs you.

---

### Post by jimi_hendrix on 2008-08-15
lol...basically ive learned that penguins  + chicken nuggets > barny + bob the builder + ronald mcdonald + children

ive also learned that tux is a mortal enemy of super mega jesus...remind me to put that in my kernel code when i write it

---

### Post by pmasiar on 2008-08-15
> **jimi_hendrix said:**
> are you sure [uncyclopedia] is a valid source of facts?

Definitely NOT!

But it is fun to read, when are you bored reading real wikipedia. You did read 'Linux' and 'kernel' pages?

---

### Post by jimi_hendrix on 2008-08-16
i read the linux page and the tux page

---


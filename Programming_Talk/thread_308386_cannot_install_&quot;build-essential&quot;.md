---
title: "cannot install &quot;build-essential&quot;?"
date: 2006-11-28
forum: Programming Talk
---

### Post by Ian0107 on 2006-11-28
I have a c program compiled, it just show " stdio.h: No such file or directory". Someone said I shold install build-essential, but it just doesn't work:

~# apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential

---

### Post by blackrim on 2006-11-28
that is odd. it should work. 
in your message you have $ apt-get install build-essential but it should be $ sudo apt-get install build-essential. 
one thing you could try is $ sudo apt-get update to ensure that you repo databases are up to date and that they recognize there is a build-essential package.
could also open up synaptic and verify that there is something there for build-essential.

---

### Post by the_dragon_booster_ on 2006-11-28
Do you have to pay 4 it? :-k 

if u do i don't really wanna install it [-(

---

### Post by Ian0107 on 2006-11-28
the problem is solved.launch the  synaptic package manager & click the reload button. thank you! Actually, I have reinstall the OS before i find the solution. :KS

---

### Post by Ramses de Norre on 2006-11-28
> **the_dragon_booster_ said:**
> Do you have to pay 4 it? :-k 

if u do i don't really wanna install it [-(

Pay for software from the repositories? No way! It's all free and open ;)
(This is, as long as you don't add multiverse.)

---

### Post by steevk on 2006-11-28
Something else I'd like to ask...how did you compile a program without build-essential?

---

### Post by shining on 2006-11-28
> **steevk said:**
> Something else I'd like to ask...how did you compile a program without build-essential?

build-essential is only a metapackage, so you can build everything you want without having it installed (as long as its dependencies are installed) :

```

$ apt-cache depends build-essential
build-essential
 |Dépend: libc6-dev
  Dépend: <libc-dev>
    libc6-dev
  Dépend: gcc
  Dépend: g++
  Dépend: make
  Dépend: dpkg-dev

```

---

### Post by steevk on 2006-11-28
I guess that's my lack of knowledge speaking. Whenever I had tried to just 'sudo apt-get install gcc' it wouldn't do it, and I was pointed towards build-essential.

---

### Post by joemaller on 2006-12-10
minor footnote which might trip up some fellow newbies. Only one instance of apt-get will run at a time. Ubuntu's Update Manager uses apt-get, I'd run updates and failed to close the window before trying to install the build-essential package. Because Update Manager had an instance open, trying to run apt-get returned these not-so-helpful errors:
```

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

```
Once I realized I needed to close Update Manager before running apt-get, my installation went smoothly.

---

### Post by sheds on 2007-12-11
Quick questions here!!!

apt-get install is asking me to put in my 7.10 gutsy cd. The thing is that i installed from a rewritable and now the cd is full of music. How can i tell the apt install command to use the regular download from the internet fashion rather than use the cd?

Thanks for the help.

---

### Post by ruibernardo on 2007-12-11
Hi sheds,

click on the menu System > Administration > Software Sources. On the first tab, below, uncheck the CD-ROM. Enable the other repositories (main, restricted, universe and multiverse) if you don't have them active. Click the close button. You will be asked to update, do it.

Now the CD-ROM isn't on your sources.list file and all packages will be installed from the internet.

---

### Post by jespdj on 2007-12-11
Select System / Administration / Software Sources. Uncheck the CDROM and click Close.

*edit* Oh, I see someone else already answered that...

---


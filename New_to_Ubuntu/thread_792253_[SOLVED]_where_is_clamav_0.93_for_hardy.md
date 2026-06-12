---
title: "[SOLVED] where is clamav 0.93 for hardy?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-05-12
i installed the clamav that is in the repsitory but i got this error when i did freshclam

```

WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.92.1 Recommended version: 0.93

```

does anybody know where i can get version 0.93 for hardy?

---

### Post by SunnyRabbiera on 2008-05-12
well this is why I usually use klamav instead as it tends to handle updates better.
you should try to run clam under sudo and see if you can get updates via root access.

---

### Post by tjwoosta on 2008-05-12
> you should try to run clam under sudo and see if you can get updates via root access.

actually i was using sudo (the database updated fine with freshclam, it just says that the program itself is out of date and i should install the lates version)

i guess i should have included the entire output of freshclam, here it is
```

tj@tj-laptop:~$ sudo freshclam
[sudo] password for tj: 
ClamAV update process started at Mon May 12 19:50:25 2008
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.92.1 Recommended version: 0.93
DON'T PANIC! Read http://www.clamav.net/support/faq
main.inc is up to date (version: 46, sigs: 231834, f-level: 26, builder: sven)
daily.inc is up to date (version: 7105, sigs: 53047, f-level: 26, builder: neo)

```

as i understand klamav is only a kde frontend for clamav therefore it would probably not solve my problem of needing to install the latest version of clamav

edit: i should probably add that i am using 64bit hardy

---

### Post by SunnyRabbiera on 2008-05-12
I would not worry about it in any case, but yeh use klamav as a front end as I think its better then the other frontends to clam

---

### Post by tjwoosta on 2008-05-13
well thanks for your help sunny

but i usually dont even use a frontend for clamav, its a simple enough program to use the command line without any troubles

aslo im not really worried about it  (i realize that clamav only usually picks up windows viruses anyway)  
but i do have a windows computer on my network that i regularly exchange files with so im just trying to get the most up to date version as possible so i dont infect others on my network

(i ran a clamscan  right after my first post and i did find two virus threats right off the bat), and that is with the outdated vesion so im wondering how many more i have but cant find yet

---

### Post by tjwoosta on 2008-05-14
ok i found the source package for 0.93 at clamav.net but i am still kina newbish when it comes to compiling stuff

here are the instructions i am trying to follow
[http://wiki.clamav.net/Main/InstallFromSource]("http://wiki.clamav.net/Main/InstallFromSource")

here are my questions
> untar the source to an appropriate location. 
what is the appropriate location?

> ensure you have a user clamav and group clamav.
why do i need a dedicated user and group just for clamav?
and how would i make the user and group?

> for clamav-milter support ./configure --enable-milter
what is clamav-milter?

---

### Post by tjwoosta on 2008-05-15
anybody?

please

---

### Post by Tatty on 2008-05-15
Try these wiki pages, they should get you started

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by tjwoosta on 2008-05-15
thank you for that Tatty, but i already know that much and it doesn't answer my questions i posted above

__> 
here are my questions
[QUOTE]untar the source to an appropriate location. 

what is the appropriate location?

> ensure you have a user clamav and group clamav. 

why do i need a dedicated user and group just for clamav?
and how would i make the user and group?

> for clamav-milter support ./configure --enable-milter 

what is clamav-milter?
[/QUOTE]

---

### Post by chebe on 2008-07-21
Maybe the easiest solution is to use the latest version from ppa ...

add the following line to your sources.list :
```
deb http://ppa.launchpad.net/ubuntu-clamav/ubuntu hardy main
```

Or just follow this link :
[https://launchpad.net/~ubuntu-clamav/+archive]("https://launchpad.net/~ubuntu-clamav/+archive")

---

### Post by Ahunt on 2008-08-18
Of interest this is bug 228438 listed on Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/clamav/+bug/228438](https://bugs.launchpad.net/ubuntu/+source/clamav/+bug/228438)

The answer there in brief says:

"The version of 0.92.1 that was released with Hardy and is also available in
dapper-updates and feisty/gutsy-backports is patched with all of the
security fixes from 0.93 and is recommended for production use.

0.93 is in Intrepid and will be released with it. So far many packages
that integrate with clamav have needed to be patched to work with 0.93.
0.93 is not recommended for production use yet unless you do extensive
regression testing on your own first."

So it looks like ClamAV 0.93 will not work properly, even if you get it installed.

---


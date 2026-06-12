---
title: "Getting GUI running"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by andymic on 2008-06-30
Hi,  Firstly I'm really green on ubuntu so please forgive me if this is a stupid question.

I have downloaded and installed the 'server' version of ubuntu 8.04 LTS.

I would really like to use the desktop environment available by default on the 'desktop' version.

Does anyone have a crib sheet on what dependancies there are and what to install?

Thanks

---

### Post by ibutho on 2008-06-30
Hi. You need to run
```
audo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by fatality_uk on 2008-06-30
Dependancies will be dealt with during

---

### Post by andymic on 2008-06-30
Thanks for the speedy reply.  I'll give that a go...
:)

---

### Post by hyper_ch on 2008-06-30
why do you want a gui on a server?

---

### Post by andymic on 2008-06-30
Ummmm....
Maybe because I'm coming from windows server 2003
And because I'm finding the docs difficult to navigate.
With the GUI I can play around and hopefully learn.

---

### Post by hyper_ch on 2008-06-30
a gui on a server is useless - except if you want to use that computer as desktop also...

---

### Post by andymic on 2008-06-30
I'm sure you're right.
Can you recommend a good book or a good online doc source for a newb like me?

---

### Post by hyper_ch on 2008-06-30
not as long as I don't have a clue what kind of server you try to setup ;)

but generally you find a lot of good howtos over at [http://www.howtoforge.com](http://www.howtoforge.com)

---

### Post by andymic on 2008-06-30
well, my intention was to set up Verlihub

---

### Post by hyper_ch on 2008-06-30
I have no clue what that is :(

but here are instructions:

(always look for the debian/ubuntu commands). [http://www.verlihub-project.org/doku.php?id=installation](http://www.verlihub-project.org/doku.php?id=installation)

and for ubuntu you have to prepend "sudo" to execute soemthing also root

---

### Post by andymic on 2008-06-30
No problem.
Can you suggest any general info on ubunto server I should be reading?

Thanks

---

### Post by hyper_ch on 2008-06-30
ubuntu server installs a very basic linux system... for actually making it a "server" you need to install "server services" like apache, ssh, mysql, ftp, ....

well, not sure what I can recommend for you to read...

---

### Post by ibutho on 2008-06-30
When I started administering an Ubuntu server, I used the [Ubuntu Server Guide]("https://help.ubuntu.com/ubuntu/serverguide/C/index.html") as a reference.

---


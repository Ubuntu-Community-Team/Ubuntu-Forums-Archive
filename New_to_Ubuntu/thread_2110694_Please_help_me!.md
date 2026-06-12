---
title: "Please help me!"
date: 2013-01-30
forum: New to Ubuntu
---

### Post by 0x0099 on 2013-01-30
Hello gents,
I'm completely new to Ubuntu, I love it.
I have some question to solve, Please help me

1) How to install .tar.bz2 file
2) how to login as root

p.s.: Im using ubuntu 9.10
<EOF>

---

### Post by deadflowr on 2013-01-30
Here:

[http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-or-tar-bz2-file]("http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-or-tar-bz2-file")

And here:

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

Hope it helps.

---

### Post by elgordodude on 2013-01-30
Welcome to the forums,

Have a look here for info on tar

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

For root you can do su - at the command line or sudo to execute individual commands, sudo is the preferred way, running as root is not recommended.

Why are you on 9.10? It hasn't been supported for well over a year, before you get too involved I would install 12.04, you'll find things to be much easier, and you'll get the security updates your system should have.

---

### Post by Bucky Ball on 2013-01-30
Welcome to the forums.

Couple of points: We are not all gents here, despite the stereotype (this includes staff members, though I am a gent). 

To increase your chances of help use descriptive thread titles. This one is generic and tells us nothing and some will just move on. It can be changed by editing the first post and clicking Go Advanced. ;)

9.10 was out of support for years (October 2010) and hasn't gotten security updates since. If you are going online with this machine there will be vulnerabilities and not advisable. 

Please upgrade by a fresh install of 12.04 LTS, supported until 2017. If you don't like the Unity desktop environment (try it from the install disk first), try another flavour; Kubuntu, Lubuntu or Xubuntu (or any of a heap of others). Xubuntu is pretty close to the older releases of Ubuntu.

PS: Why would you want to log in as root? Not advisable, especially on a machine that hasn't had a security update in years ... To do things as root, become root temporarily (for that command) in a terminal by issuing 'sudo' before commands that need them. E.g.

```
sudo apt-get update
```If you try this command not much, if anything, will happen in 9.10. If you have third party repos installed you would get updates for them that probably wouldn't function on 9.10.

Good luck.
BB

---

### Post by sammiev on 2013-01-30
Oh my 9.10! Best to do a fresh install of a newer version.

---


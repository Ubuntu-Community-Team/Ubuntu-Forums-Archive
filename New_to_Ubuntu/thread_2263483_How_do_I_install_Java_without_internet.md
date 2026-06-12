---
title: "How do I install Java without internet?"
date: 2015-02-01
forum: New to Ubuntu
---

### Post by MineisCraft on 2015-02-01
title says all.

---

### Post by MineisCraft on 2015-02-01
59 views, but no one who helped yet?  :(

---

### Post by howefield on 2015-02-01
You've barely posted an hour ago, how many of your "views" do you think have been real live people and not search spiders ?

Give it some time.

---

### Post by oldos2er on 2015-02-01
It would help to clarify if you want Oracle's java, or one of the repository packages e.g. openjdk or icedtea.

---

### Post by slickymaster on 2015-02-01
[http://askubuntu.com/questions/974/how-can-i-install-software-or-packages-without-internet-offline](http://askubuntu.com/questions/974/how-can-i-install-software-or-packages-without-internet-offline)

---

### Post by MineisCraft on 2015-02-01
> **slickymaster said:**
> [http://askubuntu.com/questions/974/how-can-i-install-software-or-packages-without-internet-offline](http://askubuntu.com/questions/974/how-can-i-install-software-or-packages-without-internet-offline)
Thank you sir. ;)

> **howefield said:**
> You've barely posted an hour ago, how many of your "views" do you think have been real live people and not search spiders ?

Give it some time.
Sorry, but I'm used to getting a reply fast on forums.

---

### Post by slickymaster on 2015-02-01
You're welcome. Please don't forget to mark your thread as [SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") so other people searching the forums know that it provides a working solution for the problem.

---

### Post by protoss96 on 2015-02-02
You can download Java binaries from:
```
https://java.com/en/download/
```
If you select .tar.gz package, you can later link java binary to /usr/bin, lets say that you unpacked java 32 bit in /usr/ folder:
```
cd /usr/bin && sudo ln -s /usr/java/i386/java // Something like that
```

---

### Post by Benjamin_Eunice on 2015-02-02
afraid you simply can't unless you have a usb flash drive and somehow find a zip file, but I wouldn't try installing java with a zip unless you know what you're doing.

---


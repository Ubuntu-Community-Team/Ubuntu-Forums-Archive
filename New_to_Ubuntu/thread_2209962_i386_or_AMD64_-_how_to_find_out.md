---
title: "i386 or AMD64 - how to find out?"
date: 2014-03-08
forum: New to Ubuntu
---

### Post by Xubuntist on 2014-03-08
Hello,

I have put this in the **absolute beginners** section because I am simply good at following instructions. I am not a knowledgeable Linuxhead.

I wanted to install [Clementine music player]("http://www.clementine-player.org") to a customer's Xubuntu 13.10 laptop and when I went to the download page I was offered [a plethora of confusing options]("http://www.clementine-player.org/downloads"). So I opened a terminal and tapped 
```
uname -a && cat /etc/*release
```
The result gave me:
```
Linux *name *3.11.0-generic #32 Ubuntu SMP True Feb 18 21:11:14 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```
So, still none the wiser, is this laptop running Xubuntu AMD64 or Xubuntu i386?

Your help gratefully received.

[EDIT] in fact, to get round the problem I did
```
sudo add-apt-repository ppa:me-davidsansome/clementine 
sudo apt-get update 
sudo apt-get install clementine
```

so the problem is largely academic for this laptop, but for the future I would like to know.

---

### Post by Vladlenin5000 on 2014-03-08
i386 -> 32-bit
amd64 -> 64-bit = x86_64

---

### Post by 3rdalbum on 2014-03-08
Adding the PPA was actually the correct way to install Clementine, not a "work around" at all.

The uname result mentions "x86_64". As you might guess, the 64 means AMD64. A 64-bit CPU and operating system. If it instead said "i386" or "i686" you would be dealing with a 32-bit OS.

---

### Post by Rob Sayer on 2014-03-08
I've installed Clementine at least a half dozen times in various ubuntu desktops.  Never had to add any ppa ... it's in the official repos.

There may be valid arguments for using the developer's ppa instead of the ubuntu repos.  You'll get newer versions which may be faster.

But they're not beta tested like the programs in the canonical repos.  There may be compatibility problems.  I wouldn't generally bother with them myself.

I wouldn't worry about it too much with a program like clementine ... which BTW is may favorite music player, bar none except possibly VLC ... but I certainly wouldn't do it with kde-desktop or something else "mission critical".

---

### Post by oldos2er on 2014-03-08
If you or your client is newish to Ubuntu, it's best to stick with the package manager front-ends e.g. Synaptic or Software Center (I don't think Software Center is installed by default on Xubuntu though).

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---


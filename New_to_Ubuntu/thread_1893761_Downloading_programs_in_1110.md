---
title: "Downloading programs in 11:10"
date: 2011-12-11
forum: New to Ubuntu
---

### Post by Jon Anderson on 2011-12-11
Now what I have done is downloaded a program perlmon 0.2.0 zip I unzipped it and put it on the desktop but how do I actually open it so I can use the program, I believe it is a graphic program. Is their another program that does it , I'm confused. Any response is appreciated.

---

### Post by linuxman94 on 2011-12-11
PerlMon hasn't been updated since 2008, so I would advise against using it.  What sort of info were you hoping to get from it?

---

### Post by Derek Karpinski on 2011-12-11
Looks to me like a 'system monitor'.

---

### Post by linuxman94 on 2011-12-11
> **Derek Karpinski said:**
> Looks to me like a 'system monitor'.

It's a CPU info program, kind of like CPU-Z on windows.

---

### Post by Jon Anderson on 2011-12-11
> **linuxman94 said:**
> PerlMon hasn't been updated since 2008, so I would advise against using it.  What sort of info were you hoping to get from it?
Thanks for the response  I am going to overclock my system and want to see my progress. Right now it is just a file sitting on my desktop . My question is how do I get it out of the file , get the program out of the file.  It has a graphic interface I believe. This is a general question If You download while not in synoptic or software center . I can get it on my desktop but I don't know how to open the programs to its graphical interface.

---

### Post by illgetit on 2011-12-11
What types of files were created after unzipping?

---

### Post by linuxman94 on 2011-12-11
To check your cpu frequency run:

```
cat /proc/cpuinfo
```
in terminal.

---

### Post by Spyderkid on 2011-12-11
Downloading applications from the internet isn't always a good idea, unless it's from a trusted source so google, opera, sourceforge, gnome-look.org

Just use the software centre for applications?

---

### Post by Jon Anderson on 2011-12-11
[QUOTE=Spyderkid;11529466]Downloading applications from the internet isn't always a good idea, unless it's from a trusted source so google, opera, sourceforge, gnome-look.org

Just use the software centre for applications?[/QUO

So is there a program or not that will convert my file on my desktop to the program that is in it.

---

### Post by ExileAmongYou on 2011-12-11
Did you download it from [here]("http://www.overclock.net/t/212320/perlmon-cpu-z-like-program-for-linux")? There are some fairly clear instructions on that page for how to install it. You open a terminal, cd into the unzipped folder, and run "sudo perl Installer".

Two reasons to be cautious about installing it: it looks like it hasn't been updated in quite a while, there's no guarantee it still works like it should.
More importantly, you're installing it from an untrusted source. Because you have to use sudo to run the installation script, you're giving it (potential) access to all the important system files. It's up to you whether or not you decide to trust the creator of this particular program, just so long as you're aware of the risks.

---

### Post by Jon Anderson on 2011-12-11
> **ExileAmongYou said:**
> Did you download it from [here]("http://www.overclock.net/t/212320/perlmon-cpu-z-like-program-for-linux")? There are some fairly clear instructions on that page for how to install it. You open a terminal, cd into the unzipped folder, and run "sudo perl Installer".

Two reasons to be cautious about installing it: it looks like it hasn't been updated in quite a while, there's no guarantee it still works like it should.
More importantly, you're installing it from an untrusted source. Because you have to use sudo to run the installation script, you're giving it (potential) access to all the important system files. It's up to you whether or not you decide to trust the creator of this particular program, just so long as you're aware of the risks.********************************************Thank you ,I'll pass on it. What do you suggest for a program that is not in Synoptic or software center, is it just stay away from them. By the way I tried their suggestion to open the file but it just said the file doesn't exist ,even though it was right on my desktop. I appreciate your advice, thank you

Jon

---


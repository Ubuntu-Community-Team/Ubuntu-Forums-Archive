---
title: "Can't install packages"
date: 2013-02-15
forum: New to Ubuntu
---

### Post by Rimski on 2013-02-15
Hello everyone I'm new to the forum and ubuntu and I obviusly came here because I have a problem
 
whenever I try to install something through the Software center all I get is this

Package dependencies cannot be resolved
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

I'm running Ubuntu 12.10 
Sorry for any grammar mistakes i'm a spanish speaker

---

### Post by ibjsb4 on 2013-02-15
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get update
```

Get any errors?  If not, try your install again.

And welcome to the forums  :)

---

### Post by MadmanRB on 2013-02-15
and keep in mind you can copy and paste commands given here.
Anywho sometimes the software center does not like outside packages, I suggest in the software center install gdebi and synaptic package manager.

---

### Post by Rimski on 2013-02-16
> **ibjsb4 said:**
> [Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get update
```

Get any errors?  If not, try your install again.

And welcome to the forums  :)

thanks, this solved my problems

---

### Post by ibjsb4 on 2013-02-16
Good deal :) don't forget 

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---


---
title: "Live Version work with Downloaded Application?"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by KAWill70 on 2008-09-05
**When running Ubuntu Live from a CD, is it possible to download a new program from the internet and get it to run?**

---

### Post by dizee on 2008-09-05
yes you can install programs in a live cd environment.

---

### Post by paul_mcl on 2008-09-05
Yep. Try it:
```
# apt-get update
# apt-get install wine
```

---

### Post by KAWill70 on 2008-09-05
Thanks all for the help.

I assume the program is installed and run totally within system memory when running Linux "Live".  I also assume the program will not reappear after the next Live boot.

I have never used the apt commands but will give them a try.

---

### Post by snowpine on 2008-09-05
> **KAWill70 said:**
> Thanks all for the help.

I assume the program is installed and run totally within system memory when running Linux "Live".  I also assume the program will not reappear after the next Live boot.

I have never used the apt commands but will give them a try.

You can also use the Add/Remove Programs or Synaptic Package Manager applications. They are basically just graphic interfaces for apt-get.

You are correct that the installed apps will be gone next time you boot from the Live CD. There is a program called Remastersys that you can use to create your own custom Live CD, however, it's a slightly involved process and I'm not sure if you can run Remastersys itself from the Live CD. :)

---

### Post by Oldsoldier2003 on 2008-09-05
> **KAWill70 said:**
> 
I assume the program is installed and run totally within system memory when running Linux "Live".  I also assume the program will not reappear after the next Live boot.


That is correct. (unless of course you have customized a live usb or set up a persistent live cd- but these are not available in the live cd you download from [www.ubuntu.com/getubuntu](www.ubuntu.com/getubuntu))

---


---
title: "catalyst control center"
date: 2012-10-06
forum: New to Ubuntu
---

### Post by beelzebufo on 2012-10-06
I manually installed the newer 12.8 catalyst drivers for my ubuntu 1204 64 bit system, all went well, and my computer is performing much much better, but, I lost my catalyst control panel somehow, so I can't set up my dual displays, synaptic says that fglrx-amdcccle is installed, but I have not access to it. 

```
wreckingball@wreckingball-pc:~$ sudo fglrx-amdcccle
sudo: fglrx-amdcccle: command not found
```

I am confused, it's probably something simple, but I am just not seeing it, any help would be greatly appreciated.

thanks in advance
Beelzebufo

---

### Post by DuckHook on 2012-10-07
*fglrx-amdcccle* is the name of the package and not the command. There will be no such command in your system. I am unfamiliar with the catalyst chipset, but try (in a terminal):

```
locate catalyst
```

If this returns nothing, then type:

```
dpkg -L fglrx-amdcccle
```

This will return a complete list of the files installed by the package. You will have to look for a command that appears to run the catalyst control center.

If this query returns a (list of) command(s), then, to be safe, Google the complete command before running it.

---


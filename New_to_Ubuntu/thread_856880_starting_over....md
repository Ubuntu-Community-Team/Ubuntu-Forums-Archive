---
title: "starting over..."
date: 2008-07-11
forum: New to Ubuntu
---

### Post by AnLGP on 2008-07-11
i'm getting good at breaking my system.  I tried to gpart my system and I must've partitioned the debian install.  whoops.  so I got myself an ubuntu minimal CD and used that.  

But now my sound doesn't work.  I followed all the "things to do after you install ubuntu guides" but can't get the sound to work :(.  If there's anything I can list to help ya please let me know.

Also, I see why they put sudo on things..

---

### Post by Inxsible on 2008-07-11
> **AnLGP said:**
> i'm getting good at breaking my system.  I tried to gpart my system and I must've partitioned the debian install.  whoops.  so I got myself an ubuntu minimal CD and used that.  

But now my sound doesn't work.  I followed all the "things to do after you install ubuntu guides" but can't get the sound to work :(.  If there's anything I can list to help ya please let me know.

Also, I see why they put sudo on things..So why didn't you use the Debian CD again?

I am assuming that you already went thru alsamixer/alsaconf and the like ...

Its much faster than Ubuntu, IMO. Anyway, I had a similar problem....your kernel is probably not loading the sound drivers. Try downgrading a kernel version and see if the older kernel picks up the drivers.

---

### Post by AnLGP on 2008-07-11
dunno.

how do I downgrade kernel versions?

alsaconf wouldn't work for some reason.

---

### Post by Inxsible on 2008-07-11
> **AnLGP said:**
> dunno.

how do I downgrade kernel versions?

alsaconf wouldn't work for some reason.just install a kernel  version lower than what you are currently using. Search it in synaptic...or if you haven't installed synaptic, you can use ```
aptitude
``` as root and it will give you a GUI in a terminal window to find the package you want.

yet another method is to use this command ```
aptitude search linux-kernel*
```

when you say alsaconf didnt work...what errors did it give you?

---

### Post by AnLGP on 2008-07-11
About to execute /usr/sbin/alsaconf.
This command needs root privileges to be executed.
Using sudo...
Enter steve password at prompt.
[sudo] password for steve: 
sh: /usr/sbin/alsaconf: not found

---

### Post by AnLGP on 2008-07-11
I think it's weird the option to use it is in the menu but after I try and run it it's not available?

---


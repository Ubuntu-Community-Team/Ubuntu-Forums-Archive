---
title: "How to check out what hardware is on my computer."
date: 2008-11-22
forum: New to Ubuntu
---

### Post by nu2this2 on 2008-11-22
I was wondering if there is a terminal command that would allow me to see what hardware devices are recognized by ubuntu? I am using Hardy Heron.

Then how to configure them. For example, my wireless card does not work the same way it does in windows, nor do I have the versatility of printer functions with ubuntu.

Thanks for any help.

---

### Post by zzHanks on 2008-11-22
Hello.
If you ant to get your hardware information (your hardware is most likely supported) then type > sudo apt-get install sysinfo in terminal, or use Synaptic.

Note: If you have not installed Ubuntu, this information is useless. But you can always try out the LiveCD.

---

### Post by fooman on 2008-11-22
> **nu2this2 said:**
> I was wondering if there is a terminal command that would allow me to see what hardware devices are recognized by ubuntu? I am using Hardy Heron.


```
lspci
```

---

### Post by mc4man on 2008-11-22
@zzHanks
that's a pretty nifty little app, I like it.

@nu2this2
If you don't see what you want or the terminal output is too congested try 

```
sudo lshw -html > hardware.html
```

Look in home folder for hardware.html, breaks the listings up for an easy read

---


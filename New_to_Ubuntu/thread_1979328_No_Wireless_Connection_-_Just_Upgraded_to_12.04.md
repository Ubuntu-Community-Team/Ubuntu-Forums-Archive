---
title: "No Wireless Connection - Just Upgraded to 12.04"
date: 2012-05-13
forum: New to Ubuntu
---

### Post by peaksails on 2012-05-13
Just upgraded to 12.04.

I cannot seem to get a wireless connection to the router at all.

Your assistance is greatly aprreciated!

---

### Post by kc1di on 2012-05-13
> **peaksails said:**
> Just upgraded to 12.04.

I cannot seem to get a wireless connection to the router at all.

Your assistance is greatly aprreciated!

A Little more information Please do you know the Wireless card your using. If not you can find it by typing the following in a terminal:
[HTML]lspci[/HTML]
look for a line that says wireless adaptor or similar.
let us know the card and we may be able to get it going for you.

---

### Post by peaksails on 2012-05-13
It says Command Not Found when entered via terminal.

We have upgraded 10 machines and this was the last. All went flawlessly until now.

This machine is a HP desktop.

Any help would be appreciated.

---

### Post by bkratz on 2012-05-13
> **peaksails said:**
> It says Command Not Found when entered via terminal.

We have upgraded 10 machines and this was the last. All went flawlessly until now.

This machine is a HP desktop.

Any help would be appreciated.


I suspect you may have typed a 1 rather than a lowercase "L" in lspci

Anyway if you copy/paste the following in the terminal (one at a time or if you insist on typing) the | is just above my \ on a US keyboard.


```
lspci -nn | grep 0280
 rfkill list all

```


we should at least get your wireless card and whether it is turned on or not

---

### Post by peaksails on 2012-05-13
Thanks!

Under rfkill: Hard & soft = No

Ralink Corp. RT3092 Wireless 802.11 2T/2R PCIe [1814:3092]

---

### Post by peaksails on 2012-05-13
bump:confused:

---

### Post by Hadaka on 2012-05-13
This should help you out, or atleast point you in the right direction
[http://ubuntuforums.org/showthread.php?t=1850267&highlight=ralink](http://ubuntuforums.org/showthread.php?t=1850267&highlight=ralink)

good luck

---

### Post by peaksails on 2012-05-13
Thanks, Hadaka.

Gave it a try but no luck.

Does anyone think a fresh install would solve the problem. This particular machine was upgraded.

Thanks!

---

### Post by Hadaka on 2012-05-13
a clean fresh install may or may not fix the wireless problem, but atleast you will 
know that there are not any files left over from the last os. so.yes..unless you
have a ton of programs and files you need, wipe the drive and go fresh. Then
if wireless is not working it will be easier to find the problem.
good luck

---

### Post by idoitprone on 2012-05-13
```
lspci -nnk 
```

we have to see if there are kernel modules conflicting each other

---


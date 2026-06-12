---
title: "Maximum usable RAM"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by Smittysmit on 2008-07-27
I'm looking at building a home server with Ubuntu.  What is the maximum RAM that Ubuntu will see/use?  It will likely be 32bit.

---

### Post by benfindlay on 2008-07-27
Realistically, depending upon the other hardware present (such as video cards etc) you can expect to get around 3 to 3.5 gigs of RAM in a 32bit system.

Hope this helps!

---

### Post by flytripper on 2008-07-27
yer, i thought it was 4 gig max, with a bit lost to system and other stuff.

---

### Post by kerry_s on 2008-07-27
32bit= 3.5
unless you rebuild the kernel with large mem or use debian with the large mem kernel.

---

### Post by ibuclaw on 2008-07-27
It will be as much as the motherboard was designed to handle.
I have one such motherboard that can use up to 2GB of RAM, and yet it has 4 RAM slots. (I have another, older motherboard that can only use 64MB of RAM per slot, regardless of the **actual** RAM size I put in...)

This question has nothing to do with what Ubuntu can handle (although, it does help on larger, rack-style systems).

To find the answer to your question, you have to look up documentations of the motherboard you wish to use, either from the manual you got with the motherboard, or from the manufacturers site.

To **utilise** the RAM you already have, set the vm.swappiness to a low value in your /etc/sysctl.conf file.
eg:
```
vm.swappinness = 0
```

Regards
Iain

---

### Post by sdennie on 2008-07-27
See: [ Ubuntu with 4GB+ of memory]("http://ubuntuforums.org/showthread.php?t=855511")

---


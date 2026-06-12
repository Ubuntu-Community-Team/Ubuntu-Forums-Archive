---
title: "Problems getting online"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by Marie Au on 2008-09-04
Hi,when I started my computer yesterday the calendar had been reset, out of nowhere, and after that I haven't been able to access any wireless network (although I have one available). The computer doesn't seem to detect any networks at all, I only get the little icon with "no network connection". Any ideas of what to do?

---

### Post by nothingspecial on 2008-09-04
Was it working before, is it wireless or wired?

---

### Post by pmlxuser on 2008-09-04
Just out of curiosity, is the wireless network switch ON.
Sometimes when that happen to my laptop i link it to a wired Lan (don't know what happens) but after that am able to see the wireless and i can connect

hope the little info is of assistance.

---

### Post by pmlxuser on 2008-09-04
sorry it was double posting
 i wish their was a way to delete a double post

---

### Post by nothingspecial on 2008-09-04
Another thing to try is resetting your router. This is usually done by unplugging it for at least 30 seconds.

---

### Post by halitech on 2008-09-04
when you set it up originally, did you hard code any information or was it all set for DHCP?

open a terminal and post the output of```
lspci
``` and ```
ifconfig
```

---

### Post by pmlxuser on 2008-09-04
Just out of curiosity, is the wireless network switch ON.
Sometimes when that happen to my laptop i link it to a wired Lan (don't know what happens) but after that am able to see the wireless and i can connect

hope the little info is of assistance.

---

### Post by nothingspecial on 2008-09-04
> **pmlxuser said:**
> sorry it was double posting
 i wish their was a way to delete a double post

You`ve done it again :)

---

### Post by halitech on 2008-09-04
as a regular user, there is no way for you to delete a douple (or triple ;) ) post. on the left side under your info there is a button called report. If you click on that, there is a message box that wil send a message to the mods and you can ask them to remove it.

from the bottom of the report page:
> Note: This is ONLY to be used to report spam, advertising messages, requesting posts be moved or deleted, and problematic (harassment, fighting, or rude) posts.

---

### Post by Marie Au on 2008-09-04
It's a wireless network, which is switched on and has been working perfectly until now. I also brought the computer at work today to test it, but even there it didn't detect any of the networks. Which leads me to conclude that the computer is the problem, not the network. I have tried to use the command I used when I installed the network: sudo dhclient, but it's not helping.

---

### Post by halitech on 2008-09-04
> **Marie Au said:**
> It's a wireless network, which is switched on and has been working perfectly until now. I also brought the computer at work today to test it, but even there it didn't detect any of the networks. Which leads me to conclude that the computer is the problem, not the network. I have tried to use the command I used when I installed the network: sudo dhclient, but it's not helping.

did you get a message when you ran sudo dhclient?

---

### Post by Marie Au on 2008-09-04
> **halitech said:**
> did you get a message when you ran sudo dhclient?

I got the message that the network is sleeping.

---

### Post by halitech on 2008-09-04
> **Marie Au said:**
> I got the message that the network is sleeping.

ok, what exactly did you type in? Also, have you run the 2 commands I posted earlier?

---

### Post by Marie Au on 2008-09-04
> **halitech said:**
> ok, what exactly did you type in? Also, have you run the 2 commands I posted earlier?

i wrote sudo dhclient. i have tried your two commands, but nothing changes.

---

### Post by halitech on 2008-09-04
> **Marie Au said:**
> i wrote sudo dhclient. i have tried your two commands, but nothing changes.

can you post the output of those 2 commands so we can check them

---

### Post by Marie Au on 2008-09-04
> **halitech said:**
> can you post the output of those 2 commands so we can check them

I can't get online with that computer so i can't copy paste it...

---

### Post by halitech on 2008-09-04
do you have a thumbdrive? you can copy the info to a text file, save it on the tumbdrive and then post it from a system that has access

---

### Post by Marie Au on 2008-09-04
> **halitech said:**
> do you have a thumbdrive? you can copy the info to a text file, save it on the tumbdrive and then post it from a system that has access

No, not here - might try tomorrow! thank you.

---


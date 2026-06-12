---
title: "Computer freezing"
date: 2014-06-10
forum: New to Ubuntu
---

### Post by Paper Pusher on 2014-06-10
My computer kept freezing when i was trying to watch videos on youtube, also when i tried to log in to gmail it would also freeze. I had to restart my computer secveral times. upgraded my computer to 14.04. We excepted all updates.

---

### Post by Vladlenin5000 on 2014-06-10
Graphics card?

---

### Post by Paper Pusher on 2014-06-10
Gallium 0.4 on NVA5. I have nvidia grapgic cards.

---

### Post by deadflowr on 2014-06-10
Quick easy
Open a terminal and copy this
```
lspci | grep VGA
```
and post the output here, in this thread.
From there, we can determine if a better driver is available for you.

---

### Post by Paper Pusher on 2014-06-10
Hi deadflowr, I pasted your command and thisi s what I got:

axel@axel-GA-78LMT-USB3:~$ lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GT216 [GeForce GT 220] (rev a2)

---

### Post by Vladlenin5000 on 2014-06-11
GeForce GT 220 works beautifully with proprietary nvidia drivers, v.304.xx.
Go to System Settings > Software & Updates and you'll find the tab for additional software, select the recommended driver, allow some time for download and installation, reboot & test again.

---

### Post by Paper Pusher on 2014-06-12
Thank you very much for all your advice. The problem was a broken graphics card. My old graphics card was a Sparkle card based on a nvidea gt220. Two blades of the fan of the card were broken. This caused the card to over heat. The card was replaced with an MSI card GT620. My computer works fine now. 

Once again, thank you very much.

---


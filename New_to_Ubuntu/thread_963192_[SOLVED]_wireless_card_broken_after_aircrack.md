---
title: "[SOLVED] wireless card broken after aircrack?"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by DoubleMcLovin on 2008-10-30
So I was playing around cracking my own wireless netowrk, I ran the comman ```
sudo airmon-ng start wifi0 6
``` which created the device ath1 on channel 6. Ran everything just fine, but then I finish up with the hex key inhand and try and check it by connecting, well first I ran ```
sudo airmon-ng stop ath1
```, after that I cant get connection through my wireless device =\ any ideas??

---

### Post by plucky on 2008-10-30
> after that I cant get connection through my wireless device =\ any ideas??



Doesn't aircrack put the interface into **Monitor mode**?

From a terminal ```
ifconfig
``` and see if it is in monitor mode.

Try ```
sudo ifdown <interface>
sudo ifconfig <interface> mode Managed
sudo ifup <interface>
```

Or something like that.


Last resort reboot.


Good Luck

---

### Post by DoubleMcLovin on 2008-10-30
Keeps saying the interface ath0 not configured. I killed ath1 which is the monitor mode interface created by aircrack. But ath0 which I use to connect isnt working. I tried killing that and rebooting and it didnt work either

---

### Post by plucky on 2008-10-30
> **DoubleMcLovin said:**
> Keeps saying the interface ath0 not configured. I killed ath1 which is the monitor mode interface created by aircrack. But ath0 which I use to connect isnt working. I tried killing that and rebooting and it didnt work either


Post output of ```
ifconfig
iwconfig
```

---

### Post by DoubleMcLovin on 2008-10-30
Interestingly enough, I ran the set of updates that came out today and it fixed my problem, though I'm guessing as soon as I try aircrack again it will give me the same problem again. 
Any way to prevent my problem in the future?

---

### Post by HyperHacker on 2008-10-30
It does put the card into monitor mode. Rebooting will fix it, but there is a better way using the command line, I don't remember how exactly.

---

### Post by DoubleMcLovin on 2008-10-30
problem is that I rebooted twice before starting this thread =\ still it wouldn't work. I wonder if when I just ran this update it updated my restricted drivers and that fixed it or something, but it was apparently broken. I just re-cracked the network key, then shut down the ath1 monitor mode interface and connected without a hitch. So I suppose I will mark this thread as solved, strange phenomena I suppose?

---


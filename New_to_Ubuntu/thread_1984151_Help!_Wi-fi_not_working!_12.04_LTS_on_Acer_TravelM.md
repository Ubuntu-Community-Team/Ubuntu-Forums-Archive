---
title: "Help! Wi-fi not working! 12.04 LTS on Acer TravelMate5520."
date: 2012-05-21
forum: New to Ubuntu
---

### Post by steerre on 2012-05-21
I just removed ubuntu 10.04 and replaced with 12.04, but now I don't have wireless anymore!!!! how it's possible??? with old version everithing was ok!!!
I downloaded and activated broadcom STA drivers but it still doesn't work....:(

---

### Post by jtarin on 2012-05-21
[Look here]("http://ubuntuforums.org/showthread.php?t=1975503")

---

### Post by centaurusa on 2012-05-21
> **steerre said:**
> I just removed ubuntu 10.04 and replaced with 12.04, but now I don't have wireless anymore!!!! how it's possible??? with old version everithing was ok!!!


Does your wired Internet connection work?  Does trying to access the wireless connection cause the entire system to hang?  The latter is a known bug - especially on the Acer Aspire One netbook, which has a Broadcom 802.11n Network (wireless) Adapter.  One solution is to disable the wired connection and just use wireless.  See:

[http://linuxnorth.wordpress.com/2011/10/23/wireless-less/](http://linuxnorth.wordpress.com/2011/10/23/wireless-less/)

---

### Post by steerre on 2012-05-21
> **jtarin said:**
> [Look here]("http://ubuntuforums.org/showthread.php?t=1975503")

DONE!!! It works!!!!

```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43
sudo modprobe b43
```

Thank you very much!!!!

---


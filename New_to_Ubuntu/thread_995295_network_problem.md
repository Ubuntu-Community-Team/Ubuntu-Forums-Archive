---
title: "network problem"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by Wils on 2008-11-27
Hi 

I am having trouble connecting to the net in my newly installed ubuntu 8.10. I have other laptop with 8.10 on it which connects very well. Both have the same settings and when I swop wireles cards the the problem move to the other laptop leaving the what was good laptop now not working. One small diffrence is that when I click on network manager in the notification area my network is shown before the network name is an orange circle the good network has a black centre the bad network has a white centre. Any help would be great 

wils

---

### Post by Michael.Godawski on 2008-11-27
Would be good to know what this "bad" wlan card is which might causing the headaches.

On that laptop which is not connecting to the wireless lan, run these commands in terminal and post the output here:

```
sudo lshw -C network
lspci
iwconfig
```

---


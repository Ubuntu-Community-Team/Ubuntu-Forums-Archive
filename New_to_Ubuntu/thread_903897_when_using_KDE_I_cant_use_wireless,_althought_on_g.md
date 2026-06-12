---
title: "when using KDE I cant use wireless, althought on gnome I can."
date: 2008-08-28
forum: New to Ubuntu
---

### Post by WinterMadness on 2008-08-28
infact when I put in my ethernet cable I dont even get something saying i connected.Typically it does, even when I used kubuntu before.

I have ndiswrapper installed and such, and my driver works. wl0 appears, and I can scan for networks in KWifiManager but nothing lets me use the network.

---

### Post by vikram on 2008-08-28
Have you tried KNetworkManager ?

Also are you using WEP or WPA or unencrypted network ?

---

### Post by Crafty Kisses on 2008-08-28
That's very weird, post the output of:
```
lshw -C network
```

---


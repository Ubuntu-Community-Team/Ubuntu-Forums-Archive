---
title: "USB wireless adapter issues"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by pete-the-meat on 2008-05-30
Hi. I am trying to install a Hawking HWU54DM usb hi-gain wireless adapter, although even this sentence seems a bit ambitious since I haven't even got that far yet.

I have a dual boot machine, running XP and Ubuntu 8.04, with an Abit Fatality AA8XE motherboard and a pentium 4 3.2 GHz processor (although I'm sure that isn't important just now).

I have run all around the internet and the closest I have come to a real answer is to install the ZD1211 firmware, but I already have the zd1211 firmware installed.

I know the adapter works because it runs fine in XP. I can't even find support for the device on the manufacturers site even though it's only a year old. D:

Please help?

---

### Post by superprash2003 on 2008-05-31
could you post your iwconfig output

---

### Post by pete-the-meat on 2008-05-31
Sure, sorry about the delay on this one, a difficult day has been had! Here's the iwconfig output:

```
pete@pete-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.
```

Both my ethernet connections are tested and working but neither is connected at the moment since wireless is the only internet source available to me.

Thanks :)

---

### Post by superprash2003 on 2008-06-01
go to system->Administration->Restricted Drivers Manager ( or hardware drivers) and see if you find any WLAN drivers there

---

### Post by pete-the-meat on 2008-06-01
No restricted drivers there except my graphics card, which is already in use

---

### Post by pete-the-meat on 2008-06-01
OK - so I tried researching the issue again and came up with a what-seems-to-be-fairly-standard solution using ndiswrapper. It works just fine (I ended up using a different wlan card, a pci one). I'm so sorry for being such a noob and bothering you with this trivial question. Many thanks for your patience. :)

---

### Post by SunnyRabbiera on 2008-06-01
> **pete-the-meat said:**
> OK - so I tried researching the issue again and came up with a what-seems-to-be-fairly-standard solution using ndiswrapper. It works just fine (I ended up using a different wlan card, a pci one). I'm so sorry for being such a noob and bothering you with this trivial question. Many thanks for your patience. :)

Hey you learn things by asking, that is why we are here.
The linux community is very supportive, even for windows issues.

---


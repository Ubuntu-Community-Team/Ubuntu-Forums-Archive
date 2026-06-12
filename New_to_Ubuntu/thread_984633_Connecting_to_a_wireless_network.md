---
title: "Connecting to a wireless network?"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by Rambler92 on 2008-11-16
I just installed xubuntu onto my computer, but I can't figure out how to connect to my wireless router to get on the internet. can anyone help? my router is a Linksys if that helps.

---

### Post by squeabs on 2008-11-16
You may want to try wine. It's a windows emulator. Also, ndis wrapper is a useful tool for connecting to wireless networks. If your wireless NIC isn't detected by linux, you'll have to install those apps (wine, ndis) and find your wireless driver from the manufacturers website. Once you do that, install it, which is where wine comes in because not all wireless driver downloads can be read by linux. Some of them may be a .exe.

You can find both of these apps in the add/remove programs under applications.
See attachments.

---

### Post by melojo on 2008-11-16
open a terminal and type this below

```
 iwlist scan 
```

if your card is recognize it will list available networks nearby.

If not post the output of.

```
 lspci 
```

```
 sudo lshw -C network 
```

---

### Post by Rambler92 on 2008-11-16
squeabs, how do i download these if i can't access the internet? the computer says i don't have wine, and ndis says that "Windows Wireless Drivers cannot be installed on your computer type (i386)."

---

### Post by squeabs on 2008-11-16
If you have a good network cable, you could plug it into the router if there's a spot for it and use a wired connection to get it. It's what I had to do when I installed Hardy on my laptop.

---

### Post by melojo on 2008-11-16
I think ndiswrapper is on the cd at least it is on 8.10

---


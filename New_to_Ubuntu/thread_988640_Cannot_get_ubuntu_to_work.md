---
title: "Cannot get ubuntu to work"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by waste301 on 2008-11-20
Hi.  I've got a new PC I bought at Walmart, because my old one was destroyed in shipping.  Brand new PC, with Vista installed.  I don't like vista and have never used it, and dl'd and installed ubuntu 8.10 after burning a live cd.  It installed fine and I can boot into it, but it won't access the internet and I cannot adjust the monitor resolution from 800x600, there aren't any other options listed.  The PC is an off the shelf Compaq, and has all kinds of HP/anti-virus/other crap that always runs.

I've searched the forums but haven't found anything.  Any help appreciated.

---

### Post by jenkinbr on 2008-11-20
Could you provide more details as to the hardware, or possibly Compaq's model number for the PC so we can look into it?

---

### Post by ciscosurfer on 2008-11-20
> **waste301 said:**
> Hi.  I've got a new PC I bought at Walmart, because my old one was destroyed in shipping.  Brand new PC, with Vista installed.  I don't like vista and have never used it, and dl'd and installed ubuntu 8.10 after burning a live cd.  It installed fine and I can boot into it, but it won't access the internet and I cannot adjust the monitor resolution from 800x600, there aren't any other options listed...
More details are needed. Are you trying to connect to the Internet over a wired or wireless connection?  What is the exact make/model/manufacturer of the PC (yes, I saw you mentioned Compaq); laptop/desktop?

It could be that 800x600 is the top resolution you can attain based on your installed graphics card (which could very well be on-board).

> The PC is an off the shelf Compaq, and has all kinds of HP/anti-virus/other crap that always runs.I thought you said you've never used Vista on this machine?

---

### Post by mkvnmtr on 2008-11-20
You might need to explain how you installed Ubuntu also.

---

### Post by dunkar70 on 2008-11-20
Did the live CD allow you to connect to the Internet or use full resolution? You can also try using the 8.04 LTS CD. The drivers on that version may not be as cutting edge.

---

### Post by halitech on 2008-11-20
for the resolution, open a terminal and run```
sudo xfix
```

to find out more about the wireless, open a terminal and post the results of```
sudo lspci
```

---

### Post by ciscosurfer on 2008-11-20
You don't have to "sudo" lscpi.  You can compare the results if you're curious.```
lspci >reg.lspci
sudo lspci >sudo.lspci
diff reg.lspci sudo.lspci
```

---

### Post by halitech on 2008-11-20
> **ciscosurfer said:**
> You don't have to "sudo" lscpi.  You can compare the results if you're curious.

just habit of putting sudo in when doing things like this, doesn't hurt anything to put it in

---

### Post by ciscosurfer on 2008-11-20
> **halitech said:**
> just habit of putting sudo in when doing things like this, doesn't hurt anything to put it inThat's entirely true ;-)

---


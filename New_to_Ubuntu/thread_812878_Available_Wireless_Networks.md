---
title: "Available Wireless Networks?"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by vbenares on 2008-05-30
Is there a way to see all available wireless networks?  I can connect to wireless networks if I know the SSID, but I can't find the available SSIDs.  

(I'm using Hardy.)

---

### Post by Joeb454 on 2008-05-30
Single Click (Left mouse button) the Network icon in the top right of your screen, it should list networks that are find in range :)

---

### Post by LibertyShadow on 2008-05-30
Also, you can open a terminal and issue the following command:
```
sudo iwlist scanning
```

---

### Post by roderick on 2008-05-30
I have a similar problem on my Wife's Laptop, with a card that requires ndiswrapper. Eversince Gutsy, the list of networks do not auto-populate in Knetworkmanager. If I however manually login once, the list of networks will appears... very strange as it used to work correctly with 7.04.

I believe this is probably the problem thew OP was describing, so the suggestion to look at the list by single-click is not a suggestion as it is the problem - no list in the is available. Though I am only guessing based on my experience.

I have yet to find a solution to this. Basically, my wife has had to memorize the SSID and encryption key details - no small feat on her part... but she does it. :)

From what I gather it's a ndiswrapper/NetworkManager issue and not Knetworkmanager (the front-end).

---


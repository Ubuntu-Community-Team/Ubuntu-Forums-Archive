---
title: "internet speed"
date: 2013-03-24
forum: New to Ubuntu
---

### Post by tylerstanton22 on 2013-03-24
Hello everyone. I just bought a brand new dell desktop and it came with windows 8. I didn't like windows 8 at all and I read online about ubuntu. Without knowing what ubuntu is I just went ahead and installed it. It seems alright, a little faster to boot. My question is since getting the computer last week it has had slow internet. It gets .5mbps download speed, where my laptop in the same spot gets 8mbps download speed. I assumed it was Windows 8 and after installing ubuntu the download speed hasnt gotten any better. I asked a question on the Dell forums and got a response, but it is how to troubleshoot on windows 8. How do I find my wireless card in ubuntu? I need to try and make changes to the settings. Any recommendations?

---

### Post by HackerFinn on 2013-03-24
Hello. :)
Glad to see a new Ubuntu user here. :)
I don't think you can do much about your problem though. :/
I think the problem is that your wireless card is just plain slow.
Could you please post all the specs on _both_ the computers _including the wireless cards_?
That would help a lot. :)
Greetings and have fun with Ubuntu. :)

---

### Post by gifford on 2013-03-24
Welcome to the forums and to Ubuntu.

To start with, copy or paste this command into a terminal window:  lspci
It will give lots of information but your card should show up as wireless network adapter. Be sure and post this back and also list what version of Ubuntu you are using as well as specific information about the laptop.

For your information, there is a Dell Ubuntu Support section listed under Ubuntu Specialised Support in the forums.  It is good to look there as well when having questions or issues with Dell products.

---

### Post by tylerstanton22 on 2013-03-24
Hey you guys thanks for the help. I am by no means a computer guy, so this is all new. The Dell 660s is the desktop that is having issues. The laptop is an HP that gets great internet speeds in the same location as the desktop. This is the wirelss cars specs that came when I put that command into the terminal.
03:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)

The desktop is this here [http://www.amazon.com/Dell-Inspiron-i660s-2002BK-Desktop-Black/dp/B00ALSNEJK/ref=sr_1_1?ie=UTF8&qid=1364178240&sr=8-1&keywords=dell+660s](http://www.amazon.com/Dell-Inspiron-i660s-2002BK-Desktop-Black/dp/B00ALSNEJK/ref=sr_1_1?ie=UTF8&qid=1364178240&sr=8-1&keywords=dell+660s)

The HP laptop is a pavillion g4 with windows 7 and a realtek RTL8188CE 802.11b/g/n wifi adapter.



Am I looking at just getting a better wireless card for my dell 660?

---

### Post by tylerstanton22 on 2013-03-24
Im running the 64 bit ubuntu 12.10

---

### Post by sandyd on 2013-03-24
try [http://ubuntuforums.org/showthread.php?t=2018238](http://ubuntuforums.org/showthread.php?t=2018238)

---

### Post by tylerstanton22 on 2013-03-25
Basically type this code into the terminal? /etc/modprobe.d/ath9k.conf followed by 

options ath9k nohwcrypt=1 ? Thanks

---

### Post by sandyd on 2013-03-26
do
```

gksu gedit /etc/modprobe.d/ath9k.conf
```

paste in
```

options ath9k nohwcrypt=1
```
save, close, and reboot

---


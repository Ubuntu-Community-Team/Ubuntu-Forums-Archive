---
title: "problem on printing"
date: 2007-12-10
forum: Philippine Team
---

### Post by jmazaredo on 2007-12-10
[IMG]http://photos-674.friendster.com/e1/photos/47/66/5436674/1_394274085l.jpg[/IMG]

yan ang network ko.

pag nagkabit ako nang printer sa isang pc na nasa lan at shinare ko d ako maka print pero na iinstall ko.

ung windows server may domain controller at dns
ung linux naman may dhcp at nagiging router nang internet

nilagay ko sa dhcp config ko sa linux na isama ang 192.168.0.4 na dns para sana maresolve ung mga nasa lan ( d ko alam kung tama ako )
dati naka static lahat sila binago ko lahat na dynamic nalang so ang nagiging config nang client ay

ex,

ip 192.168.0.100
sm 255.255.255.0
gw 192.168.0.1
dns 1 - dns nang isp ko
dns 2 - dns nang isp ko
dns 3 - dns nang domain controller na 192.168.0.4

san ba ako dapat mag konfigure?

---

### Post by elite_angel on 2007-12-10
hmm? you switched to dynamic? Static is advisable when you have DOMAIN...

On printing, try to research about SAMBA... It can help!

---

### Post by daxumaming on 2007-12-12
I use CUPS, for windows, I just add this: [http://IPofPCwithPrinter:631/printers/NameofPrinter](http://IPofPCwithPrinter:631/printers/NameofPrinter)
I make sure first that I can access that from a web browser before I add it to my windows clients
As for Linux, Kubuntu specifically, i sometimes have problems printing via IPP/HTTP, so I usually select use Remote CUPS Server. I just input the ip address, username, and password.... and there you go!

---

### Post by jmazaredo on 2007-12-17
i tried putting static ip on the client pc where the printer is installed... it somewhat solved the problem i don't know why. 

Another problem is when i connect to a workstation with a shared printer it asks me for a username and password then i input the username and password and it will connect then after a day ( i think ) when both pc's reboot, the saved pass is gone and access denied again. anyway i think this is not a ubuntu question anymore but thanks anyway.

---

### Post by jmazaredo on 2007-12-18
I have an server active directory with dns that handles windows logon and another linux server that handles gateway and proxy.

The problem whenever i share the printer on a client that is in the active directory the printer loses connection from time to time. Sometimes it prints sometimes it don't print and just spools.

I have tried many options but didn't work.

The solution i got is

Make a client computer that don't belong to the active directory, a single pc that has its own workgroup. Share the printer as normal and on the clients just add it by browsing the printer in the network.

So basic......
This solution I think is just a workaround if you cant share the printer in an active directory environment ( not publishing the printer in the active directory because 1st and foremost I don't know ^^ im a noob ).

Hope this helps other noobs like me.

:lolflag:

---


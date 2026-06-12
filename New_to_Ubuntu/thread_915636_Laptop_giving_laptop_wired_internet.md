---
title: "Laptop giving laptop wired internet?"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by BluePlum on 2008-09-10
Just a quick question, I have a laptop connected to a wireless network, Can i get an ethereal cord and plug it into the ethereal slot on 1 laptop and connect it to the slot in the other laptop? will this work? or does it just not work like that :P

PS. I'm aware that i may have spell ethereal wrong...:KS

---

### Post by skippuff54 on 2008-09-10
yeah u can do it. u need to set what's called a bridge. u will have to bridge ur network interfaces. should be listed under /etc/network/interfaces.

i forget how exactly to do it but u definitely aren't the first one. many people will advise u to get a crossover cable, which is an ethernet (RJ45) cable with a couple of wires reversed.

related issues are setting up a gateway or virtual private network (VPN) depending on ur needs. start with a search along the lines of bridge internet connection or bridge network interface...i'm also pretty sure it's in the wiki, this issue is well documented.

---

### Post by aloshbennett on 2008-09-10
If you want to connect two laptops with an ethernet cord, just plug the cord between them. And bingo! you have a very fast LAN.

Now for the catch: The cable must be cross-crimped. Normal ethernet cable would not work. You can get the cross crimping diagram from net, and make one very very easily (if you have a crimping tool). Its cheap and very handy.

PS: I didnt see the previous post. So thats makes me one of the "many people" :-)

---

### Post by BluePlum on 2008-09-10
You lost me at hello :?

---

### Post by skippuff54 on 2008-09-10
r u still confused or watchin jerry maguire

---

### Post by BluePlum on 2008-09-10
I'm still confused and I live in Austrlia so we dont get the worst shows in the world here :D

---

### Post by skippuff54 on 2008-09-10
well correct me if i'm wrong but what i think u got is a wireless router and two laptops. and what u want to do is pickup wifi with laptop 1 and serve it to laptop 2 via wired connection. right, close, wrong?

IF that's what u wanna do...u need to bridge the connections - and this act is called a bridge - between your wireless network interface (wifi card) and your wired network interface (ethernet card) on laptop 1. so visually it should look somethin like:

Internet<------>wifiLappy1(------->ethernetLappy1<------->ethLappy2

your interfaces can be found by in the menu or by doing in terminal ```
sudo ifconfig
```

wired is probably eth0, wireless is probably eth1, you can find this in menu or doing in terminal ```
sudo iwconfig
```

and like i mentioned what you'll want to do, in terms of programming, is set up what's called a bridge between your wifi interface and your wired interface. lots of documentation out there to help u, just search for somethin like ubuntu wireless bridge on google, look in the wiki and of course these forums

now as far as hardware, you'll most likely need a crossover cable, which is a regular ole ethernet cable with a slight modification to the wires at the end...u can do it urself as described above, find a buddy with a crimp tool to do it for u or just break down and buy one from ur local tech shop.

ps jerry maguire is a tom cruise movie, and i'm proud to be an american who vehemently avoids tv. sittin in front of the tv is one good way to be ignorant of a president who tramples ur constitution

---


---
title: "type of wireless compatibility"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by adwatkin19 on 2008-09-15
hi all, i have a new laptop, its the medion akoya netbook e1210. bought it last sunday n have been itching to put ubunutu on it.

however during my hardware checking on the net, i couldnt find anything about the wireless card. if anyone can help.

the card is an azurewave aw-ne766. does anyone know if this works under ubuntu?

thanks alot

adam

---

### Post by tangibleorange on 2008-09-15
> **adwatkin19 said:**
> hi all, i have a new laptop, its the medion akoya netbook e1210. bought it last sunday n have been itching to put ubunutu on it.

however during my hardware checking on the net, i couldnt find anything about the wireless card. if anyone can help.

the card is an azurewave aw-ne766. does anyone know if this works under ubuntu?

thanks alot

adam

i'm not sure exactly but it would help if you knew the chipset upon which the card is based. if you have a live CD, boot into it and type at a terminal:

```
lspci
lshw -C network
```

posting the output of both commands.

---

### Post by adwatkin19 on 2008-09-19
Update to this thread, after a lot of googling and translating of foreign websites and the such, the aboved mentioned wireless card has a Ralink RT2700E chipset. Does anyone know if it is supported already, or if there will be support of it soon

Many thanks for any help.

Adam

---

### Post by amersault on 2008-09-19
i know Atheros and Ralink chipsets are generally supported. 

also, this link might help - 

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

to determine card and and chipset, type this in terminla:
[I]
lspci -v | less[/I]

---

### Post by likebikes on 2009-01-22
Hi yes Ubuntu 8.04.1 (the .1 is important) does work on the Medion Akoya E1210! and the wireless works almost out of the box. Just use 'windows wireless Drivers' and install the drivers that are on the drivers CD that came with the netbook. I have also installed Ubuntu remix and it looks really nice.

---

### Post by adwatkin19 on 2009-01-26
As an update to this, i have gone to Intrepid and fully updated it, i installed the deb file that contains the driver for this card, i find that it will happily connect to my home unsecured wireless network, however anything else will just not connect and i get an infinite number of passkey entry screens asking for the same key over and over and over again. 

I am looking further into this to hopefully solve it, i will keep this thread updated. 

Adam

---

### Post by adwatkin19 on 2009-01-27
Update once more, i have got this to work, i was entering my passphrase under the 128bit passphrase option, and this didnt work, so i decided to enter the wep passphrase under the 40/128bit key option and it works flawlessly everytime now.

Thanks to those that attempted to give help. 

Adam

---

### Post by diogenes_3 on 2009-02-11
I, too, have the Medion Akoya, and have so far tried it with Easy Peasy and Eeebuntu, both of which are based on Ubuntu and the Netbook Remix. Both worked like a charm, wireless with WPA-PSK was available in the live session without any tweaking or extra installing.

I installed neither, though... will stick to Ubuntu itself.

---


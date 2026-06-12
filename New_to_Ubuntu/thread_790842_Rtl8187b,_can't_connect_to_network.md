---
title: "Rtl8187b, can't connect to network"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by icdelg on 2008-05-11
I am a complete noob when it comes to linux. Through countless days of sifting through posts I have been able to install the modified rtl8187b driver (Ndiswrapper always showed hardware present:no.) However, I can't seem to connect to my WEP 128 wireless network. I am currently using Network MAnager. Every time I enter my passphrase under open system authentication ubuntu locks up and my only option is to cold boot my system. Any suggestions?

(I am running 8.04 LTS on a Toshiba Satellite A215 S7422)

---

### Post by Tom--d on 2008-05-11
Yay, I can help :)

Do this in terminal (Applications > Accessories > Terminal)
```
lsusb
```

Post here the out come.

---

### Post by icdelg on 2008-05-12
Sorry my reply took so long...

lsusb output:

Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 0000:0000

---

### Post by Tom--d on 2008-05-12
O no.. 
Not the 8197 ID.. :(

I have that one.. and it took me ages to connect. 

Check your mail.

---


---
title: "Wireless not working on Dell Inspiron 910"
date: 2013-07-10
forum: New to Ubuntu
---

### Post by MakeMineAPint on 2013-07-10
I can get it to work by entering the command:-
 sudo modprobe -v b43
but I have to enter this every time I start the computer.
Is there a way/command that will load it automatically when the computer boots up?

---

### Post by kc1di on 2013-07-10
Hello MakeMineAPint,

which version of Ubuntu are you using?

please list the output of the following command in a terminal : ```
lspci
```

since you entering b43 you should be using a Broadcom wireless card.  

you should have been able to install the drivers from the additional driver tool. But it's in different places depending upon which version of Ubuntu your using.

---

### Post by kc1di on 2013-07-10
you can go to a terminal and enter the following ```
sudo gedit /etc/modules
```
once that opens simply add b43 to the bottom of the list and save the file. 

you may also want to check ```
sudo gedit /etc/modprobe.d/blacklist-bcm43.conf
```
when it opens look to make sure b43 is not on the list if it is place a # infront of that line or simply remove it and save the file.
Reboot b43 should load automaticlally.
good luck- dave

---

### Post by MakeMineAPint on 2013-07-10
Hi,
currently running Lubuntu 12.10.
Can I get back to you tomorrow with the listing of lspci as it goes on for several pages and will take me an age to type it here.
Thanks for your help so far.
Off to bed now as it's 11pm here in England.
Chris.

---

### Post by kc1di on 2013-07-10
Hi,
You do not have to type the whole thing I'm only looking for the line that looks something like this :
```
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
```

---

### Post by wildmanne39 on 2013-07-10
Hi, you could also do:
```
sudo su 
echo b43 >> /etc/modules 
exit
```
and that should fix your issue, as long as it is not blacklisted.
Thanks

---

### Post by MakeMineAPint on 2013-07-11
That's fixed it.
Thank you.

---


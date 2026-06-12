---
title: "Mobile App Under Ubuntu 8.04"
date: 2008-06-29
forum: Programming Talk
---

### Post by mr_pro_2020 on 2008-06-29
Hi 


i wanna make a mobile applicaton under linux in this project i want to do : 

connect my mobile via wifi to mu labtop and give the computer complete access to mobile HOW??!!

via my lab top i can make calles using speakers and mic all that via my  mobile

or i can give any one on any other palce to access my computer via internt and make calles using this application that will use my mobile conected to computer ... etc 

can any one help me about that 

what programming lang U Recommedn .. ithink it will be java

is this idea possible ??

but when i serach for awile i found some projects work with python and C 

bye

---

### Post by dwhitney67 on 2008-06-29
There already exists an application of which you describe... it's called [JoikuSpot]("http://www.joiku.com/?action=products&mode=productDetails&product_id=310").  Works with Nokia S60 3rd-edition phones.  I have not used it, but I will when I travel overseas.

---

### Post by mr_pro_2020 on 2008-06-29
i think this near to what i want but i want to make it for SonyEricsson or iPhone

---

### Post by coombesy on 2008-06-29
i had a bash script to do exactly that with my samsung phone. unfortunatly my hard drive has since crashed and the script is no longer there.

if i remember correctly i had two command line programs
1) scanned for all bluetooth devices
2) ftp'd to a device

I'll have a look for the programs but i think they were something like 'obex-ftp'.

hope this helps.

---

### Post by coombesy on 2008-06-29
got it...
scan for a device and get the MAC addres
-$ hcitool scan
then use obexftp to connect
$ obexftp -b 00:12:47:00:00:01 -l

both these can work with IrDA and Bluetooth.

---

### Post by firfin on 2008-10-12
> **dwhitney67 said:**
> There already exists an application of which you describe... it's called [JoikuSpot]("http://www.joiku.com/?action=products&mode=productDetails&product_id=310").  Works with Nokia S60 3rd-edition phones.  I have not used it, but I will when I travel overseas.

I have tried it. It allows you to set up your phone as an ad-hoc wifi access point. Unfortunately i cant connect to it.  Cant even see it if i dont set the channel in joiku to six or eleven.  Does anyone have any pointers.?

---


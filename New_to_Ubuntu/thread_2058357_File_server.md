---
title: "File server"
date: 2012-09-15
forum: New to Ubuntu
---

### Post by gathamar on 2012-09-15
Hi there just a quick newbee question,i used my old pc and put on it ubuntu 12.04 and works well,got it to shere on local net and took my external usb hdd´s and conected them to linux machine,used samba to share them on net but some of the folders showed emty,not all worked grate i could play vids on win 7 but cant understand those emty folders,i conected them back to win cop and thay are not emty there ,did get a litle scered i had ****** upp and large movie collections had gone but lukly not,so my question is why didint those files show and what can i do becose i realy like 12.04 UI and do apprisiate what you ppl are doin with this.
 
can se that old laptop installed with ubuntu will do anything scool kids need
 
thank you

---

### Post by Bucky Ball on 2012-09-15
> **gathamar said:**
> can se that old laptop installed with ubuntu will do anything scool kids need
 


Welcome. And yes, will do most of what many students at all levels of education require. 

What are the partitions on the external drives formatted as (filesystem) and on which machine are they showing empty? Are they showing empty or not showing at all (not mounting)? On the Ubuntu machine, you could open a terminal (Applications>Accessories>Terminal) and, with the external drives plugged in, paste this in and hit return:

```
sudo blkid
```Post the output back here, please.

---


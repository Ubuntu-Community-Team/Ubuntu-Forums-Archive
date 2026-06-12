---
title: "Which wireless card?"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Tom--d on 2008-04-26
I've had enough of my wireless card in my laptop. 

Its a Realtek rtl8187b but with a stupid id number >.<

I'm on Hardy and looking for a new card but I dont know what to look for as my wireless comes under my usb: 

Bus 007 Device 003: ID 0bda:8197 Realtek Semiconductor Corp. 


I did find this one on [here]("http://www.dabs.com/productview.aspx?Quicklinx=4JLJ&CategorySelectedId=11175&PageMode=1&NavigationKey=11175,4294960297,4294959763,50010000,4294960486")

Its a intel 3945ABG. 
Does it work out of the box?
Whats the card like?
Should I get that one?


How will I know it will work with my laptop? 


I can use ndiswrapper if I have to. I don't mind :)

---

### Post by insane_alien on 2008-04-26
intel cards are good. they play nice with linux.

---

### Post by Tom--d on 2008-04-26
Ah good :)

Another note about the card. 

I do have a USB wireless dongal (currently using it now as my internal wireless card doesn't work) works out of the box. BUT, the driver which is in the kernal is really buggy and causes my system to crash when downloading something. I solved this by using ndiswrapper. 

This will not happen to the intel card will it?

---

### Post by Mazza558 on 2008-04-26
> **Tom--d said:**
> Ah good :)

Another note about the card. 

I do have a USB wireless dongal (currently using it now as my internal wireless card doesn't work) works out of the box. BUT, the driver which is in the kernal is really buggy and causes my system to crash when downloading something. I solved this by using ndiswrapper. 

This will not happen to the intel card will it?

Search on the forums for that model, it should give some hints as to whether you'll have any problems.

---

### Post by chili555 on 2008-04-26
Search over on the Wireless forum; some have difficulty with it and some (including me) have none. There is a package you can install> I enabled the Hardy Backports repository in 'Software Sources' (tab Updates). When I hit 'close' it asked to reload the repositories, I did that.
After that I opened Terminal and entered:

sudo apt-get install linux-backports-modules-hardy-generic

That's all really, after the backports-modules were installed I tried logging in again with nm-applet and it worked.


What would concern me more is that some laptop manufacturers have a whitelist in the BIOS that only allows certain cards to be installed, otherwise, they won't boot. Before you spend any money, please Google the exact model of your laptop along with *whitelist* and make sure you are good.

This assumes you are using the Hardy Heron; otherwise, it just works. No ndiswrapper needed.

---

### Post by Tom--d on 2008-04-26
I did that and no results where found :(

But all of my hardware is intel. My guess is that it will work.

---

### Post by radiopirate on 2008-04-28
edimax with chipset RT2571 works out of box with hardy heron usb device

---


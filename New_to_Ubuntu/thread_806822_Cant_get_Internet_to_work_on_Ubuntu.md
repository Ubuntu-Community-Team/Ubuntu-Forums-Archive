---
title: "Cant get Internet to work on Ubuntu"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by 7raTEYdCql on 2008-05-25
I somehow cant get the Internet to work on myLaptop having Ubuntu7.10.

I have an ADSL router conection, and when i simply plug my laptop in i dont get my net to work.

Last time around when i tried to get the internet working i actually ruined the intrnet connection to my computer(which by default is connected to that router)

I need help please.

---

### Post by diablo75 on 2008-05-25
> **i.mehrzad said:**
> I have an ADSL router conection, and when i simply plug my laptop in i dont get my net to work.

Last time around when i tried to get the internet working i actually ruined the intrnet connection to my computer(which by default is connected to that router)

Could you be a little more clear?  What application are you opening up?  Firefox?  If so, what does it say?  Perhaps that it's in "Offline Mode"?  If that's what's happening, click on File>Offline Mode to switch it off and then try again.

If that's not the problem, try power cycling the modem after you plug the laptop into it so we can be sure the computer is being assigned an IP address by the modem.  You should also make sure your computer is not configured to assign itself a static IP address of any kind, or else the modem won't talk to it.

---

### Post by 7raTEYdCql on 2008-05-25
I get the message which is the usual message that we get when we go online of firefox.

I used to get the internet working back at campus, but somehow it doesnt seem to be the direct connect and surf down at home.

---

### Post by diablo75 on 2008-05-25
> **i.mehrzad said:**
> I get the message which is the usual message that we get when we go online of firefox.

And what message is that, exactly?

---

### Post by 7raTEYdCql on 2008-05-25
"Server not found"

This is the message that i get.

---

### Post by ettercap on 2008-06-19
hey mehrzad ...hyder here.....
try this

sudo pppoeconf 

it worked for me i use bsnl broadband......
hope this helps

---


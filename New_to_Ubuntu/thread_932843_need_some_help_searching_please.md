---
title: "need some help searching please"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by strafeshotte on 2008-09-28
i am new to ubuntu but would love nothing more than to rid myself of windows.

i have installed it on my 2 desktops and just installed it on my wifes laptop. and as i figured it didnt automatically access the internet via the internal wireless card.

my computer is a Dell Inspiron 1525. my wireless modem is a netopia (SBC DSL). i dont know what other info is need to get to what i am asking.

here is the question. (i have searched as best as i can not really knowing what i am searching for.) what exactly do i need to set it up so it can access the 'net wirelessly?

if someone could just point me in the right direction so i can research it would be fine. i dont mind working, i just dont know where to start looking.

thanks in advance.

Strafe Shotte

---

### Post by handydan918 on 2008-09-28
> **strafeshotte said:**
> i am new to ubuntu but would love nothing more than to rid myself of windows.

i have installed it on my 2 desktops and just installed it on my wifes laptop. and as i figured it didnt automatically access the internet via the internal wireless card.

my computer is a Dell Inspiron 1525. my wireless modem is a netopia (SBC DSL). i dont know what other info is need to get to what i am asking.
Well, let's start with the 1525. To find out what wireless card it has, open a terminal and do ```
lspci
```This will show a list of the various pci connected pieces. Post the specific line back here that references the wireless device.
> 

here is the question. (i have searched as best as i can not really knowing what i am searching for.) what exactly do i need to set it up so it can access the 'net wirelessly?
The other thing to try, after you establish the identity of your wireless card, is to turn off encryption at your modem/router/gateway so it doesn't trip you up in initially connecting. Once you have a connection working, you can go back and play with the encryption and see if it can be made to work.
Hope this helps.> 
if someone could just point me in the right direction so i can research it would be fine. i dont mind working, i just dont know where to start looking.

thanks in advance.

Strafe Shotte

---

### Post by strafeshotte on 2008-09-29
ok just got off work, ill figure out what wireless card im using and post it here.

thanks for the help

---


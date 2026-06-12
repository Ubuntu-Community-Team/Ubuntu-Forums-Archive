---
title: "Ubuntu 12.04 desktop network and Autorun problems."
date: 2014-04-02
forum: New to Ubuntu
---

### Post by Mike_Lavender on 2014-04-02
I have installed Ubuntu Desktop 12.04 LTS to run alongside Windows7 as my copy of window7 that I bought and paid for is somehow invalid in a few days because ei installed it on a new machine. Anyway, I installed it without a problem and I think I would very much like to use it however, I cannot get it connected to the internet. It keeps telling me that Wired connection1 is connecting to the internet and then I get a message saying that wired connection hass disconnected from the internet and I am now offline. It will do that over and over. 


In addition I have tried installing drivers from disk and when I click on run.exe (i.e. my Gigabyte motherboard utility and drivers) I get a message saying "cannot find the auto run program."

I tried loading the drivers for an ASUS wireless card, I thought it might be able to connect to my wireless router and I get the same thing.


Help! I would like to use this OS, if I ever get it to work. I am running outta time according to Microsoft they want more of my doe ray mi and I ain't givin it to em.

Mike

---

### Post by chili555 on 2014-04-03
.exe and autorun are Windows programs. We don't and can't use them in Ubuntu Linux. It is highly doubtful that your motherboard manufacturer writes Linux drivers at all.

I think you will have much better luck asking here about your wired ethernet and wireless. I'm pretty sure someone over there can help.[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336) 

Please help us by identifying your exact devices. The fast, easy way to do so is from the terminal command:```
lspci -nn | grep -e 0200 -e 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---


---
title: "Update failure messed up my Ubuntu 14.04"
date: 2014-07-19
forum: New to Ubuntu
---

### Post by indyeah on 2014-07-19
Hi guys,

Yesterday i logged in my Ubuntu after few days and saw updates worth 209 MB or so.So i clicked on install updates and they started downloading and after a while installing.
The installation went on fine untill i saw the error show up on notification panel (the one with red dot with vertical line); It said something about dependencies not found error.

So i clicked on X button on updates,tried to restart my system but it simply wont restart or shutdown.Had to manually force shutdown the system.

Anyways when i boot into Ubuntu,it boots in fine till i see the desktop but with flashing icons and cursor and no networking or wifi.I cant even shutdown/restart.All it does is show me option for logoff/sleep option.

I tried the safe mode in grub panel and tried to fix the dependencies but had no luck.

Can i repair my system without having to reinstall Ubuntu.Keep in mind i have dual boot Ubuntu with windows 8.1 on my Dell Inspiron Laptop.



TIA

---

### Post by indyeah on 2014-07-19
Solved the update and other issues by simply typing this code in the terminal.

```
sudo dpkg --configure -a
```
 
It updated my system and its back to normal now.

---


---
title: "Ubuntu CLI Commands"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by hungryOrb on 2008-11-04
Hi,
The ubuntu server I'm running seems to have crashed, only in that typing doesn't do anything.. I'm on the CLI, and changing screens with CTRL-ALT-F1 and other function keys works fine. But I cannot type anything on these screens. My GUI is not working correctly, because there doesn't seem to exist a driver to run the display properly for ubuntu :( only debian, and the screen looks like it would when it can't find a good resolution.. so like an earthquake.. so I guess I have no option but to just power down right?
It may be worth mentioning that the website it's serving still works fine. 
Thanks for consider.

---

### Post by taurus on 2008-11-04
Try to reconfigure your X server again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by handydan918 on 2008-11-04
> **hungryOrb said:**
> Hi,
The ubuntu server I'm running seems to have crashed, only in that typing doesn't do anything.. I'm on the CLI, and changing screens with CTRL-ALT-F1 and other function keys works fine. But I cannot type anything on these screens. My GUI is not working correctly, because there doesn't seem to exist a driver to run the display properly for ubuntu :( only debian, and the screen looks like it would when it can't find a good resolution.. so like an earthquake.. so I guess I have no option but to just power down right?
It may be worth mentioning that the website it's serving still works fine. 
Thanks for consider.
Depends. If you have a way to login to the server remotely, (ssh, etc.) you could do all that stuff without the downtime.
It sounds like you may be running a GUI, yes? Have you tried CTRL+ALT+BKSPC ?

---

### Post by hungryOrb on 2008-11-04
> **handydan918 said:**
> Depends. If you have a way to login to the server remotely, (ssh, etc.) you could do all that stuff without the downtime.
It sounds like you may be running a GUI, yes? Have you tried CTRL+ALT+BKSPC ?

Thanks for reply. Yes tried that. Sorry I should have mentioned that I did..

---


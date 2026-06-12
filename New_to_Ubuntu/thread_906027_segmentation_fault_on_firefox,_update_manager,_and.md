---
title: "segmentation fault on firefox, update manager, and synaptics"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by charlie1kimo on 2008-08-31
Hi everyone,
Today I installed Ubuntu 8.04 on an old computer at my home, the installation all went pretty good without any errors. But when I started Ubuntu and wanted to get the newest update by update manager, the update manager opened and then disappeared.

So I decided to use synaptics to installed my updates... and then
when I opened up synaptics, it opened and then disappeared, just
like what happened to update manager.

I was extremely curious about why and how this happened, so I went to execute synaptics under terminal. It gave me a "Segmentation Fault" on the output, and I think that explains why it disappeared.

Afterward, I tried to use firefox. Same thing happened to firefox that it opened then disappeared... I went to execute firefox under terminal and it gave me a "Segmentation Fault" as well...

Does anybody know what happened to my computer, or Ubuntu?
This old computer is AMD Athlon 1.6 GHz, with SiS 315 Pro and 1GB RAM. 

Thanks!

---

### Post by swoll1980 on 2008-08-31
Wow I never heard of anything like that happening before with so many different apps. If it were me I would open a terminal(accessories > terminal) then try  ```
sudo dpkg --configure -a
```

see if that helps or just do a reinstall

---

### Post by kellemes on 2008-08-31
> **charlie1kimo said:**
> (..) "Segmentation Fault" on the output, and I think that explains why it disappeared.

Afterward, I tried to use firefox. Same thing happened to firefox that it opened then disappeared... I went to execute firefox under terminal and it gave me a "Segmentation Fault" as well...

Is this the only output you get? Can you post the exact output here please?

---

### Post by tootlet on 2008-09-04
Greetings,
I can't start Firefox from the icon or terminal. The icon command is firefox %u and I get "Segmentation fault" from the terminal when I try "firefox". 

I tried sudo dpkg --configure -a with no joy. I tried firefox in safe mode and it still wouldn't load. 

I used synaptic manager to uninstall and then reinstalled it. Still getting my "Segmentation fault". Any suggestions warmly recieved.

Tom

---

### Post by philinux on 2008-09-04
Run this. Copy and paste it.

sudo apt-get update && sudo apt-get upgrade

---


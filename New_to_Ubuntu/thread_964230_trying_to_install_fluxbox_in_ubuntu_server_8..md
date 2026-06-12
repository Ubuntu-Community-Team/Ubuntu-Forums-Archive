---
title: "trying to install fluxbox in ubuntu server 8."
date: 2008-10-30
forum: New to Ubuntu
---

### Post by mac-i-bear on 2008-10-30
took this command from the FAQ section

sudo apt-get install fluxbox x-window-system-core xdm

and this is the server response

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package x-window-system-core is a virtual package provided by:
  xorg 1:7.3+10ubuntu10.2
You should explicitly select one to install.
E: Package x-window-system-core has no installation candidate

i'm a real newb thanks for some advice

---

### Post by bodhi.zazen on 2008-10-30
Just do

```
sudo apt-get install fluxbox
```

The dependencies (including X) should be pulled with it.

---

### Post by mac-i-bear on 2008-10-30
> **bodhi.zazen said:**
> Just do

```
sudo apt-get install fluxbox
```

The dependencies (including X) should be pulled with it.

wow it did the job - thank you 
now the next question - how do i launch it ?

---

### Post by pirattrev on 2008-10-30
run ```
fluxbox
```?

---

### Post by mac-i-bear on 2008-10-30
gives me the following error

Error: Couldn't connect to XServer

---

### Post by bodhi.zazen on 2008-10-30
Try (in order)

startx

startfluxbox

/usr/bin/startx /usr/bin/startfluxbox #(all 1 line)

---

### Post by mac-i-bear on 2008-10-30
same error

i ls the /usr/bin directory and did not see "startx"

---

### Post by bodhi.zazen on 2008-10-30
Try installing xserver-xorg

---

### Post by aeiah on 2008-10-30
i havent done this in a couple of years but i believe you need xserver-xorg as was mentioned, then you can do ```
startx && fluxbox
``` or you could try it first without xserver-xorg i suppose

---


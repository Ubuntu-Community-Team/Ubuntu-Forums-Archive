---
title: "Wireless Driver"
date: 2012-07-11
forum: New to Ubuntu
---

### Post by Raf33k9 on 2012-07-11
installed yesterday ubuntu desktop 12.04. now going to connect it to wifi network. it says wireless driver not found. what should i do now ?

---

### Post by Redblade20XX on 2012-07-11
Have  you checked the restricted drivers menu?

- Red

---

### Post by Raf33k9 on 2012-07-11
how can i do it . can you help me plz....

---

### Post by Raf33k9 on 2012-07-11
It is giving error " device not ready ( firmware missing)"

---

### Post by Redblade20XX on 2012-07-11
In the unity search menu, type in restricted drivers and see if an option comes up. Tell us what you see.

> **Raf33k9 said:**
> It is giving error " device not ready ( firmware missing)"

Yeah you need to install the wireless driver. It has the firmware the device needs.

Please post the output of  :
```
lspci
```

in the terminal. So we can identify your wireless card.

- Red

---

### Post by Raf33k9 on 2012-07-11
Host bridge: intel corporation mobile pm965/gm965/gl960 memory controller hub (rev 0c). 
Lot of lines like this. Can't post all from cell phone.

---

### Post by Redblade20XX on 2012-07-11
> **Raf33k9 said:**
> Host bridge: intel corporation mobile pm965/gm965/gl960 memory controller hub (rev 0c). 
Lot of lines like this. Can't post all from cell phone.

Okay. Can you tell us the details of the computer? Name,manufacture, etc.
Is it a desktop or a laptop?

- Red

---

### Post by Raf33k9 on 2012-07-11
Laptop. Dell Inspiron 1525. Intel Core 2 duo.

---

### Post by Redblade20XX on 2012-07-11
> **Raf33k9 said:**
> Laptop. Dell Inspiron 1525. Intel Core 2 duo.

There are multiple wifi cards for your laptop so I'll need you to find out which one.
In the terminal, type: 
```
**sudo lshw -C network**
```

and look for a description called "wireless interface".
Under that there should be a label for vendor and one for product.
Post both entries.

- Red

---


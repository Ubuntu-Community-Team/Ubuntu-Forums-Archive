---
title: "No information"
date: 2012-05-19
forum: New to Ubuntu
---

### Post by concerro on 2012-05-19
I installed Ubuntu, but I made the swap space too big. I installed gparted, and I deleted the old swap space and made a new partition.  That went well.

I logged into Ubuntu, and I am trying to follow online instructions to make Ubuntu recognize the new partition as the  swap space. I am told to right click on the new drive so I can get the UUID or the path, but when I click  a drive all I get is 

Lock to Launcher
Open 
Format
Safely Remove (it is a USB HD)
Unmount.

Was I supposed to get the UUID from gparted?

---

### Post by Cheesemill on 2012-05-19
To get the UUID open a terminal and type:
```
blkid
```

---

### Post by concerro on 2012-05-19
> **Cheesemill said:**
> To get the UUID open a terminal and type:
```
blkid
```

Nothing happened. What else do I type?

---

### Post by Cheesemill on 2012-05-19
Sorry, try:
```
sudo blkid
```

---

### Post by concerro on 2012-05-19
> **Cheesemill said:**
> Sorry, try:
```
sudo blkid
```

Thanks. :)

---


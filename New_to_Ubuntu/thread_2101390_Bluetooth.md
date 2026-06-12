---
title: "Bluetooth"
date: 2013-01-04
forum: New to Ubuntu
---

### Post by aweshucks78 on 2013-01-04
Who knows how to turn on bluetooth in Ubuntu 12.01

---

### Post by aweshucks78 on 2013-01-04
How do I turn on bluetooth in Ubuntu 12.01?

---

### Post by remarks999 on 2013-01-04
I simply "right click" on the bluetooth icon and select "turn on bluetooth". :) 

Is your bluetooth device being properly detected?

---

### Post by aweshucks78 on 2013-01-04
How does one check to see if its properly detected?

---

### Post by Vakman on 2013-01-04
Try:
```
sudo /etc/init.d/bluetooth restart
```

---

### Post by howefield on 2013-01-04
Duplicate threads merged.

---

### Post by Vakman on 2013-01-04
Is it a USB bluetooth device or integrated?

Put the output of: ```
lspci
```

> **howefield said:**
> Duplicate threads merged.

I was wondering where the other posts came from :lolflag:.

---

### Post by aweshucks78 on 2013-01-04
> **Thisislaw said:**
> Is it a USB bluetooth device or integrated?

Put the output of: ```
lspci
```

I was wondering where the other posts came from :lolflag:.
it's intergrated, and both sudo restart and start did'nt work either. I'm stumped

---

### Post by remarks999 on 2013-01-04
What happens when you perform the following? 

```
hciconfig -a
```

---

### Post by aweshucks78 on 2013-01-04
This sounds dumb, but I cannot for the life of me get my bluetooth to turn on. Can anyone help.

---

### Post by howefield on 2013-01-04
Merged again, please desist in opening new threads with the same question.

It won't help the members who try to help you if there are several independant threads open.

---

### Post by remarks999 on 2013-01-04
> **remarks999 said:**
> What happens when you perform the following? 

```
hciconfig -a
```

This needs to be done in terminal...access it by holding ctrl and alt and T

---

### Post by aweshucks78 on 2013-01-04
its checked but neither command you gave me in terminal made any indication that they took

---

### Post by aweshucks78 on 2013-01-04
nothing happens

---

### Post by remarks999 on 2013-01-04
So, to confirm, you didn't see anything similar what I've posted below? 

```
username@computername:~$ hciconfig -a
hci0:	Type: BR/EDR  Bus: USB
```

Are you sure you have bluetooth? You should have some sort of output, but if there's no hci*X* then no bluetooth is found.

---


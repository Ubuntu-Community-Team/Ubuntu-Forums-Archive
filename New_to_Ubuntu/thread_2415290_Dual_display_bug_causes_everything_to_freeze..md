---
title: "Dual display bug causes everything to freeze."
date: 2019-03-23
forum: New to Ubuntu
---

### Post by kajob on 2019-03-23
My external display is **LG 25UM58.**


I'm connecting to it over a hdmi cable. It extends my laptop display properly when in landscape, but causes my screen to freeze when put in vertical.

Before it was still buggy but it behaved differently. The screen would just turn black and then the setup would revert after about 20 seconds. However, after completing the partial upgrade this morning, I tried to connect the display in portrait mode again to see if the problem had been fixed but it just froze my screen.

```
jmw16@jons-pc:~$ uname -a
Linux jons-pc 4.18.0-10-generic #11-Ubuntu SMP Thu Oct 11 15:13:55 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

```
jmw16@jons-pc:~$ sudo dmidecode | grep -A 9 "System Information"
System Information
    Manufacturer: Hewlett-Packard
    Product Name: HP Pavilion 15 Notebook PC
    Version: 0896100000304100000620100
    Serial Number: 5CD3442G3Z
    UUID: 33444335-3434-4732-335A-A0D3C152A8CE
    Wake-up Type: Power Switch
    SKU Number: F4T58EA#ABU
    Family: 103C_5335KV G=N L=CON B=HP S=PAV X=Null 

```

---

### Post by kajob on 2019-03-26
Does anyone know how to fix this?

---


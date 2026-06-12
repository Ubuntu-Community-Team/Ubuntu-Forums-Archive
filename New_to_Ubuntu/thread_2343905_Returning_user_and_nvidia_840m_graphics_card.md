---
title: "Returning user and nvidia 840m graphics card"
date: 2016-11-20
forum: New to Ubuntu
---

### Post by Morten ML on 2016-11-20
Hello

I haven't been using Ubuntu in a couple of years now, but now i am returning. I have a Lenovo Z50-70 with a nvidia 840m graphics card that i can't figure out if ubuntu is using or not. I am currently using nvidia 375 version 375.20. How can i check if ubuntu is using the 840m graphics card and not the onboard intel graphics?

Thx for your help.

---

### Post by Bashing-om on 2016-11-20
Morten ML; Hello and Welcome back :)

To see what nVidia drivers are installed:
```

dpkg -l | grep -i nvidia

```
to see that a driver is installed:
```

sudo lshw -C display

```
and look in the configuration line.

To see what X is setting up for the GUI interfacing :
```

less /var/log/Xorg.0.log

```

To know the driver availability status:
```

cat /var/log/gpu-manager.log

```
[INDENT][INDENT]hope this helps[/INDENT][/INDENT]

---

### Post by Morten ML on 2016-11-20
Thank you Bashing-om

It does indeed work, so i am happy. Thx for the terminal commands. It may sound weird but i actually missed the terminal while using windows.

---

### Post by Bashing-om on 2016-11-20
Morten; Good deal.

> **Morten ML said:**
> Thank you Bashing-om

It does indeed work, so i am happy. Thx for the terminal commands. It may sound weird but i actually missed the terminal while using windows.


I can not help it -- I am terminal ( minded) .

[INDENT][INDENT]<- the universal language
[/INDENT][/INDENT]

---


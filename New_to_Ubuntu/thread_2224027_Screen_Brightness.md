---
title: "Screen Brightness"
date: 2014-05-14
forum: New to Ubuntu
---

### Post by retriever on 2014-05-14
I use the F5 and F6 keys on my computer, but I wanted to know if there was a setting that I could use to permanently set my screen brightness.

Thanks!

---

### Post by keratos2 on 2014-05-14
what do you mean "permanently" - just dont use the F5/6 keys !!?!! the default screen brightness is set under the power management menus where you can define screen brightness when: On A/C ; On battery; low battery. If you dont touch F5/6 then you get a "permanent" solution !

---

### Post by retriever on 2014-05-14
> **keratos2 said:**
> what do you mean "permanently" - just dont use the F5/6 keys !!?!! the default screen brightness is set under the power management menus where you can define screen brightness when: On A/C ; On battery; low battery. If you dont touch F5/6 then you get a "permanent" solution !

[s]snip[/s]"Permanently" means between sessions, and I have tried the "Brightness/Lock" feature, and "Power Management", but when I reboot my laptop the screen brightness is back to 100%.

---

### Post by Toz on 2014-05-14
@retriever, can you run the following command and report back the results? It will identify your currently active backlight interface(s). If we can manually manipulate the brightness we can add a command to /etc/rc.local to set the brightness to a value of your choice at boot:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```

---


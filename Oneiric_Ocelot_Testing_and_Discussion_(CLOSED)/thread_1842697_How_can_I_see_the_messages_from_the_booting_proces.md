---
title: "How can I see the messages from the booting process?"
date: 2011-09-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lobo_tuerto on 2011-09-12
Hello guys,


How can you see the log with all the messages that appears when you are booting your PC? the ones that say [OK] or [FAIL].

---

### Post by chakra_888 on 2011-09-12
The file is located at** /var/log/boot.log**

---

### Post by lobo_tuerto on 2011-09-12
Thank you, although that log seems incomplete. Only seven lines, while in the booting screen appears a lot more.

Also, where can I see the same messages but when you turn the computer off? I have seen some "System V" messages when I'm turning my PC off, is this normal?

---

### Post by ronacc on 2011-09-12
if you want to see them during boot remove quiet from the bootline in /boot/grub/grub.cfg

---

### Post by lobo_tuerto on 2011-09-12
I did that already, but it happens so fast that I cannot read them properly.

Also, what's the key to go back to that screen? Ctrl+Alt+F1 through F6 doesn't take me back there.

---

### Post by cariboo on 2011-09-12
If you want to check the log after you've booted up, just open a terminal and type:

```
dmesg | less
```

Then use the space bar to go to the next page. Press q to quit.

---


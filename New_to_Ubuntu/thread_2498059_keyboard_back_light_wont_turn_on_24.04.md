---
title: "keyboard back light wont turn on 24.04"
date: 2024-05-28
forum: New to Ubuntu
---

### Post by wamiko on 2024-05-28
[SIZE=3][FONT=times new roman]running Ubuntu 24.04 no partition
laptop is dell latitude 5490
[COLOR=#000000]Intel Core i5-8350U Quad Core CPU @ 1.9 Ghz
16 GB RAM (DDR4 @ 2400Mhz)
ok! so i went through several iterations of Ubuntu very briefly before settlin on 24.04 and they all had their own quirks. But the keyboard back light turned on in the version up to 23.10 but when i upgraded to 24.04 it stopped working and because 24.04 is relatively new there arent a lot articles about this issue on this specific iteration of Ubuntu. 

to be clear, the back light works. it turns on when i power down the laptop. I'm aware that this has happened to other people on previous versions of Ubuntu but im still new to Ubuntu and i dont know if the code fixes for those versions of Ubuntu will work for this version of Ubuntu[/COLOR][/FONT][/SIZE]

---

### Post by ActionParsnip on 2024-05-29
What does "no partition" mean in this context please?

---

### Post by ActionParsnip on 2024-05-29
If you run:
```

echo 1 | sudo tee /sys/class/leds/dell::kbd_backlight/brightness > /dev/null

```
Does it change the brightness?

---

### Post by wamiko on 2024-06-14
thank you! the code fix from ActionParsnip was an immediate fix. This is why I love Ubuntu. Thanks guys!

---


---
title: "Any power saver mode?"
date: 2017-01-18
forum: New to Ubuntu
---

### Post by yoshiki2 on 2017-01-18
Any power saver mode I can use on ubuntu? or any dark theme mode? thanks

---

### Post by MartyBuntu on 2017-01-18
I just wanted to mention, on the point of dark themes...they are not actually more energy efficient than lighter themes.
"Dark" is not the absence of light. It actually takes CPU/GPU computations to display "black".

---

### Post by vasa1 on 2017-01-18
> **MartyBuntu said:**
> I just wanted to mention, on the point of dark themes...they are not actually more energy efficient than lighter themes.
"Dark" is not the absence of light. It actually takes CPU/GPU computations to display "black".
+1 to that.

I think for some newer cell phone screens, dark themes may be beneficial but I'm not sure that such screens are available for even laptops, let alone desktops.
> The amount of power the display consumes varies significantly depending on the color and brightness shown. As an example, one commercial QVGA OLED display consumes 0.3 watts while showing white text on a black background, but more than 0.7 watts showing black text on a white background, while an LCD may consume only a constant 0.35 watts regardless of what is being shown on screen.[11] Because the black pixels actually turn off, AMOLED also has contrast ratios that are significantly better than LCD.Source: [https://en.wikipedia.org/wiki/AMOLED](https://en.wikipedia.org/wiki/AMOLED)

---

### Post by Impavidus on 2017-01-19
LCDs consume, at least theoretically, slightly more power when displaying dark colours compared to bright. But when the brightest pixel of the screen gets darker, the LCD can save energy by reducing backlight. My TV screen does this, which can be somewhat annoying when watching a very dark scene with occasional subtitles. Other types of screen consume more power when showing more light. But I expect the power consumption of most computers is dominated by CPU and GPU, if you have a big one of those.

There is a package in the repositories named laptop-mode-tools, which promises to save a bit of energy. I never tried it myself and never heard much about it.

Some computers have hybrid graphics, both a powerful (both in performance and energy use) graphics card and light on-board graphics. Switching the powerfull graphics card off when you don't need it saves much energy. I've got no experience with those, but if your computer has hybrid graphics, search for more information on how to handle that.

---


---
title: "Slow loading of Ubuntu programmes and pages"
date: 2012-06-09
forum: New to Ubuntu
---

### Post by simoncdl on 2012-06-09
Just installed 12.04 on my laptop. I wiped out windows 7 completely. My lapto is an HP Pavilion g series with 500gb internal memory and 64 bit.  Beyond that i don't know.
I am having issues with very slow page turning capabilities on this Ubuntu. Clicking on a window can sometimes take a while to open, even when not on the Internet. Occasionally the screen will darken before coming back a few moment slater. Maybe it's me but i kind of expected a little more speed as my laptop is only about 8 months old and my wifes one is about 4&1/2 years old and has no problems with her Ubuntu
Any help gratefully received but please keep it simple, child speak will be welcomed :-)

---

### Post by critin on 2012-06-09
One thing you could try is Additional Drivers.  Run it and see what it recommends.

---

### Post by numand on 2012-06-09
@simoncdl, push ctrl+alt+t keys to open terminal. Then copy and paste ```

sudo sed -i 's/NoDisplay=true/NoDisplay=false/' /etc/xdg/autostart/*.desktop
```After this, you can disable some applications to start at bootup so you can save some RAM. 

For more suggestion, I should take a look at ```
lspci
``` output.

---


---
title: "ubuntu, nvidia, dual monitors"
date: 2012-01-06
forum: New to Ubuntu
---

### Post by daveyman123 on 2012-01-06
Hi, this is my first post here
Im new to linux and currently using ubuntu 11.10 and trying to set up dual monitors. Isearched and tinkered for a few hours and this is where I, as are a few other people in this particular thread, am stuck:

On logging in, the second display briefly shows my desktop background, then clears to white blank display. Right clicking on this causes the desktop background to show again, but I can't get any applications to run in it at all.

If I select "Home folder", the second display once again blanks out.

The solution that was provided is this but im still unclear about where to go from here in order to set up another monitor:

There is a working patch and the dev team is aware of the problem and solution.


You will have to compile Nautilus from source, or wait until the fix gets added to your repo.




appreciate any help! thanks

---

### Post by josephmills on 2012-01-06
Hi there I am also having trouble with this to get it to work I have had to go back to using nouvea or how ever you spell it. Worked but then my screen started flickering like crazy so I installed nvidia from ubuntu repo = nothing then I installed xswat repo = nothing I then went and installed the driver from the site and nothing. could you please open your terminal and type in ```
lspci -nn | grep VGA
``` then paste here I am wondering if you have the chip-set as me if so then bug file time :)

here is mine 
```
02:00.0 VGA compatible controller [0300]: nVidia Corporation C77 [GeForce 8200M G] [10de:0845] (rev a2)
```

---

### Post by daveyman123 on 2012-01-07
01:00.0 VGA compatible controller [0300]: nVidia Corporation GF110 [GeForce GTX 560 Ti] [10de:1200] (rev a1)

---

### Post by daveyman123 on 2012-01-07
bump. still unresolved.

---

### Post by David Crockett on 2012-01-09
Hi,

I cant get my dual monitor system to go as well.      It worked fine in 11.04.  But since 11.10 the second monior is a large paperweight.

here is my card:

01:00.0 VGA compatible controller [0300]: nVidia Corporation NV18GL [Quadro NVS 280 SD] [10de:018a] (rev a2)

Cheers,
DC

---


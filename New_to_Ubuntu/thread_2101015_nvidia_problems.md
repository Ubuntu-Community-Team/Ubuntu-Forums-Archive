---
title: "nvidia problems"
date: 2013-01-03
forum: New to Ubuntu
---

### Post by sendy on 2013-01-03
edit: add some details
hi guys i have nvidia problems :( i dont know what happen because when i run warcraft with optirun it display errors then if i type optirun glxgears, it displays the same errors as when im running warcraft .. :
```
 optirun glxgears
[   25.424416] [ERROR]The Bumblebee daemon has not been started yet or the socket path /var/run/bumblebee.socket was incorrect.
[   25.424460] [ERROR]Could not connect to bumblebee daemon - is it running?

```how to fix this :(, it suddenly happens like that 
 sry i forgot to add details:
 ubuntu 12.04 64 bit
 NVIDIA geforce GT 630M 

added new details:

i use lspci | grep VGA from google then:
```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
```it seems my laptop does not detect my Nvidia GeForce GT 630M anymore :'(
it worked before i knew that my optirun is broken, i didnt do anything... i just installed geany recently and make a virtual host and oh yes, i use ctrl + alt + sys req + REIUSB because i had my laptop freeze few hours ago


i saw in google that i should reinstall bumblebee, but im not sure.. since i dont know how to do so, so i googled again how to reinstall bumblebee, again every post related about reinstalling it has different problem, so i dont know to use which method.

**SOLVED**
  what i have done : i frustrated, i boot ubuntu live cd and try ubuntu, use      lspci | grep VGA
  it detected my 2 vga:
  ```
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09) 01:00.0 VGA compatible controller: NVIDIA Corporation Device 0de9 (rev a1)
```   i slept, then i woke up in the morning, hope for magic happens, AND  YES IT DOES, use optirun and it works! it also detected my VGA with  lspci | grep VGA
  note: **i already had bumblebee installed and it worked before my laptop suddenly didnt recognize my vga..**



two questions :
  
[LIST]
[*]why did that happen? (more specific why did that nvidia problem arised?) is it because when i use ctrl + alt + sys req + REIUSB ?? yes i typed it REIUSB and not REISUB..
[*]why did my solution work?
[/LIST]

---

### Post by sendy on 2013-01-03
bump.. sry guys i forgot to add details because of i panicked T_T, now i added details in  my thread, please look at it :(

---

### Post by sendy on 2013-01-03
added new sad details again:(

---

### Post by Calinou on 2013-01-03
Can't you read error messages? Make sure Bumblebee is started. Maybe try reinstalling it, too. Also, it's REISUB, not REIUSB.

---

### Post by sendy on 2013-01-03
bump.. solved! but i have 2 more questions, please see my first post

---


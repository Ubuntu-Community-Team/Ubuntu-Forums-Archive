---
title: "USB - LED On &amp; Off programming"
date: 2012-07-21
forum: Programming Talk
---

### Post by snowz on 2012-07-21
[]("http://i.imgur.com/yyDch.png")
[LIST]
[*]LED
[*]USB cable
[*]COMPUTER (with Ubuntu 12.04)
[/LIST]
How to make the LED light on & off with the help of programming?

---

### Post by ofnuts on 2012-07-21
This would mean to be able to power off/on the USB port. AFAIK There is no provision for this. However, on some laptops you can control the various lights, on my Thinkpad it's easy to control  by software the LED at the top of the screen (it's meant to light the keyboard) as well as various indicator lights. 
```

# blink the keyboard light, must be run as root
for i in $(seq 1 20); do sleep .2; echo on >/proc/acpi/ibm/light; sleep .2 ;echo off  >/proc/acpi/ibm/light;done

```

---

### Post by Bachstelze on 2012-07-21
I'm not an expert on USB, but I don't think this is possible with just a LED. USB is complicated, so you might need a controller and whatnot. It would be simpler with a serial or parallel port (but you will still need to throw in a reisistor to avoid frying your port and/or LED).

---

### Post by snowz on 2012-07-21
Sounds a bit complicated :-k

---

### Post by trent.josephsen on 2012-07-21
> **snowz said:**
> Sounds a bit complicated :-k
A bit. Do it anyway. You'll learn a lot.

---

### Post by snowz on 2012-07-22
I realise that yeah, it must be an awesome experience to make this work properly. And later on, when understanding how it works and how its done, make a sequence of on's & off's so the led blinks. That must be great to accomplish :)

---


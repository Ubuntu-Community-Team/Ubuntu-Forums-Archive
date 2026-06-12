---
title: "4Gb shows 3.8, 8Gb shows 7.7"
date: 2014-03-19
forum: New to Ubuntu
---

### Post by Dr. McKay on 2014-03-19
I have Ubuntu 13.10 64-bit installed on a Core2quad desktop with 4Gb of RAM and a nVidia 9800gtx card.
Until yesterday, I had 4G  of RAM and in system settings, it only showed 3.8gb.

Yesterday, I added 4Gb for a total of 8 and now, Ubuntu shows only 7.7 Gb.

Can someone explain this to me ?  If I had an computer with integrated graphics, then it'd be logical since the graphics take up a portion of the RAM, but I have a dedicated card...

---

### Post by Korkel on 2014-03-19
I got the same problem, got 12GB ram and it shows me only 11,6. I think that 0,4gb is use automatic for swap or something.

---

### Post by mastablasta on 2014-03-19
post results of commands:

```
free -m


```and maybe 

```
top
```

wrap them in code tags (the # icon) so we can read them more easilly.

---

### Post by Dr. McKay on 2014-03-19
Come to think of it, sometime ago, I remember installing Ubuntu 64-bit (can't remember which version, must have been 12.04 or something) on a Core2duo iMac with 4Gb of RAM and a dedicated Radeon HD2600 card with system settings reporting the exact same 3.8gb installed. Very strange indeed.
System monitor in OS X gave me the full 4Gb, no question...

---

### Post by Korkel on 2014-03-19
> **Dr. McKay said:**
> Come to think of it, sometime ago, I remember installing Ubuntu 64-bit (can't remember which version, must have been 12.04 or something) on a Core2duo iMac with 4Gb of RAM and a dedicated Radeon HD2600 card with system settings reporting the exact same 3.8gb installed. Very strange indeed.
System monitor in OS X gave me the full 4Gb, no question...
Pleas follow the steps given above if you want help:
> **mastablasta said:**
> post results of commands:

```
free -m


```and maybe 

```
top
```

wrap them in code tags (the # icon) so we can read them more easilly.

---

### Post by Dr. McKay on 2014-03-19
> **Korkel said:**
> Pleas follow the steps given above if you want help:

I will, but I'll do it tonight, I'm at work right now...

---

### Post by varunendra on 2014-03-19
The amount of memory you see missing is usually used as 'Video buffer' by the graphics card. I'm not sure if it happens when you have a dedicated graphics card, but I know that the onboard ones share the memory from the installed RAM.

If you would be happy by seeing the size reported to the system (not the 'usable size', which is what you are seeing currently), use any of these commands -
```
sudo lshw -C memory
sudo dmidecode -t memory
```

---

### Post by slickymaster on 2014-03-19
There are numerous factors that influence in the amount of usable memory shown.

When the system loads it needs a required amount of memory for everything to function as smooth as it can. If you have 512MB the system will not reserve a lot since it will notice the lack of memory. If you have 1GB or 2GB the amount reserved gets bigger. The limit for 32 Bit is 4GB from which it reserves between 200MB and 1GB of RAM so everything can run smooth. So you would be left with a total usable memory between 3.0GB to 3.8GB. Depending on the hardware, integrated devices (Integrated video card, sound card, network card, etc...), amount of devices connected, the amount reserved will change.

---

### Post by ajgreeny on 2014-03-19
Presumably if your cpu has a graphic chip integrated onit, as most seem to these days, that will take at least some of the available ram unless it has been disabled in the BIOS in favour of the dedicated card.

I could be wrong, of course, as I'm not a hardware expert.

---

### Post by Dr. McKay on 2014-03-20
> **Korkel said:**
> Pleas follow the steps given above if you want help:

Haven't had time yesterday, will do it tonight...

---

### Post by buzzingrobot on 2014-03-20
Memory can be measured in decimal units or hexedecimal units.  A measurement done in one will show slightly different results than a measurement done in the other.

---

### Post by codingman on 2014-03-20
That is probably the amount that is usable, and as buzzingrobot said, it can be measured in both hexadecimal and decimal.

---


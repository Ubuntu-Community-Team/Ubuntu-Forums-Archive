---
title: "Ubuntu and HP"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by thomashome on 2008-09-07
Ok so I am not a Beginner but hear are some things

I have a HP Pavilion dv9500em that is 1 year old and the wi fi is not working it does not work with ubuntu or windows xp. But when I put HP's Vista manufacture disk it works after a night of installing. But when I try normal vista it does not work. What could I do to get it running on all systems!

---

### Post by Peter09 on 2008-09-07
Can you post the output of

```
sudo lshw -C network
```

and

```
ifconfig
```

---

### Post by teeleef on 2008-09-07
thomashome,  did you check that the wireless slider button is switched to on?  I know that's an obvious thing to check, but when I put Ubuntu on mine I'd accidently caught the switch by mistake and was bamboozeled when it didn't work...Doh!! 

I have a HP9500 series laptop and all runs perfectly using Gutsy.


Teeleef

---

### Post by Crafty Kisses on 2008-09-07
That's really weird, usually HP is very well supported in Ubuntu. As suggested above check your Wireless switch on your laptop, I'd also like to see the results of this output:
```
iwconfig
```

---

### Post by thomashome on 2008-09-11
Thanks everybody anyway!

I got it working under Ndiswrapper I followed a guide for a Apple MacBook!
Just needed to type My wireless card into google!

---

### Post by akbeancounter on 2008-09-11
> **thomashome said:**
> I have a HP Pavilion dv9500em that is 1 year old and the wi fi is not working it does not work with ubuntu or windows xp.

I know you've already solved the problem, but as the proud owner of a dv6636nr, I'm surprised you had a problem.  My laptop's wireless driver automatically installed the first day; we did two "install updates -> restart" cycles, then a pop-up asked if I wanted to install proprietary drivers for my nVidia graphics card and my Broadcom wireless card.  I didn't have to ndiswrapper or anything.

-- A.

---


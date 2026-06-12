---
title: "too hot"
date: 2012-08-18
forum: New to Ubuntu
---

### Post by amrosama77 on 2012-08-18
hello,

Psensor program show that my pc temp is 91 some times 95
is there any risk in this ...?

Note #1. I set on hp labtop pavilion g6
Note #2. the fan is working I can hear it.

---

### Post by 25tom on 2012-08-18
Sounds too hot to me... as far as I'm aware, most computers automatically shut off at 100 degrees. My advice is to buy a laptop cooling gel pad, which helps to dissipate the heat.

Edit: That's 100 celsius

---

### Post by mtron on 2012-08-18
hello!

you need to power down the radeon gpu, see this thread for more: [http://ubuntuforums.org/showthread.php?t=2039443](http://ubuntuforums.org/showthread.php?t=2039443)

---

### Post by 25tom on 2012-08-18
> **mtron said:**
> hello!

you need to power down the radeon gpu, see this thread for more: [http://ubuntuforums.org/showthread.php?t=2039443](http://ubuntuforums.org/showthread.php?t=2039443)

 I see that the problem is deeper than I thought... cooling pad seems not to be the solution...

---

### Post by robtygart on 2012-08-18
Mine usually reads around 125+F

---

### Post by amrosama77 on 2012-08-18
Thank you all,

now when I install my ATI driver the temp is about 71 C:D

---

### Post by ruslan kim on 2012-08-18
> **amrosama77 said:**
> Thank you all,

now when I install my ATI driver the temp is about 71 C:D

Hey,
I had the same problem with my HP Pavillion g6 when I installed Ubuntu. Kindly see the solution here:
[http://ubuntuforums.org/showthread.php?t=2039443](http://ubuntuforums.org/showthread.php?t=2039443)

---

### Post by amrosama77 on 2012-08-18
Thank you,

I installed the graphic driver and it didn't go above 90c now

---

### Post by robtygart on 2012-08-19
So I don't need to start a new thread... How hot is too hot? Mostly for processors?

```
rob@rob-mobile:~$ sensors -f
acpitz-virtual-0
Adapter: Virtual device
temp1:       +131.0°F  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +143.6°F  
Core1 Temp:  +149.0°F  

nouveau-pci-0090
Adapter: PCI adapter
temp1:       +192.2°F  (high = +212.0°F, crit = +230.0°F)

rob@rob-mobile:~$ sensors -f
acpitz-virtual-0
Adapter: Virtual device
temp1:       +132.8°F  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +141.8°F  
Core1 Temp:  +149.0°F  

nouveau-pci-0090
Adapter: PCI adapter
temp1:       +188.6°F  (high = +212.0°F, crit = +230.0°F)

rob@rob-mobile:~$ 

```

---


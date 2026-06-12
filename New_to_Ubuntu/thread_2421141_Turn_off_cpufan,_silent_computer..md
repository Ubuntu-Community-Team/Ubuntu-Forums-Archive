---
title: "Turn off cpufan, silent computer."
date: 2019-06-17
forum: New to Ubuntu
---

### Post by knabbjolf2 on 2019-06-17
Hej.
In windows 10 there is several applications turning cpu fan completely off so computer is silent but how do I do it in ubuntu ? I can not use ubuntu with a noisy fan.

No one will be happier if I fry this computer by turning off cpu fan but I have not been able breaking it yet using windblows allthough Im editing lot of films and presentations for five years now. It just wont break eventhough cpu temp is up at 90*C. I think the cautions of cpu cooling and temperatures is highly exagerated, they wont break and trust me, I have been trying hard for five years as I have good backup hygiene(firewall/updates is always disabled as i have no patience with virus or updates, you only get viruses as long as you are buying updates, if you stop paying for updates & virus software all virus attacks also stops and you get a reliable efficient computer). 

If I fry this computer I will have legit excuse get rid of this and buying a new fanless silent computer.

Acer aspire es151222kw intel quad n2920. 

Any advice for scripts appreciated, and yes I could cut the cord to the cpu fan but I would prefer doing it by software as in windows 10.
 
Kindly K.Jolf.

---

### Post by dino99 on 2019-06-17
Install lm-sensors & fancontrol
[https://askubuntu.com/questions/22108/how-to-control-fan-speed](https://askubuntu.com/questions/22108/how-to-control-fan-speed)

Lm-sensors is a hardware health monitoring package for Linux. It allows you
to access information from temperature, voltage, and fan speed sensors. It
works with most newer systems.

This package contains a daemon that calculates fan speeds from temperatures
and sets the corresponding PWM outputs to the computed values. This is
useful when this feature is not provided by the BIOS or ACPI, which should
normally be the case on a laptop.

---

### Post by mastablasta on 2019-06-19
> **knabbjolf2 said:**
> 
No one will be happier if I fry this computer by turning off cpu fan but I have not been able breaking it yet using windblows allthough Im editing lot of films and presentations for five years now. It just wont break eventhough cpu temp is up at 90*C. I think the cautions of cpu cooling and temperatures is highly exagerated, they wont break a.

higher temperatures are probably less efficient
when it reaches a high enough temp it will turn off to protect itself
obviously you haven't thrown enough at it so it didn't get too hot. + it likely has a good cooler on it and it is connected to CPU with a good thermal paste.

i once had the radiator move slightly. it turn off as soon as i presented it with a more difficult app. - reason was overheating.

---


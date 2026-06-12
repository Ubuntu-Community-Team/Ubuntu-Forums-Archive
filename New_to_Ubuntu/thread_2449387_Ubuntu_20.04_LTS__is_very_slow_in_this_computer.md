---
title: "Ubuntu 20.04 LTS  is very slow in this computer"
date: 2020-08-25
forum: New to Ubuntu
---

### Post by candylovergirl on 2020-08-25
Hello,

I just installed Ubuntu 20.04 LTS in a Aspire Z1 - 601
[https://www.acer.com/ac/en/IN/content/model/DQ.SYFSI.002](https://www.acer.com/ac/en/IN/content/model/DQ.SYFSI.002)

The computer is very slow and old, I wont upgrade RAM 

Please suggest another Flavor very similar to Ubuntu 20.04 LTS but lighter (With Ubuntu Store)

I only want to Browse, Watch YT Videos, post @Twitter and check my email (Gmail and POP3) 

Thanks

Camelia

---

### Post by poorguy on 2020-08-25
Ubuntu 20.04 is pretty resource demanding so it's not going to run very well on your laptop.

Give Lubuntu 20.04 a test drive and see how it runs on your laptop.

[https://lubuntu.me/](https://lubuntu.me/)

[https://manual.lubuntu.me/stable/](https://manual.lubuntu.me/stable/)

[https://lubuntu.me/downloads/](https://lubuntu.me/downloads/)

---

### Post by mastablasta on 2020-08-26
> **candylovergirl said:**
> 
The computer is very slow and old, I wont upgrade RAM 


computer is not that old (5 years). it is more low power usage & weaker CPU machine.

passmark is 1191 (on CPU benchmark.net).

mine is old - it's 16 years old and has passmark of about 400. i can play various modern*ish* games on it due to separate GPU.

aside from CPU (that is really not that fast) your PC has 2 issues that make it slow.
[LIST]
[*]hard disk - it is a smaller one that has 5400 rpm compared to 7200 rpm from big HDD or the SSD that doesn't even spin. this is an issue because every time your system has to read from it or write to it it feels a bit slow.
[*]RAM - the biggest issue. you have 2 GB ram of which at least 0.5 Gb is probably used by GPU (Intel® HD Graphics for Intel Atom® Processor Z3700 Series). any every time you ran out of ram disk is then used which is why the system is slow.
[/LIST]


the biggest issue is actually ram and since this is ddr3 it is cheap to upgrade - you can upgrade to 4 GB which would cost you about 16 EUR. maybe 20. 

having enough ram makes a big difference because the applications you use (firefox) firefox need ram and they also use the GPU so it means GPU also needs enough RAM available to do it's job. and the PC doesn't use the disk so much when it has more RAM available. RAM is much much faster than hard disk. in other words inadequate RAM slows down the speed of computer.

remember my old PC? it has 4 GB ram and separate GPU (so it means GPU has it's own RAM and is not using PC ram). when i turn on firefox and few other things ram easily gets filled up to 3 GB and i still have space in it. so even though the PC is really old and has very slow CPU, because i have enough ram i don't really feel that and it is working well for my needs.

i also have a younger 8 year old laptop (about twice as fast CPU) that has only 2 Gb ram and that one is slow once you start firefox. i can browse and all but i can feel the lack of ram a lot. it is good enough if i just have 3 or less tabs open in firefox. and for some light games.


there are a couple of distributions that will start out with lower ram usage like Lubuntu, MX linux, AntiX or if you install only windows manager to Ubuntu (like IceWM). so you might start the PC with 120 MB or 250 MB ram instead of 500 MB+. however as soon as you start loading applications like firefox it will again fill up the ram, it will start using disk (swap) and it will again slow it down. for that reason the best solution is really to upgrade the ram. 

if you are short on cash you might get a used stick for less. if this PC works for your needs and if you do not experience any other issues it seem to be good enough to be worth a small investment. another good option is to get a newer used business laptop PC. or a Ryzen laptop. they sell new Ryzen 3 laptops with 8 Gb ram for a little over 300 EUR and they will leave this acer in the dust.

---

### Post by candylovergirl on 2020-08-26
> **poorguy said:**
> Ubuntu 20.04 is pretty resource demanding so it's not going to run very well on your laptop.

Give Lubuntu 20.04 a test drive and see how it runs on your laptop.

[https://lubuntu.me/](https://lubuntu.me/)

[https://manual.lubuntu.me/stable/](https://manual.lubuntu.me/stable/)

[https://lubuntu.me/downloads/](https://lubuntu.me/downloads/)

Thank you I will continue with Ubuntu 20.04 LTS in this machine

@mastablasta is right

> If I start loading applications like firefox it will again fill up the ram, it will start using disk (swap) and it will again slow it down. for that reason the best solution is really to upgrade the ram. 

> **mastablasta said:**
> computer is not that old (5 years). it is more low power usage & weaker CPU machine.

passmark is 1191 (on CPU benchmark.net).

mine is old - it's 16 years old and has passmark of about 400. i can play various modern*ish* games on it due to separate GPU.

aside from CPU (that is really not that fast) your PC has 2 issues that make it slow.
[LIST]
[*]hard disk - it is a smaller one that has 5400 rpm compared to 7200 rpm from big HDD or the SSD that doesn't even spin. this is an issue because every time your system has to read from it or write to it it feels a bit slow. 
[*]RAM - the biggest issue. you have 2 GB ram of which at least 0.5 Gb is probably used by GPU (Intel® HD Graphics for Intel Atom® Processor Z3700 Series). any every time you ran out of ram disk is then used which is why the system is slow. 
[/LIST]


the biggest issue is actually ram and since this is ddr3 it is cheap to upgrade - you can upgrade to 4 GB which would cost you about 16 EUR. maybe 20. 

having enough ram makes a big difference because the applications you use (firefox) firefox need ram and they also use the GPU so it means GPU also needs enough RAM available to do it's job. and the PC doesn't use the disk so much when it has more RAM available. RAM is much much faster than hard disk. in other words inadequate RAM slows down the speed of computer.

remember my old PC? it has 4 GB ram and separate GPU (so it means GPU has it's own RAM and is not using PC ram). when i turn on firefox and few other things ram easily gets filled up to 3 GB and i still have space in it. so even though the PC is really old and has very slow CPU, because i have enough ram i don't really feel that and it is working well for my needs.

i also have a younger 8 year old laptop (about twice as fast CPU) that has only 2 Gb ram and that one is slow once you start firefox. i can browse and all but i can feel the lack of ram a lot. it is good enough if i just have 3 or less tabs open in firefox. and for some light games.


there are a couple of distributions that will start out with lower ram usage like Lubuntu, MX linux, AntiX or if you install only windows manager to Ubuntu (like IceWM). so you might start the PC with 120 MB or 250 MB ram instead of 500 MB+. however as soon as you start loading applications like firefox it will again fill up the ram, it will start using disk (swap) and it will again slow it down. for that reason the best solution is really to upgrade the ram. 

if you are short on cash you might get a used stick for less. if this PC works for your needs and if you do not experience any other issues it seem to be good enough to be worth a small investment. another good option is to get a newer used business laptop PC. or a Ryzen laptop. they sell new Ryzen 3 laptops with 8 Gb ram for a little over 300 EUR and they will leave this acer in the dust.

Thank you very much, I don't have the money and the need at this moment to get a newer used business laptop PC, but after reading your reply, I changed my mind, I will buy more RAM  :cool:

Camelia

---


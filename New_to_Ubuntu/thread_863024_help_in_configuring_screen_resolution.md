---
title: "help in configuring screen resolution"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by arda_sar on 2008-07-18
Hi all,

I'm new to Ubuntu (linux) and I do not know much a bout the command line.
At the moment I have AMD64 Athlon and I instaled the Ubuntu 8.04 LTS 64-bit. 
I have 2 monitors (my graphic card supports 2 monitors)
***My monitor is Hp 15 inch LCD and the other one is LG 24 inch LCD

At the moment I'm not able to configure my monitors screen resolution indipendently (I'm stucked with 800 x 600). How do I make it so my I can configure my monitor resolution independently to it's max potential resolution?

Any baby steps is greatly appreciate it.

Thank you

Arda

---

### Post by arda_sar on 2008-07-18
anyone at all....?:(

---

### Post by arda_sar on 2008-07-19
pls help.....:cry::cry::cry:

---

### Post by philinux on 2008-07-19
What are your full specs.

Also 

Have a look in System>Admin>Hardware Drivers.

---

### Post by arda_sar on 2008-07-19
how do I get my full spec?
sorry I know my question is very basic, but I'm just totally new.

thanks

---

### Post by rockerphil on 2008-07-19
to the best of my knowledge (may be untrue) you can't configure the screen resolution for the monitors seperately. but you can configure your screen resolution with this command, it is to configure monitor properties

sudo dpkg-reconfigure -phigh xserver-xorg

just go through the steps with that and you should be able to set your resolution to the highest resolution your monitor(s) support, hope it helps,

Phil

---


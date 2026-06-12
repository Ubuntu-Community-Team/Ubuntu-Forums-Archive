---
title: "Fresh install will only boot via recovery mode"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by Nately on 2008-11-19
Hello,

I have installed Ubuntu 8.04 on my (old) dell inspiron 1100 laptop. Works great...when i get it to start right. At first i thought my booting problems were related to some messing around on my part so i did a complete fresh install. The install works fine and so does the live cd.
The only problem i have is that the laptop will not boot normally, i get a black screen without any cursor or whatever. The only way i get it to boot is by starting in the recovery mode and than, without doing anything in this mode choose to resume normal boot.
I have searched in some logs but they give so much information and i don't know what to look for. Who can send me in the right direction?

Thanks, Nately.

---

### Post by dracayr on 2008-11-19
when exactly while booting do you get the black screen? 

in the boot menu, where you can choose between recovery and normal boot, select the normal boot (bud don't press enter), press e, and then remove the 'splash' from the line beginning with "kernel /boot..." (the 'splash' is at the end of the line) (I think to edit the line, you have to select the line and press e again, but I'm not sure here. There are instructions at the bottom of the screen). when you've edited, press b (not in the main menu, but in "menu" you got when you pressed e the first time". This disables the splash screen. 

Do you get any error messages?

dracayr

---

### Post by Nately on 2008-11-20
Dracayr,
Thanks for your reaction. If i remove the 'splash' as you suggested the system boots just great. The only error message i see is:
Loading hardware drivers
[37.790822] intel_rng: FWH not detected.

For as far as i can find this must not be a problem.
When i try the normal boot, without removing the 'splash' the system also boots normal. So only when i startup the system by just using the on/off button and without interupting to get in any menu i end up in the black screen.

Can you make something of this?

Nately.

---


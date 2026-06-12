---
title: "Trouble With Lenovo And Ubuntu"
date: 2011-10-09
forum: New to Ubuntu
---

### Post by Smooth Operator on 2011-10-09
hello there 
let me start by saying i have been a ubuntu user for years i recently had to buy a new laptop because old one died on me, since then i have been misrable why
because ubuntu is not working with my new laptop. i dual boot Windows 7 and ubuntu, now what happens when i boot ubuntu it completely disables my wifi card so then i boot back to windows and my wifi dosent work!!!!!! i flash my bios and the wifi is back ok perfect and i boot back to ubuntu and wifi disabled again!!!!
i dont knwo what to do any help
here are my laptop specs
 
Lenovo V570
Intel i5
6GB Ram
Intel Centrino Wifi
Intel HD graphics.....
 
i already tried alot of console commands
and nothen
 
help adivce any other linux os that will work with my laptop?..
THANKS IN ADVANCE

---

### Post by Smooth Operator on 2011-10-10
okay i guess i answerd my own question....
for those of you using A Lenovo V570 with a i5 sandy bridge
here is how i finally got it worken
 
i first installed Ubuntu 11.04 then i updated the kernel to 3.0
afterwards you may notice wifi is still disabled internally boot back to you windows OS
download you bios driver or bios update from lenovo flash your bios(becarefull  follow all instructions as it it very risky!!!!) after flash reboot system boot back to ubuntu open terminal and type
 
sudo rmmod -f **[COLOR=#ff0000]acer-wmi,[/COLOR]**
**[COLOR=#ff0000][/COLOR]** 
**[COLOR=#ff0000][/COLOR]** 
**[COLOR=#ff0000]and your wifi shoud work!!!!![/COLOR]**
**[COLOR=#ff0000]thats how i fixed my issue[/COLOR]**
**[COLOR=#ff0000][/COLOR]** 
**[COLOR=#ff0000]for detailed info feel free to message me[/COLOR]**
**[COLOR=#ff0000][/COLOR]** 
**[COLOR=#ff0000]PS[/COLOR]**
**[COLOR=#ff0000]ILOVEUBUNTU[/COLOR]**

---


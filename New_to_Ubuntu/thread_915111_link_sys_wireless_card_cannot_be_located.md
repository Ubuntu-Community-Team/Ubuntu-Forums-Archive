---
title: "link sys wireless card cannot be located"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by duquer on 2008-09-09
i am working on my friends computer and he just installed a link sys wireless b card in his cpu.the green light on the card is on but when i go to look for the local networks nothing was there to be found. i tried installing the indiswrapper but it kept saying it need a disc. maybe that because it still wasnt connected to the internet. but if that is the case after i install it what do i do next. do i need to also turn on the network controller. if so how? thanks for alls advice it is greatly appreciated.

-duquer

---

### Post by starcannon on 2008-09-09
First check if there is a hardware driver available in the gui:
System>Administration>Hardware Drivers

if the card is listed, put a check mark in its box(best to have a network cable attached in case it needs to download any files, or have the Ubuntu install CD in the drive).

For Ndiswrapper use this guide:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

It is asking for the disk because it needs the *.inf file for that card.

GL have fun

---

### Post by duquer on 2008-09-10
ok i got the ndiswrapper installed but when i try to use commands in the terminal to find the link sys card  or to turn the network controller on it basically keeps say this command is locked i download most of the software but i dont know. maybe its the age of the hardware inside of the tower but all the software will not install. it will fail. cause as of now i dont have any drivers to choose from.i have even tried using the command sudo and it still will not work. i dont know maybe i just need to tell them to buy a newer cpu

---


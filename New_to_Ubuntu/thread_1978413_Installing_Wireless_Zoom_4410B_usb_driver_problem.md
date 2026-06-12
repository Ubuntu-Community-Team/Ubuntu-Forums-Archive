---
title: "Installing Wireless Zoom 4410B usb driver problem"
date: 2012-05-11
forum: New to Ubuntu
---

### Post by pedrok1664 on 2012-05-11
Hi, Im a complete beginner so excuse if i'v missed something basic here. I have installed ndiswrapper fine. I then located the correct .inf from the ndiswrapper website which had the pciid 0803:4410, The thing is I only copied this file so when i ran the install i got a msg saying "couldn't find WlanUZG.SYS" make sure all driver files are copied or installation may be incomplete". I then copied all the files into my linux directory but when i try and run ndiswrapper -i WlanUZG.inf it just says "already installed". Iv ran ndiswrapper -l and it says invalid driver. I'v also tried to remove the driver using ndiswrapper -r WlanUZG.inf to try reinstall but it says  couldnt delete. No such file or dir, and i am defo in the right directory. Could anyone give me some help

many thanks

---

### Post by pedrok1664 on 2012-05-11
f**k me lol, Problem solved. The driver file WlanUZG.ing saved as wlanuzg, lowercase. Used the -r to remove and reinstalled with sys files present. BINGO.

---


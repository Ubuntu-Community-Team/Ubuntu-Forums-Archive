---
title: "Installing packages errors"
date: 2014-03-15
forum: New to Ubuntu
---

### Post by aleksandar6 on 2014-03-15
Hello,
Im new to all this so i dont know too much about Ubuntu. I installed 12.04 LTS version and i have problem where almost every package i install on the end i get error that instalation fails but applications seems to be installed. Does that have some connection with encrypting that i choose when i started installing Ubuntu?

Second thing: I have installed win7 (2primary part.) and one logical so i resized logical and made 2 more partitions for ubuntu 1 is 15gb as main and second 5gb swap at the end of that HDD. I manage to install Ubuntu but i cant format linux swap partition. Is it maybe that a reason for receiving error?

I have HP G6 Pavilion 4GB DDR2 ram 
500GB hitachi HDD    
processor  AMD E2-3000M APU with Radeon(tm) HD Graphics × 2

---

### Post by deadflowr on 2014-03-15
I don't understand.
What's what about what?

firstly, what are the errors for the updates.

secondly, how did you make the swap partition?

---

### Post by aleksandar6 on 2014-03-17
I somehow solved problem.
1. Ubuntu install from USB
2. I choose to encrypt home and swap
3. After several attempts i first made format swap partition and then ubuntu with ext4 fs
4. Everything was nearly ok but when i was booting system i get error /dev/mapper/cryptwap1 (you probably know)
5.Gparted didn t recognise swap at all from start. it was showing unknown with red sign .
6. Then i was searching internet how to install java7 and i found some pages where it is uses ppa:webupd8team .... and try that but i was getting error mismatching packages SHA:***
7. after that every single application that i tryed to install was installing with error on the end. First i was thinking that apps wasnt installed but i notice that shortcuts was there.
8 I installed Synaptic Package manager app for removing and adding packages and i uninstall anything that was java7 related and installed Icetea java app and that solved problem with java.
9 After that every package was installing ok.
10. I found on internet solution for cryptwap1 missing error. i did everything as it should but when i dont do command sudo ecryptfs-setup-swap Gparted recognise swap as normal linux-swap fs ..... And if i use that command i get startup error dev mapper cryptswap1 is not ready .... then i must everything from start.

So problem was installing Oracle-java7 from repository so if anyone has that kind of problem this is how i solved. Mismatching package.
For cryptwap1 booting error i guess that Gparted cant recognise it becouse it is encrypted or something else idk becouse this is first time i have installed Ubuntu.

---


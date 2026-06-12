---
title: "black screen"
date: 2015-05-25
forum: New to Ubuntu
---

### Post by jose77 on 2015-05-25
Bit of a noob user and I have just recently fresh installed Ubuntu 14.04, it installed perfectly but when I boot I get a purple screen followed by blank screen,  and after a minute or so I'm prompted with the login screen, after I login, it then goes blank again, is this a graphics problem and how do I go about fixing it, I'm using an old nvidia card but I'm not sure which card...

---

### Post by RobGoss on 2015-05-25
Hello and welcome, My first question would what are the specs for your machine - sometimes older machines don't handle the full version of Ubuntu 14.04

You might want to consider a lighter version of Ubuntu like Lubuntu or Xbuntu, they might do better if your machine is a older one.

---

### Post by Vladlenin5000 on 2015-05-25
Regardless of the previous information which, by the way, is probably correct considering the "old nvidia card", many nvidia cards/chips, old or new, aren't correctly supported by the open source driver. As such you need to edit Grub, find the line that boot Ubuntu and add the *nomodeset* parameter. This will give you generic video and will let you installs the recommended proprietary drivers for your nvidia.

---


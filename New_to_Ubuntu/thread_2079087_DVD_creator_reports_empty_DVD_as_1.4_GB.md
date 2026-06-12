---
title: "DVD creator reports empty DVD as 1.4 GB"
date: 2012-11-01
forum: New to Ubuntu
---

### Post by uppflog on 2012-11-01
Hi, gurus!

When I put a full-size (4.7 GB) DVD-R in the DVD  burner and open the program CD/DVD-creator [1] (Nautilus 2.30.1), it  reports the DVD as being only 1.4 GB.

I've tried two different brands of DVD-R - same result.
I  did a simulated burning of a 3GB ISO file which resulted in "unknown  error" and a huge log file that didn't make me wiser (I can post it on  request, but it's big.)

The (IDE) NEC ND-3520A DVD burner worked  well for burning in the Windows XP computer where I used it until  recently. Reading discs is no problem.

I've run the hardware  driver update program under the System menu, but it doesn't find  anything for the DVD burner. NEC homepage assumes one is using a Windows  computer. I can't find the CD that I suppose came with the DVD burner.


[LIST]
[*] Ubuntu 10.04 LTS, Swedish
[*] AMD computer from around 2000
[*] 256+128+64 MB RAM
[*] 60 GB HDD
[/LIST]
 
I've  tried searching forums and support database and also Google, but no  result. I post in this section because I'm unsure which section is  appropriate and then it was suggested to post here.
Any help and suggestions much appreciated.

[1] I don't know the English name, but the Swedish name translates to this. :-)

---

### Post by ibjsb4 on 2012-11-01
Try a different burner.  K3b is a good one.  In terminal:

sudo apt-get install k3b

---

### Post by uppflog on 2012-11-01
Thanks, great advice, and easy installation!

Regards,
Erik

---


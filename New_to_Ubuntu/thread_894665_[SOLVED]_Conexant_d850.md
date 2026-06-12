---
title: "[SOLVED] Conexant d850"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by ranch hand on 2008-08-19
I do not use Ubuntu but want to.  I have a new dell xps 420 and love it.  It has one BIG problem - Vista Home Premium.  

I am sure this is a fine OS for those who like it.  I don't.

I need windows for one program that I use.  I am going to get another HD and just switch from one to the other so that I will be using a clean machine.

I can not get an answer to the problem I am running into with an Ubuntu 8.04.1 LTS Desktop Live-install Disc  x84_64.

It does not recognize the modem.  I have a Suse 10.3-KDE Live  i386 disc also and it has the same problem.

I believe that the Conexant D850 is a windows only modem.  What I need to know is - What modem should I install?

It does not have to work with Vista.

If the software for my Olympus camera would work on Linux there would be no need for Windows at all.

All that is available here is dial up or satalite connection.

Satalite is too pricey under the current conditions of flux here at the ranch.
Thanx,
ranch hand

---

### Post by angryfirelord on 2008-08-19
Here's the wiki on how to set up your modem: [https://help.ubuntu.com/community/DialupModemHowto]("https://help.ubuntu.com/community/DialupModemHowto")

If you get confused, just reply back here.

---

### Post by ranch hand on 2008-08-19
angryfirelord,
The only problem with this is that right now I am just running off the CD.  It will be next month that I get a HD.

I would really like a recommendation for a Modem that will work with ubuntu in this configuration.

Working online on Vista makes me very nervous.  IE is a sieve and this machine is so slow on dial up compared to the old on that I can't even update the security software.
ranch hand

---

### Post by ranch hand on 2008-09-09
I have my new HDD!  One happy guy.

Loaded Hardy Heron and it works great except for the fact that the modem won't work.

I think I need to get a different modem and I think that I have found one that will work.  Now I just need the money for that.  It is a US Robotics USR5637.  I think I can do it for less than $75.

Until then I am going to try to get this conexant to work.

For me anyway, this is proving to be pretty tough.  The scan modem tool that is much recomended does not work on Vista.  This does not bother me too much as much of Vista does not work on Vista.

The conexant sites ID for chip sets is nice but does not mention the number on mine although I think it is safe to assume that I have an HSF modem.

On that basis I have been trying to get what I need to get the drivers to work.

Downloaded the driver, couldn't install - needed alsa-driver-linxant.  Got that couldn't install - need Libc6-dev_2.6.24-18.32_i386.deb.  Got that.  Fun over unreliable dial up modem.  Can't install that because there is some problem with libc-dev_2.6.24-18.32_i386.

This is, I think a conflict of some sort and I have not  figured this out yet.

I think that right now I should go and fix fence before all the cows are out instead of just 1/4 of them.

By the way, the modem on this machine has disconected 8 times while writing this.  MS is great.
ranch hand

---

### Post by ranch hand on 2008-12-06
This was fixed by installing a USR5610c internal.  Works great.

---


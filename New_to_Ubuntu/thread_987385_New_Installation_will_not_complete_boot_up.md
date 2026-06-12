---
title: "New Installation will not complete boot up"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by Habo123 on 2008-11-19
I am running Windows XP. I have tried to install Ubuntu, which it appears to have done. Now when I restart my machine I have the option of running Windows or Linux. However, the Ubuntu logo shows up as Linux boots up...then I am taken to a screen which shows all the things that have booted up. The last line says the SWAP FILE IS (BEING - I think) BEING SWAPPED.

Then everything stops.

I can run windows, but I would like to give Linux a fair trial. Can anyone help.

Thank You,
Habo

---

### Post by nhasian on 2008-11-19
during the installation of ubuntu, did you create a partition for swap?  if so, how big is it?

---

### Post by drs305 on 2008-11-19
You can check to make sure the swap file is listed properly in fstab with:
```

sudo blkid | grep swap
cat /etc/fstab | grep swap

```

Make sure the two /dev/sdXX or UUIDs match.

If this is not the problem, can you get to the root command prompt using the recovery mode?

---


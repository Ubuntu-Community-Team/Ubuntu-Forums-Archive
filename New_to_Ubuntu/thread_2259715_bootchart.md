---
title: "bootchart"
date: 2015-01-06
forum: New to Ubuntu
---

### Post by martin-bermann on 2015-01-06
hi I'm new to ubuntu and changed 14.04LTS from HDD to SSD (new installation). Now it seems my boot takes too long. I made a botchart and as far as I can judge the real boot starts only after 60sec but I'm completely new. could this be true? who can help me to solve that?
thx martin

---

### Post by sammiev on 2015-01-06
I'm sure that no one will be able to read that. :-k

---

### Post by grahammechanical on 2015-01-06
It should take seconds to load Ubuntu, especially if it is loading from an SSD. There is always a delay of about 10 seconds as the boot loader gives us on opportunity to boot into another OS or recovery mode. If Ubuntu is the only OS then we do not see the bootloader but it is still there and timing out.

Perhaps you can explain in more detail how you changed 14.04 from the HDD to the SSD. If it was a new installation on to the SSD and the HHD with Ubuntu 14.04 was still in the machine then you should see the Grub bootloader. It defaults to loading the new install of Ubuntu on the SSD. It will be at the top of the list. It should also give an option to load Ubuntu on the HDD or any other OS present. 

I am guessing that the motherboard might be first looking for an OS on the HHD and not finding one for some reason. It then looks elsewhere and eventually finds an OS on the SSD. All this takes time. Have you set the boot priority in the machine's boot system (BIOS/UEFI) to first look at the SSD?

Regards.

---

### Post by cariboo on 2015-01-06
Boot times are largely irrelevant, except for bragging rights, but bootchart shouldn't show any wait time while checking for other installed versions. I'd suggest you use an image hosting service, like [imgur.com]("http://imgur.com/") to post an image large enough for us to actually see what is going on.

As an aside, I'm running Vivid with systemd, this is what a typical boot looks like on my system running a fairly inexpensive ssd.

[[img]http://i.imgur.com/QyqA0lwl.png[/img]](http://imgur.com/QyqA0lw)

---

### Post by mooreted on 2015-01-06
I have Ubuntu on an SSD. It takes longer for my BIOS to POST than it does to boot Ubuntu which boots in about 10 seconds.

---

### Post by martin-bermann on 2015-01-07
thx for your comments. I installed the 14.04 directly on the SSD no move from HDD. I have 2 SSD (1-Ubuntu, 2-Windows) + 1HDD for data. When I start the computer I can select vie F10 if I take ubuntu or windows. the primary ssd is ubuntu whcih wil start automaticall when i do not select. but it takes time. see a biger picture form the beginning of the bootchart

---

### Post by sandyd on 2015-01-07
> **martin-bermann said:**
> thx for your comments. I installed the 14.04 directly on the SSD no move from HDD. I have 2 SSD (1-Ubuntu, 2-Windows) + 1HDD for data. When I start the computer I can select vie F10 if I take ubuntu or windows. the primary ssd is ubuntu whcih wil start automaticall when i do not select. but it takes time. see a biger picture form the beginning of the bootchart
Still a bit too small,
Ubuntu Forums has a habit of resizing large pictures - please upload to a picture hosting site (I reccomend [http://imgur.com](http://imgur.com)), and post the link here.

Thanks!

---


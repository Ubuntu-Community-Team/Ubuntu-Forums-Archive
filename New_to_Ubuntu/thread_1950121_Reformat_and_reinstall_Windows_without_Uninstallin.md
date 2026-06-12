---
title: "Reformat and reinstall Windows without Uninstalling Ubuntu OK?"
date: 2012-03-31
forum: New to Ubuntu
---

### Post by fatgreta on 2012-03-31
Hi,

If I reformat my hard drive and reinstall windows while it's set up as a dual boot with Ubuntu as the primary boot option, will that be OK? Or do I need to first uninstall Ubuntu somehow? If that's the case, how do I do that?

I thought I'd play around with and learn Ubuntu, but I just never did, and have lost interest. So I want to go back to just Windows XP (Home). I'm not certain what version of Ubuntu I have (I understand it's not supported any more), so I'm not sure if that matters for this question. If need be I can boot it and find out.

Thanks,

Chris

---

### Post by drklunk on 2012-03-31
well, if you wanna go back to Windows and not have Ubuntu on your machine anymore, just run the Windows disks and use it to do a complete format. thats all you need to do if thats the case, itll erase Ubuntu completely and give you a fresh windows install. 

if you rather dual boot and give Ubuntu a go, wait a few weeks for 12.04LTS to be out of beta, download it, and do a fresh install of 12.04 and use the setup guide to partition out your hard drive for a dual boot. from here just finish installation and then go through the Windows installation, just remember to select the proper partition ;)

---

### Post by coffeecat on 2012-03-31
You don't have to uninstall Ubuntu. If it's on its own partition, simply delete that with the Windows XP installer. If it's a wubi install it will be inside the Windows partition and will be lost when you reformat that.

Use your Windows XP install CD to remove all current partitions and then set up whatever partitions you need for the installation. It will be confused by the Linux partitions and refer to them as unknown partitions (or some such) but it will recognise them and delete them if you tell it to.

---

### Post by fatgreta on 2012-03-31
> **coffeecat said:**
> You don't have to uninstall Ubuntu. If it's on its own partition, simply delete that with the Windows XP installer. If it's a wubi install it will be inside the Windows partition and will be lost when you reformat that.

Use your Windows XP install CD to remove all current partitions and then set up whatever partitions you need for the installation. It will be confused by the Linux partitions and refer to them as unknown partitions (or some such) but it will recognise them and delete them if you tell it to.

OK, thanks to both of you. Maybe I'll come back to Linux some day.

---


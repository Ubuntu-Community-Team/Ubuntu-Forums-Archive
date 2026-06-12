---
title: "Can I repair Windows 7 after installing Ubuntu due to &quot;blue screen of death&quot;?"
date: 2014-05-29
forum: New to Ubuntu
---

### Post by jonny7 on 2014-05-29
A little while ago my installation of Windows 7 (pro/64-bit) went kaput. One moment it was fine, but the next time I switched it on it was blue-screen-of-death city. A friend was able to back-up the files from the hard disc, but we had no idea what had caused the Windows installation to go wrong. I then installed Ubuntu using a DVD. This installation works fine, and I can see all the files and folders on the Windows partition (called "263 GB Volume" in Files), and can even open the pictures, documents etc. Still no Windows, though.

What I'm wondering is this: is there a way of repairing the Windows installation while using Ubuntu? I'm loathe to wipe the entire system just to reinstall Windows, and I do have a lot of useful progams on there (Office, CS suite, etc). Any help would be gratefully appreciated - thanks!

---

### Post by Impavidus on 2014-05-29
It may not be easy to repair Windows using Ubuntu, although it depends on the kind of damage present. If you have a Windows repair disk or a Windows recovery partition you could try that. Chances are it will overwrite the Linux boot loader, which you'll have to recover. See here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Note that I know nothing about Windows, not having used it in years.

---

### Post by jakke1975 on 2014-05-29
Windows usually gives a BSOD when you have a problem between the driver and the hardware. If everything is working using Ubuntu, it's unlikely that you have an issue with your hardware, so, you have an issue with your driver.
There's not much information in your request to work with (did you install it as dual boot?). If you can still boot into your windows, try to boot in safe mode (using F8 when it boots up). Check the eventlog to see which driver caused the BSOD and reinstall that driver.

Now, before you do all that, you should be asking yourself what went wrong... it could very well be that your hard drive is starting to fail. This usually happens with a few bad sectors, which will cause a file (~driver) to go corrupt before anything serious happens. If your drive really is failing, you should be backing up your files and replace the hard drive.
There are many different tools to check your HD, but I'd start checking the smart parameters. You can install smartmontools in Ubuntu and check the HD. Then google around for disk monitoring tools and see what else is there before you do much trying to solve a problem that you may not even be able to solve.

---

### Post by LastDino on 2014-05-29
> **jakke1975 said:**
> Windows usually gives a BSOD when you have a problem between the driver and the hardware. If everything is working using Ubuntu, it's unlikely that you have an issue with your hardware, so, you have an issue with your driver.
There's not much information in your request to work with (did you install it as dual boot?). If you can still boot into your windows, try to boot in safe mode (using F8 when it boots up). Check the eventlog to see which driver caused the BSOD and reinstall that driver.

[B]Now, before you do all that, you should be asking yourself what went wrong... it could very well be that your hard drive is starting to fail. This usually happens with a few bad sectors, which will cause a file (~driver) to go corrupt before anything serious happens. If your drive really is failing, you should be backing up your files and replace the hard drive.
There are many different tools to check your HD, but I'd start checking the smart parameters. You can install smartmontools in Ubuntu and check the HD. Then google around for disk monitoring tools and see what else is there before you do much trying to solve a problem that you may not even be able to solve[/B].

This, I've had the same problem when my 250 GB old SATA was near its death. It took 6 long months to finally give out, but signals were pretty clear. Windows often needed to run disk repair at start-up. Not to mention the load noises.

---


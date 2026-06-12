---
title: "Ubuntu 9.04  upgrade how?"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by SansHobo on 2012-12-26
I am creating a Ubuntu PC for myself to teach me more about Linux in general and I am having some difficulty.  Let me explain what I have done first:

Hardware: an old Dell Vectra PC, 20 GB hard drive, 256 MiB's RAM, Pentium 4 1.7 Ghz CPU.  (Got it for free so I'm not complaining...).

I downloaded 12.10 (32-bit) and attempted an install; the install appears to hang after the initial screens.  I see a list of successes and two failures (one is a video GPU loop back test).  After this point the screen goes blank, leaving cursor in the upper left corner.  I have left it in this state and nothing happens.  I executed a shutdown with the power button and the install starts shutting down.

I happened to have a live Ubuntu CD (9.04) that I made a couple of years ago.  Using this CD, Ubuntu installed perfectly without any issues.  I attempted to update this version to 12.10 through the web without any success.  The system keeps looking for Ubuntu 9.10 and giving web 404 errors.  I googled for additional instructions but did not find anything specific for my situation.

I did re-download 12.10 (32-bit) again, paying attention so the DVD install is perfect.  However, the result is still the same as my original download mentioned above.  I even tried using the DVD as a source for updates without success.

Can anyone shed light on my issue here?  I cannot boot to a USB stick because the PC is too old.

I am not afraid to take a system apart and rebuild it;  I have done this many times with Windows as an OS.  With Ubuntu, I am in over my head but wish to learn as much as I can.

Thanks in advance for the help!
Sandor.

---

### Post by acimi66 on 2012-12-26
As far as I know you get from 9.04 to 12.10 as an upgrade. So it has to a completely new install.

---

### Post by sudodus on 2012-12-26
Ubuntu 9.04 has passed end of life, and I suggest that you get a new system. Unfortunately the current standard Ubuntu versions, 12.04 LTS and 12.10 need much more horsepower to run (and even install properly). There are four months to go of Ubuntu 10.04 LTS, so that is a candidate to test, but ...

1. The most light-weight version of Ubuntu with a graphical desktop environment is ***Lubuntu***. But not even that version will install properly from the standard live CD. However, you can install it from the ***alternate CD***. I suggest that you try Lubuntu 12.04.

You can also test some really light-weight distro of linux:

2. Skip the graphics and have only a text screen. This is typical for servers and for rescue systems, so it might be worth trying.

3. Try DSL (damn small linux), meant to run live with or without persistence.

4. Use one of the above and create a swap partition of 512 MB on the hard drive.

5. Try Knoppix, meant to run live with or without persistence.

6. Try Debian stable with LXDE, which needs less horsepower than Lubuntu.

---

### Post by bodhi.zazen on 2012-12-26
I would run puppy linux on that rig. Or slitaz or tinycore.

---

### Post by grahammechanical on 2012-12-26
> The minimum memory requirement for Ubuntu 12.10 is 768 MB of memory and 5 GB of disk space for Ubuntu Desktop. Note that some of your system's memory may be unavailable due to being used by the graphics card. If your computer has only the minimum amount of memory, the installation process will take longer than normal; however, it will complete successfully, and the system will perform adequately once installed.

[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop#System_Requirements]("https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop#System_Requirements")

12.04 needs less RAM - 512 MB

[https://help.ubuntu.com/12.04/installation-guide/i386/minimum-hardware-reqts.html]("https://help.ubuntu.com/12.04/installation-guide/i386/minimum-hardware-reqts.html")

This is why 9.04 installs but not 12.10.

Regards.

---

### Post by Michael Dooley on 2012-12-26
Please see this page:

[https://help.ubuntu.com/community/EOLUpgrades/Jaunty](https://help.ubuntu.com/community/EOLUpgrades/Jaunty)

You'll have to change your repositories in Synaptic for your Jaunty install to properly update.

---

### Post by arpanaut on 2012-12-26
> You'll have to change your repositories in Synaptic for your Jaunty install to properly update.

Yet with that little memory, as pointed out before, the performance would be horrible.
And would need multiple upgrades to get anything close to current.
Best to look at other alternatives more suited to OP's hardware.

---

### Post by BertN45 on 2012-12-26
The best solution is to buy more memory, say a 1GB stick.
Else the best option would be Lubuntu 12.04/12.10. You could try Xubuntu, but to be sure use the alternate CD to install. The standard desktop install needs all 265 MB and if your video card takes 32 or 64 MB, you could run into problems.

---

### Post by SansHobo on 2012-12-26
Thanks to all of you for the quick response.  I am investigating adding memory now.

---

### Post by CaptainMark on 2012-12-27
The best place to find old ddr memory is down the tip/recycling centre, look for old looking pc's and just open em up and take the memory, surprisingly ddr goes on ebay for a higher cost that ddr2 or ddr3 despite the fact it is much older tech

EDIT: I would also still recommend using lubuntu but I would choose 12.10, there seems to be little point in sticking to 12.04 on lubuntu as it isn't an LTS so is only suuported for another 10 months or so

---

### Post by superDave972 on 2012-12-27
> **SansHobo said:**
> Thanks to all of you for the quick response.  I am investigating adding memory now.

I considered adding 1 GB of RAM to an old machine (Dell Dimension 3000) that only had 256 MB of RAM originally. The 1 GB of RAM cost almost $100! I was appalled!! 

I decided to dump the old Dell, hit up Craigslist, and with that same $100 (+$50), buy a decent Lenovo Core2Duo laptop machine with 4 GB of RAM! The new machine runs Ubuntu 12.04 perfectly!

Moral of the story: Spend your $100 wisely and hit up Craigslist!

---

### Post by bodhi.zazen on 2012-12-27
> **superDave972 said:**
> I considered adding 1 GB of RAM to an old machine (Dell Dimension 3000) that only had 256 MB of RAM originally. The 1 GB of RAM cost almost $100! I was appalled!! 

I decided to dump the old Dell, hit up Craigslist, and with that same $100 (+$50), buy a decent Lenovo Core2Duo laptop machine with 4 GB of RAM! The new machine runs Ubuntu 12.04 perfectly!

Moral of the story: Spend your $100 wisely and hit up Craigslist!

+1

And check your hardware compatibility list before you buy.

---

### Post by superDave972 on 2012-12-27
> **bodhi.zazen said:**
> +1

And check your hardware compatibility list before you buy.

Agreed. If someone doesn't want to do a lot of checking, I recommend Lenovo because I believe Lenovo machines are very friendly with Ubuntu. I didn't have to change anything after installation.

However, I did have to do some googling to find a terminal command that would increase the sensitivity of the trackpoint on my Lenovo. (I hate slow mouse cursors!)

---

### Post by sudodus on 2012-12-27
I agree, it is a bad idea to buy new RAM to such an old computer, but if you can get used memory from someone or somewhere, thats a good idea.

But it can also be a good idea to play with such an old computer, and in this case I'll refer back to my previous post (post #3). Play with DSL! There is a new release candidate at the web site

[[COLOR="Red"]http://www.damnsmalllinux.org/download.html[/COLOR]]("http://www.damnsmalllinux.org/download.html")

You might also play with Kolibri OS

[[COLOR="red"]http://kolibrios.org/en/[/COLOR]]("http://kolibrios.org/en/")

Finally, if you add swap, it will be possible to install and run Lubuntu, but the computer will be more responsive with a very small OS.

---


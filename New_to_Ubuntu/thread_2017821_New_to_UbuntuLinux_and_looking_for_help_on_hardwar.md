---
title: "New to Ubuntu/Linux and looking for help on hardware"
date: 2012-07-05
forum: New to Ubuntu
---

### Post by JLWow893 on 2012-07-05
Hi All,

I need advise on hardware for Ubuntu 12.04LTS.

I'm looking at current generation Dual Xeon E5-2620 workstation which had Intel C602 chipset with Intel i350 gigabit NIC.  The motherboard in this case is the Supermicro X9DRW-iF.

X9DRW-iF came with Renesas SH7757 BMC G200 video which I find very little information around the web.

I planned to install 12.04LTS on 3Ware 9750-4i RAID controller configured in RAID 5.

My questions is that will Ubuntu work out of box with above minimum components?  Or will I encounter major installing issues such as driver recompiling?

Sincerely yours,


T. Lu

---

### Post by anewguy on 2012-07-06
It's hard to say - we would need to know the chipset on the video adapter.  You could boot using the livecd and select the "try ubuntu" option, then open a terminal window and type "lspci" (without the quotes) and post back the resulting output.

Did you try a google/bing/yahoo/whatever search with:

ubuntu Renesas SH7757 BMC G200

in the search string and see what turns up.

---

### Post by JLWow893 on 2012-07-06
Hi [anewguy]("http://ubuntuforums.org/member.php?u=331304"),

Thank you for your reply.  I had yet to get the hardware together to run Ubuntu live.  So I'm unable to run "lspci" to get info on the Renesas SH7757 BMC G200.  The hardware components is too costly.  I did a search as you suggested and there's almost zero info on it.  I even went to Renesas and find no product info on SH7757 G200.  This is definitely odd.

It's possible that I can live with just VESA display mode.  But will rest of the spec I mention causing any issues out of box or Ubuntu 12.04 installation?


Sincerely yours,


T. Lu

---

### Post by sandyd on 2012-07-06
> **JLWow893 said:**
> Hi [anewguy]("http://ubuntuforums.org/member.php?u=331304"),

Thank you for your reply.  I had yet to get the hardware together to run Ubuntu live.  So I'm unable to run "lspci" to get info on the Renesas SH7757 BMC G200.  The hardware components is too costly.  I did a search as you suggested and there's almost zero info on it.  I even went to Renesas and find no product info on SH7757 G200.  This is definitely odd.

It's possible that I can live with just VESA display mode.  But will rest of the spec I mention causing any issues out of box or Ubuntu 12.04 installation?


Sincerely yours,


T. Lu
It is the Matrox G200 graphics card.
[http://www.metafore.ca/Product/Default.aspx?SupplierPartNo=NC4004&CatalogID=100](http://www.metafore.ca/Product/Default.aspx?SupplierPartNo=NC4004&CatalogID=100)

---

### Post by anewguy on 2012-07-08
Checking around on the net, it appears that at least in some point in the past you had to install an ubuntu firmware all package so that you could get the firmware for the Matrox G200 (Thanks sandyd!).  It's also possible you may need to enter a boot option such as nomodeset, noapic, perhaps even vga=xxx.

I would see this [link]("https://help.ubuntu.com/community/BootOptions") for more information on the boot options.

As far as the rest of the system is concerned - it's hard to tell. How much memory are you going to put into this machine?  What will the speed of the processors be?

Also, sometimes raid can be a little testing to install.  you may want to read some of the ubuntu raid how-tos before you start.

---

### Post by JLWow893 on 2012-07-16
Hi anewguy and sandyd,  Thank you for your updates.  It's great to finally narrowed down that Renesas SH7757 BMC G200 is actually a Matrox.  This will help a lot.  From my own search, Matrox G200 seemed to be widely supported by all Linux distro.  anewguy, I'll definitely check out the link on the boot options.  All this look kind of daunting.  But we all must go through it to learn.  The system will cost me around $5000 in parts and the CPUs are a pair of Intel Xeon E5-2620 2.00GHz.  Sincerely yours,   T.Lu

---

### Post by NikTh on 2012-07-16
Hi , 
the best way to check if Ubuntu works well with your hardware is to test it via LiveUsb. Download the image (.iso) and burn it to Usb (use a tool like unetbootin) , boot from Usb and check if your hardware supports Ubuntu (or vice versa) , i don't really know what is more appropriate for someone to say. 
Thanks

---

### Post by JLWow893 on 2012-08-07
Hi All,

Thank you for all your advices.  I had managed to installed Ubuntu 12.04 server successfully.  It look like the Supermicro X9DRW-iF MB will work under 12.04 if you leave everything as default.

Although I did face some weird hanging issue during booting or restarting ubuntu.  But it's intermitten and once I was able to log-in, it seemed to be working alright.

I'm doing some burn-in test now and see if new problem will comes up.

Sincerely yours,


T. Lu

---

### Post by Integyant on 2012-08-13
I've seen the rebooting issue on 3 separate X9DRW-iF boards at work. The kernel will hang on a black screen when using the "sudo restart now" command. The board will then proceed to hang on subsequent start-up attempts after GRUB is passed. 

The system will shutdown fine if "sudo shutdown now" is used. But I still see it go to a black screen intermittently after restarting. 

I found that the only way to get back to the log-in screen 100% of the time is to cut power to the board completely for a few seconds. Once the system is plugged back in it will boot into Ubuntu without issues.

As to what's causing it, I have no clue. But this is a confirmed issue! :)

---


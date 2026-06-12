---
title: "problem with installing ati driver !"
date: 2012-09-17
forum: New to Ubuntu
---

### Post by snifer7 on 2012-09-17
hi
i am new to ubuntu 
few days ago i downloaded ati driver 12.2 from "amd website" , and installed it . but after reboot this message shows up : "ubuntu runs in low-graphic mode ... "

so i fix it with great effort (via recovery mode)  , after that i used "Additionals Drivers" in "system setting" to install ati driver !  but it didnt work again !
i have no idea what to do now! 

**my graphic is:   ati radeon mobility 4550**

please help :)

---

### Post by snifer7 on 2012-09-18
No body !!!!????????

---

### Post by NikTh on 2012-09-18
Hi , 

please follow this guide : [http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers)

Thanks

---

### Post by snifer7 on 2012-09-19
> **NikTh said:**
> 
please follow this guide : [http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers)


i followed that , but it didnt work !! after reboot this message shows up again : **"ubuntu is running in low-graphic mode , your screen and graphic card and ... "**
and i think this is the fourh time that i installed "ati catalyst" and i see this message !!   :|

because my graphic is swithcable and it is "ati radeon **mobility** 4000" ! i search alot , the solutions is just for "ati radeon 4000" not the "ati** mobility** radeon 4000" !!! what shoud i do !?

---

### Post by QIII on 2012-09-19
"Switchable" as in ATI/ATI dual graphics or Intel/ATI hybrid?

---

### Post by vandorjw on 2012-09-19
Just to be sure about your hardware please post the results to the following:
```

lspci | grep VGA

```

Since proprietary graphics drivers enjoy creating config files, may I also recommend you remove any configurations you may have accidentally made, by doing the following.

```

# mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bkup

```
In case you are unfamiliar with notation, '#' means this needs to by run as root. On Ubuntu this can usually be done by inserting "sudo" infront of the command, and providing your password.

Restart the computer after this.

I am getting something to eat. I'll check up in 30 minutes.
Also please post the link to the driver you downloaded so I can look what it may have done. (check if anything needs to be reversed...or maybe lend you a hand)

Cheers

---

### Post by QIII on 2012-09-19
Before you go further, let me say two things:

1.  If you have ATI/ATI dual graphics (such as an APU with a an additional "dedicated" ATI GPU), I see at least three errors/omissions in the Ask Ubuntu answer.

2.  If you have Intel/ATI hybrid graphics, you need to take a different approach, and that may not work in your case anyway.

---

### Post by snifer7 on 2012-09-19
> **QIII said:**
> "Switchable" as in ATI/ATI dual graphics or Intel/ATI hybrid?

intel/ATI
--------------------------------------------------------------------------------------------------------------------------------------
> **QIII said:**
> Before you go further, let me say two things:
2. If you have Intel/ATI hybrid graphics, you need to take a different approach, and that may not work in your case anyway.

actually , i dont need  swith !! i just want my ati graphic back :D
for more info , in my windows os , there is a "512 mb deticated memory" when i switch graphic to   "high performance"  ;)
so i only want to use that ati graphic (512 mb)

thanks again :)

---

### Post by snifer7 on 2012-09-19
> **cc7gir said:**
> Just to be sure about your hardware please post the results to the following:
```

lspci | grep VGA

```Also please post the link to the driver you downloaded so I can look what it may have done. (check if anything needs to be reversed...or maybe lend you a hand)

Cheers
The result was positive :D
[I]00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV710 [Mobility Radeon HD 4300/4500 Series][/I]
--------------------------------------------------------------
i downloaded the catalyst 12.6 from amd website :
```
http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx
```

---

### Post by QIII on 2012-09-19
You have an Intel/ATI hybrid, which creates problems that have been hit and miss as far as solutions go.  This is a problem across the Linux ecosystem.

I added a bit to the ATI wiki in my signature that has worked for some.  Look for the special case installation of Catalyst 12.6 with Intel hybrids in the wiki.  Be aware, however, that all of the possible solutions I have seen appear to work ONLY with ATI 6xxx and 7xxx series GPUs.

Can you disable one or the other of the graphics in your BIOS?

DO NOT use the legacy driver or you will likely end up with a completely unusable system.  Yours is not a legacy GPU and that driver WILL NOT WORK with X post 2008.

If you do decide you want to be able to switch, the open source Radeon driver with vgaswitcheroo might work.  But you wouldn't have the proprietary driver.

---

### Post by snifer7 on 2012-09-19
> **QIII said:**
> 
 Look for the special case installation of Catalyst 12.6 with Intel hybrids in the wiki
Can you disable one or the other of the graphics in your BIOS?

DO NOT use the legacy driver or you will likely end up with a completely unusable system.  Yours is not a legacy GPU and that driver WILL NOT WORK with X post 2008.


no, BIOS has not such possibility !
i searched for "hybrid and special case installation catalyst" , and i found [THIS LINK]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") !
in this guide , it says download "catalyst driver" from "AMD website" !so i have to download legacy catalyst again and ... and what !?

so should i give up !!!? no solution !? :( its ridiculous

---

### Post by QIII on 2012-09-19
No.  Do NOT use the legacy driver.  It will not work.  It does not work with X any longer.

The guide says to download 12.6.  However, as I said, that solution is not likely to work with your series of GPU.  I made a note specifically indicating it is not likely to work with series 5xxx GPUs and earlier.

All solutions I am aware of work only with series 6xxx or later GPUs, and even then they are not guaranteed.

If you can't disable the Intel graphics, your only likely solution is to use the open source Radeon driver with vgaswitcheroo.

This is the same story across Linux.  The OEM drivers for Linux do not work well with Intel hybrid graphics.  NVIDIA users are running into similar issues with Intel/NVIDIA hybrids.  The "solution" would be for the OEMs to modify their Linux drivers.  ATI's only works for more recent series GPUs.  There isn't much we can do about it.

---

### Post by snifer7 on 2012-09-20
> **QIII said:**
> 
The guide says to download 12.6.  However, as I said, that solution is not likely to work with your series of GPU.  I made a note specifically indicating it is not likely to work with series 5xxx GPUs and earlier.

All solutions I am aware of work only with series 6xxx or later GPUs, and even then they are not guaranteed.


:) thanks,  thats why i installed ubuntu last week,   for the linux community:)

and can u explain me what is OEM !?
thankyou

---

### Post by QIII on 2012-09-20
Original Equipment Manufacturer.

AMD makes ATI GPUs.  The "ATI" brand is carried over from when AMD bought ATI.

The OEMs are the ones who write drivers for their hardware.  Open source developers sometimes have a fair amount of success writing drivers that will work, albeit often with limited functionality because the hardware is proprietary and they can't peer deeply enough in to it to make their drivers perfect.

---

### Post by snifer7 on 2012-09-20
> **QIII said:**
> Original Equipment Manufacturer.

AMD makes ATI GPUs.  The "ATI" brand is carried over from when AMD bought ATI.


i searched for 5 days , and google gives me nothin :D
so i have to use "vgaswitcheroo" , is this my **only **solution?

---

### Post by QIII on 2012-09-20
Uninstall the proprietary ATI driver and get rid of xorg.conf.  Use the open source Radeon driver, which you will default to on restart (you don't have to install it.)

Because I can't predict which GPU your machine will default to on start up, install vgaswitcheroo (I'm on my cell phone on my way to work, so I can't give you a link.)

Then you can choose between the two GPUs.

---

### Post by snifer7 on 2012-09-20
ok , i'll do that

 and the last question :
take a look at [this page]("http://ubuntuforums.org/showthread.php?t=1930450") , in fourth paragraph it says the solution has been tested on intel HD 3000 ...
i guess it might works for me !

---

### Post by QIII on 2012-09-20
Unfortunately not.  That solution only works with series 6xxx and higher cards as well - when it works, which is not guaranteed.

---


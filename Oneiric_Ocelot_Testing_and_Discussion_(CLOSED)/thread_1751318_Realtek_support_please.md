---
title: "Realtek support please"
date: 2011-05-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by yungballla6 on 2011-05-06
I know in the past releases of ubuntu there hasnt been really alot of support for realtek wireless cards, just hopin oneiric ocelot will let users with realtek cards to enjoy the full experience of ubuntu without worrying if they can use wifi.

---

### Post by kaldor on 2011-05-06
Not up to Ubuntu to bring hardware support; that's Linux's job.

---

### Post by mr_luksom on 2011-05-06
Do you have a specific wnic in mind? I got my 8192c working by downloading the driver from realtek and loading it into the kernel manually.

---

### Post by yungballla6 on 2011-05-20
> **mr_luksom said:**
> Do you have a specific wnic in mind? I got my 8192c working by downloading the driver from realtek and loading it into the kernel manually.
 
Could you tell me how to do this. because im at a loss of words of searched everywhere.

---

### Post by ronacc on 2011-05-20
during natty something happened to wireless support for realtek . My card (rtl 8185 ) which had been rock solid since I installed it during gutsy suddenly became unreliable with random disconnects. I bugged it months ago .

---

### Post by cariboo on 2011-05-20
@ronacc, have you tried any other distros, to see if it is an Ubuntu only problem?

---

### Post by ronacc on 2011-05-20
> **cariboo907 said:**
> @ronacc, have you tried any other distros, to see if it is an Ubuntu only problem?

As I posted in the natty forum , sabayon ,suse , puppy and ubuntu prior to the natty kernel do not exhibit this behavior . I have since found that Debian squeeze can be made to exhibit the behavior if the package firmware-realtek is installed.This package is for cards later than mine (rtl 8185) the driver for mine and earlier has been built into the kernel for a long time . This package does not exist in the Ubuntu repos , so I suspect that begining with the .38 kernel Ubuntu built the contents of the package into the kernel causing a conflict for earlier cards .

---

### Post by mr_luksom on 2011-05-21
First, you need the device you want to get working. Try:

```

lshw -c network

```

This will give you the device #, like 8192c.

Then go to realtek.com.tw, and download the driver. It will come with a presentation that will give instructions on compiling the driver.

---

### Post by imnotrich on 2011-06-08
No, there is no useful driver on the realtek site for the 8185. 

The linux driver you can download there is two years+ old and was designed for Ubuntu 7. Already tested with 11.04, don't bother. Driver installs sometimes with errors, sometimes not and the proprietary hardware (jockey) thing can see the driver but it refuses to scan. 18" from my router and it says there are no wireless ap's available.

The Vista driver download direct from realtek is a "rar" file. Ubuntu doesn't support rar files even with the rar related packages - they won't extract. So I had to go back to windows and winrar but I returned to Ubu with the inf file and ndiswrapper told me it was invalid. 

The Realtek 8185 is not a new card, Puppy's had support for this card like 3 years now (but I note bug reports and forum posts on the Ubuntu side going back to 2005) so I can't understand why Ubuntu doesn't support it already, even with the 2.6.38.10 kernel.

Debian Squeeze's foss driver sometimes supports the 8185 sometimes not. But when it does connect it runs at dial up speeds, 33k-mostly. Again, don't bother. Mint 11, Mint 10, Mint Debian, Fedora 14, Open Suse 11 something, PClinuxOS - nobody seems to support this card out of the box except Puppy. 

I've tried Wicd and the other wifi config utilities included in Ubuntu repos, no joy. They won't scan or connect, and when I use Ubuntu's native network manager and tell it to connect - it keeps asking me for the key every 30 seconds even though the key is properly typed in (no typos). Already reported, I know - but a very annoying bug.

---

### Post by ronacc on 2011-06-08
I think that is just a quirk of the natty kernel , with 2.6.39
in oneric my realtek 8185 is working again . in debian squeeze (2.6.32 kernel) it shows available and displays the signal strength but wont connect unless I use wicd , debian sid with 2.6.39 is ok with the 8185 .

---


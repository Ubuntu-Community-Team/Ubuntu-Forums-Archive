---
title: "Instaling Ubunto on an Acer Aspire 9300"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by khaderzeidan on 2008-07-27
Hi,

I am really interested in kissing Microsoft Windows Goodby. so I got Ubuntu 8. 

I burnt the CD and tied to install it.
when I boot the CD the followig happens:
1- cant install because nothing happens after I click install and it starts listing what its doing.
2- failed to allocate memory resources error message appears and then start listing lots of lines being ok
3- managed to get to the desktop 3 times. the first 2 times i click install and it only does 15% and teh final time manged to install Ubunto but when i reboot my laptop it presents me with the failed to alocate mem resources and tehn a blank screen. 

Any help? I would really appreciate all teh help I can get as I am really really interested in Ububto.

---

### Post by rockerphil on 2008-07-27
i'd suggest using the Alternate install image, either that or you might try Xubuntu, it's been known to run on machines with limited system resources

---

### Post by coffeecat on 2008-07-27
> **rockerphil said:**
> i'd suggest using the Alternate install image, either that or you might try Xubuntu, it's been known to run on machines with limited system resources

I don't think the Acer Aspire 9300 is particularly limited or particularly old. A quick search of this forum shows several people using one, so they must have been able to install Ubuntu on it. The main problems seem to be getting the Atheros wireless and the webcam working. 

**khaderzeidan**, first, did you check the md5sum of the downloaded .iso and did you burn the CD at a low speed? A lot of these problems stem from a faulty download or faulty burn. Post back if you need help with this.

Also, can you post specifications of the machine - processor, memory, graphics card, anything you might think relevant. Lastly, it might be worthwhile doing a memory check on that machine. Windows uses memory differently from Linux and sometimes Linux can reveal a RAM fault that is not apparent in Windows. There is a memtest option on the live CD. You need to run it for several hours.

---

### Post by khaderzeidan on 2008-07-28
> **coffeecat said:**
> I don't think the Acer Aspire 9300 is particularly limited or particularly old. A quick search of this forum shows several people using one, so they must have been able to install Ubuntu on it. The main problems seem to be getting the Atheros wireless and the webcam working. 

**khaderzeidan**, first, did you check the md5sum of the downloaded .iso and did you burn the CD at a low speed? A lot of these problems stem from a faulty download or faulty burn. Post back if you need help with this.

Also, can you post specifications of the machine - processor, memory, graphics card, anything you might think relevant. Lastly, it might be worthwhile doing a memory check on that machine. Windows uses memory differently from Linux and sometimes Linux can reveal a RAM fault that is e-not apparent in Windows. There is a memtest option on the live CD. You need to run it for several hours.

Hi,

thank you for your propmpt reply.

1- My Acer Aspire 9300 is as follows:
a- AMD Turion 64x2 Mobile Tech TL-50 (1.6 GHz, 2 256 KB L2 Cash)
b- 17"WXGA+ CrystalBrite color TFT LCD
c- Up to 256 MB NVIDA GeForce Go 7300 w/TurboCashe Technology
d-120GB HDD
e-DVD-Super Multi Double Layer / DVD +_RW
f-1 GB DDR2 (Support dual-channel)
g-802.11 b/g wirless LAN
h-Bluetooth 2.0+EDR

As for Burning the CD, I burnt it 3 times and used a working version of UBUNTO 7 from a freind that he installed it on his Laptop and working perfect. I used the Server edition as well of 8 and teh work station with 8. 

Software I used for Burning called ISO burner from downloads.com
Used Spped 1 as max speed of buring

Booted several times managed to install bit it wont boot.
Booted several times and teh screen freezez after the list of what it is doing is finished
Booted using 800x600 resolution of monior and tht seems to have more luck going towards the loading of the environment. 

Tried to install and boot from it more than 60 times. successed to partually install 2 times and fully install1 time. never managed to boot after installtion.

i have no idea what is the md5sum thing is!!!
testing the memory?? how?

Please help

---

### Post by coffeecat on 2008-07-28
[Everything you need to know about md5sum]("https://help.ubuntu.com/community/HowToMD5SUM?"). :wink:

If your friend managed to successfuly burn a CD from the file, then it is unlikely to be corrupted, but it's still worth checking anyway, beacuse if the .iso file fails the md5sum test, you should not use it.

As far as I remember, the memory test is 'memtest' - the last option on the menu when you start the live CD. If I've got this wrong, I'm sure someone will soon correct me.

Two more suggestions:

The optical drive may need cleaning or is faulty. And if you are using a version 7 of Ubuntu, you may have better luck if you download the latest 8.04.1 and use that instead. Your machine is fairly up-to-date and Ubuntu 7 might just be choking on some aspect of the hardware.

---

### Post by khaderzeidan on 2008-07-28
I version that I managed to install is version 8 not 7. version 7 just didnt work at all.

the Optical drive have been cleand but will clean it again and will clean teh CD. 

what else to say :(

thanx for the link I will read about it.

when it says faild to alocate mem resources it is about teh memory correct?

if i try to install XBunto do you think that will help? is it less of a good thing than Ubunto?

Should I ask an expert around me to helpinstalling Ubunto?

---

### Post by Assembly on 2009-02-01
I have this same laptop Acer Aspire 9300 and everything working fine! Just not working fully card reader (not support XD card - only SD and MicroSD). I used ubuntu from 7.04 version 64bit (on this version too much freezing computer) now on 32bit version work for me excellent!.

---


---
title: "New installation, Total newby user"
date: 2013-03-31
forum: New to Ubuntu
---

### Post by cyclonecat5 on 2013-03-31
Hi all
I have been using Ubuntu from the disc for a few days and plan to install as I am really pleased with its perfomance. I am still figuring out what the best way to do that is. I have a emachines with T3300 processor running W7 and I am not sure about how or what size partitioning. Its quite a job trudging through the forums trying to locate a similar thread for information and as time is not my friend, any tips on a related forum or any direct tips would be highly appreciated.

The reason I came across Ubuntu is because I was given an acer3000 32x  for my daughter but it was full of viruses so I had a copy of xp and tried to do a complete reinstall. Unfortunatly the disc was scratched and the install stuffed up after completely wiping and reformatting so now nothing works. I can open in safe mode but access no files. That is why I came across Ubunto, looking for a solution. So my problem is, I cant install Ubuntu on the acer and wonder what else I can do or if there are any tricks. The disc I used to install Ubuntu is fine as it runs on my emachines despite it being a 32x. I realise I could get an unscratched copy of xp but if I am going to buy  that I would be better just grabbing a better machine second hand.

Any tips are really appreciated

---

### Post by Stonecold1995 on 2013-03-31
Are you asking how to install?  What the correct partition sizes to use?

If you are using the 32-bit live CD, you can reboot and boot into the CD again, and it should give you an option to install.  If you have no other Windows partitions you need to keep, you can just use the whole drive.  Next time you boot up it'll be into Ubuntu.

---

### Post by cyclonecat5 on 2013-03-31
Well my main problem is installing Ubuntu onto the acer that had a xp reinstall disaster and only opens in safe mode now and cant access any files. I have tried to install Ubuntu from safe mode but am not allowed to access the drive. I can boot from cd with Ubuntu disc inserted but it doesnt boot up, I get a black screen.

---

### Post by d0006 on 2013-04-01
You need to force  the Acer to boot from the CD.  One way to do this is enter the BIOS when the machine boots. A search indicated pressing **F2** or **Del** should do this on Acers. So:
Make sure the Ubuntu install CD is in the drive.
Reboot the system while tapping the **F2** (or **Del**) key. Hope the system opens the BIOS setup.
In the BIOS look around and find where you can specify the boot order.  You want your system to boot from the CD first. Save and exit the BIOS.
Reboot. Hope the system boots into Ubuntu from the CD.
Install Ubuntu, etc.

---

### Post by kikcer2 on 2013-04-01
hello cyclonecat,

now im a newer user also. but i am wondering something, do you know what graphics are on the Acer?

im asking because i had issues with my nvidida graphics card and i thru my research i found  a good bit of people would get a black screen when they booted with ubuntu with the nvidia graphics card.

---

### Post by mechdave on 2013-04-01
You could possibly need to disable acpi on the laptop before you boot the cd. I don't exactly know how to do it with the newer installs. Maybe someone else could point you in the right direction with more experience in this than me. :)

---

### Post by cyclonecat5 on 2013-04-01
Hi

Thanks for the replies.

I have changed order in the bios and it boots from cd, first a stick man and an icon appear at the bottom, then the Ubuntu logo comes up and the 4 dots change from red to white for a  while, but then error message comes up, something to do with kernel drivers but it never stays up long enough to take notes of the message, then just the tinge of red screen  flickering to black continuously. 

I may have to persist untill I can get details of the error message although bits of it are actually past the edge of the screen. Anyways, the disc is ok, not missing any drivers because it works a treat in my other machine (typing in Ubuntu now).

Any more thoughts anybody?

Cheers

---

### Post by MoebusNet on 2013-04-01
If you are attempting to use Ubuntu 12.10 or newer, your older WinXP machine may no longer be supported. I recommend giving Lubuntu 12.04 a try. It is optimized for older 32-bit non-PAE machines with older video cards. I run it on my 2002 Dell Latitude D800 (1.4 Ghz Pentium-M with 32 Mb NVidia video card).

[https://help.ubuntu.com/community/Lubuntu/PreviousReleases](https://help.ubuntu.com/community/Lubuntu/PreviousReleases)

Or you may prefer Xubuntu 12.04:

[http://cdimage.ubuntu.com/xubuntu/releases/12.04.2/release/](http://cdimage.ubuntu.com/xubuntu/releases/12.04.2/release/)

---


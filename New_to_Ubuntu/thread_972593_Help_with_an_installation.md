---
title: "Help with an installation"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by boringlarry on 2008-11-05
Hi..Ive installed 6.something, got it going good enough to download the new 8 point something, and when i go to install it, i get as far as i choose the language, then when i choose to either try, or install, the screen goes black and i get 2 lines of messages....a string of numbers which changes everytime, and this follows: ACPI:EC: acpi_ec_wait timeout, status= 0, expect_event =1 and then another line which reads:ACPI:EC:read time out, command =128......
HUH???please help!!..thanks

---

### Post by nhasian on 2008-11-05
you may want to be a bit more descriptive in future posts.  I think you are saying you had installed one of the ubuntu packages from 2006?  and then you tried one from 2008?  like 8.04 or 8.10 ?  

If you have trouble installing Ubuntu from the LiveCD, try downloading and installing from the Alternate CD.

---

### Post by harsh1kumar on 2008-11-05
I think you are trying to upgrade your ubuntu from a very old version. It is always a bit of problem if you upgrade from a very old version. 6.* are very old versions dating back to 2006. What you should try is download the latest version of ubuntu from the site or from torrent.

---

### Post by lovinglinux on 2008-11-05
Are you trying to install on a notebook?

I have an HP V6000 series notebook which has a BIOS bug related to ACPI, which prevents the installation of newer versions. The installation stalled at the same point as yours several times, until I left the default language unchanged. You can add other languages after installation if needed.

You could also try to use advanced boot commands by pressing F6 when the first menu you mentioned appears (the one asking for try or install). Then add "noapic nolapic" (without quotes) before the "--" at the end of the line that appears. Click enter and see if the installation go further than the language selection.

> **harsh1kumar said:**
> I think you are trying to upgrade your ubuntu from a very old version.

He is trying to install the new version using the Live CD

---

### Post by boringlarry on 2008-11-06
hi , and thanks...here's the long story....
i have a sony vaio laptop that was "made for vista", and hating vista, i wanted to upgrade it to xp pro; well, after days of searching and trying different things, there just doesn't appear to be xp drivers made for some things in it....So, i had a copy of 6.something laying around, i wiped, and installed it, started playing with it, decided i liked it, and ordered the cd for 8.04...tried to install it, and thats when the messages i posted started...
so...i wiped the hard drive re-installed 6.something, it worked fine, although it did hang once during the install and had to start again, went to a friends with broadband wireless and downloaded 8.10, and....some o same o...
So...i tried this morning the command after f6 (default is english, so no change there), and same result....
what other info might you need to help with this...
[SIZE="2"][SIZE="2"][SIZE="1"][/SIZE][/SIZE][/SIZE]and THANKS!!!

---

### Post by lovinglinux on 2008-11-06
> **boringlarry said:**
> what other info might you need to help with this...
[SIZE="2"][SIZE="2"][SIZE="1"][/SIZE][/SIZE][/SIZE]and THANKS!!!

Look under your notebook and check if it is made by FOXCONN. I guess it is.

There are reports that FOXCONN modified the BIOS ACPI to get Vista certification and this modification makes it incompatible with recent Linux kernel. 

If this is the case, I strongly recommend contacting Sony support to get a BIOS update. In my case, I had to flash the BIOS with the new  firmware to make Intrepid installation possible.

---

### Post by Coreigh on 2008-11-06
See this thread about APIC errors. I have done several installations where I had to use special options to boot the LiveCD properly on older hardware.

[http://ubuntuforums.org/showthread.php?t=270280]("http://ubuntuforums.org/showthread.php?t=270280")

---

### Post by boringlarry on 2008-11-06
I looked, but can see no indiction it was made by foxxconn......

---

### Post by boringlarry on 2008-11-06
And how does one do these special installations?...i'm really a rookie at Linux.....

---

### Post by boringlarry on 2008-11-07
> **Coreigh said:**
> See this thread about APIC errors. I have done several installations where I had to use special options to boot the LiveCD properly on older hardware.

[http://ubuntuforums.org/showthread.php?t=270280]("http://ubuntuforums.org/showthread.php?t=270280")

...I read this thread that was recommended, but i dont understand how to edit anything during the boot-up process.......

---


---
title: "linux on laptop,win8"
date: 2019-04-08
forum: New to Ubuntu
---

### Post by eyeneedhelp on 2019-04-08
i have a linux tower computer ver 14.? which works so well i am spoiled,i quit learning, its so good. have about 8 years.

now i have a w8 laptop,not used because i hate win.
i want to install linux ubuntu on the laptop.
please advise a spoiled dummy.
also,what user name am i? !!i tried 2oldjeeps but see eyeneedhelp?
i must be in from yrs ago, forgot..

---

### Post by yancek on 2019-04-08
Is your windows 8 install a UEFI install?  Windows 8/10 are generally UEFI if pre-installed.  If that's the case, I would suggest you read the documentation at the Ubuntu site below which explains the process in detail.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by eyeneedhelp on 2019-04-08
> **yancek said:**
> Is your windows 8 install a UEFI install?  Windows 8/10 are generally UEFI if pre-installed.  If that's the case, I would suggest you read the documentation at the Ubuntu site below which explains the process in detail.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
thanks...and  YIKES  ..way over me. since i built that tower i became an appliance operator, got spoiled lazy and just used it...flawlessly. if it got a glitch, it fixed itself. i even forgot the version,12.3?
so i need to look into the toshiba w8 thing to see what i have,what to do. ill try to read more about uefi? so im not totally helpless. laptop is touchscreen,will that ever work on linux? im out of date.
tnx again.   be back later, tom

---

### Post by yancek on 2019-04-08
You should be able to determine the release you are using with this command from a terminal:

```
cat /etc/issue
```

If it is anything before 16.04, it is not supported and some releases after 16.04 are also not supported.  Supported releases can be seen at the Ubuntu site below.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I installed Ubuntu 18.04 for a friend with a touch screen and it works fine.

While you are booted into Ubuntu and in the terminal, you can determine whether you are using UEFI or Legacy by running the command below:

> [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"

---

### Post by RedDirtDog on 2019-04-08
Are you looking to trash Win8 and install Ubu on the laptop, or do you want to keep Win8 as an option in case you need it?

---

### Post by oldrocker99 on 2019-04-08
Since Win8 is no longer supported, either pay for the upgrade to Win10 or deep-six the malware magnet and give the whole laptop the ultimate upgrade by installing Linux on it.

---

### Post by eyeneedhelp on 2019-04-09
> **oldrocker99 said:**
> Since Win8 is no longer supported, either pay for the upgrade to Win10 or deep-six the malware magnet and give the whole laptop the ultimate upgrade by installing Linux on it.

i probably should do that since i havnt turned it on in years! and just dont like ms.
right now i get a virus message on it as well?

its been , as i said b 4 a long time since i did any real installation work.
im open to guidance on downloading linux  and "killing' w8.

btw im on a w7 laptop i use for email,etc. the linux 12.3 ? is in another room. 

right now i want to leave it alone since it is trouble free. maybe later upgrade it huh..
thanks for all comments. im listening for anyone with patience!!!

---

### Post by yancek on 2019-04-09
> im open to guidance on downloading linux  and "killing' w8.


That gives you a lot of options since there are over 500 different Linux distributions available.  The link below lists a number of them and has links to each distribution site with more detailed information.

[https://distrowatch.com/](https://distrowatch.com/)

If you want Ubuntu as you mentioned above, go to the Ubuntu site and find the "hardware requirements" and compare that to the hardware you have.  If you don't want windows 8, it should be a matter of simply downloading the Ubuntu iso, burning it to a DVD or putting it on a usb, booting it and selecting the option to Erase disk and install Ubuntu.

---

### Post by eyeneedhelp on 2019-04-09
> **yancek said:**
> You should be able to determine the release you are using with this command from a terminal:

```
cat /etc/issue
```

If it is anything before 16.04, it is not supported and some releases after 16.04 are also not supported.  Supported releases can be seen at the Ubuntu site below.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I installed Ubuntu 18.04 for a friend with a touch screen and it works fine.

While you are booted into Ubuntu and in the terminal, you can determine whether you are using UEFI or Legacy by running the command below:

if 18.04 will work on my w8 lap id like to load it into a usb thumb stick to boot and install on the laptop. i first saw the term 'uefi" here in this thread! i have zero knowledge of it.
can i "assume" i can do that
?. how?
i cant check it as mentioned since i dont have ubunto installed!

---

### Post by yancek on 2019-04-09
Installing Ubuntu UEFI is explained at the link I posted above, post #2.  If you plan to install Ubuntu over windows 8 and not have windows, there will be an option to ERase disk and install Ubuntu.
You can check your BIOS on the computer to see if there is any reference to UEFI.

---

### Post by eyeneedhelp on 2019-04-10
thanks again, i found a friend who is a linux guy. he wiil help me.

---

### Post by eyeneedhelp on 2019-04-20
back again,got lost. i got mint on my w8 laptop, killed w8.

having some trbl getting display so i can read it. colors are low contrast like a win 10 desk comp i have.but the lap is working.

i hope to do mint or? on the w 10 comp but keep win for now so advice is welcome and appreciated.

its an hp 6305 refurb that looks like new,w 10 runs ok now. big ram,big hd,lots of room.

---

### Post by oldos2er on 2019-04-20
Linux Mint forums are [here]("https://forums.linuxmint.com/"), or you may post in [https://ubuntuforums.org/forumdisplay.php?f=453](https://ubuntuforums.org/forumdisplay.php?f=453).

---


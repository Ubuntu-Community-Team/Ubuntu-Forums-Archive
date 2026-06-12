---
title: "cant install amd hd3000 catalyst driver software"
date: 2016-02-14
forum: New to Ubuntu
---

### Post by sunil16 on 2016-02-14
all its showing is window with no text when i followed the process from youtube and forums[ATTACH=CONFIG]267297[/ATTACH],,, im doing this because a game in flashplayer doesnt work like it used to work in windows,,, the graphics is messed up when playing on ubuntu,,, pls help thanks

---

### Post by Bashing-om on 2016-02-14
sunil16; Ouch !

Some issues to address for sure.

The 1st major thing is that release 14.10 is End_Of_Life and has no support . The software repository has been turned away.
Install or upgrade to a current release.

2) well what is the hardware exactly ?
Post back - between code tags - the outputs of terminal commands:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
be aware there are no proprietary drivers for the old ATI cards  with kernels greater than 3.2 series .

Better advise pending when we know more ->
[INDENT][INDENT]it is a thing
[/INDENT][/INDENT]

---

### Post by mastablasta on 2016-02-15
hd 3000 is no longer supported with proprietary drivers. the opensource drivers available on OS install should do fine.

---

### Post by Geoffrey_Arndt on 2016-02-15
So, how did you go about and do the driver install?  From what source, and what specific driver package?   Please provide adequate details, no 5 or 6 word blurbs if you get my drift.

---

### Post by mastablasta on 2016-02-16
in Ubuntu Linux OS most drivers are part of the Linux kernel and do not need special install as they are installed when OS is installed. proprietary drivers when installed actually "patch" the kernel. in this case the proprietary drive is no longer available as AMD dropped Linux support for this chip.

more info on radeon driver: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by sunil16 on 2016-02-18
if i buy new graphic card will i be able to install new drivers then?

---

### Post by sunil16 on 2016-02-18
> **mastablasta said:**
> in Ubuntu Linux OS most drivers are part of the Linux kernel and do not need special install as they are installed when OS is installed. proprietary drivers when installed actually "patch" the kernel. in this case the proprietary drive is no longer available as AMD dropped Linux support for this chip.

more info on radeon driver: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
if i buy new graphic card will i be able to install new drivers then?

---

### Post by richardsdma on 2016-02-18
of course you will. why dont you try ubuntu 14.04 for that actual card?

later edit:
take a look to this and read carefully: 
[http://support.amd.com/en-us/download/desktop/legacy?product=Legacy2&os=Linux+x86](http://support.amd.com/en-us/download/desktop/legacy?product=Legacy2&os=Linux+x86)

[SIZE=5][B]Description:
[/B][/SIZE][B][SIZE=5]Automated installer and Display Drivers for Xorg 6.9 to Xserver 1.12 and Kernel version up to 3.4

[SIZE=3]so, you must download ubuntu 14.04 first edition, from april 2014, install it and you can use proprietary driver. if i remember right, it has 3.2 kernel. also, it is supported for 5 years, until 2019. 
[/SIZE][/SIZE]http://old-releases.ubuntu.com/releases/14.04.0/

or maybe it is 12.04....i do not know.
[/B][http://old-releases.ubuntu.com/releases/12.04.0/](http://old-releases.ubuntu.com/releases/12.04.0/)

---

### Post by Geoffrey_Arndt on 2016-02-18
Another way to fix your PC . . . rather than spend more money on another graphics card (for an old pc) . . . . . why not just try a lighter version of Ubuntu?

    Suggest you download Xubuntu iso, burn it to dvd (at slow speed, 4x or 8x), and then do a full reinstall.    That may be the fastest and best way to get your PC running right.

[http://xubuntu.org/](http://xubuntu.org/)

---

### Post by richardsdma on 2016-02-18
if we are talking about ganes and flash player, you wont notice any diffrence by installing xubuntu. the only way is to install a version of ubuntu witch has kernel under 3.4 and still has support. i guess it is 12.04. i thik i was wrong when i said about 14.04, it rather has 3.13.

---

### Post by QIII on 2016-02-18
Take care with the point release of 12.04 (supported until April of 2017).  The proprietary AMD driver will work up to and including 12.04.1.  It will not work with 12.04.2 or beyond.

---

### Post by richardsdma on 2016-02-18
as i said, it must have kernel below 3.4. 
but still, since amd moved the hd3000 series to legacy, they had to release some ofthe specs of their radeon cards to comunity, so the linux developers would be capable to build a competitive driver for their cards. it is quite strange to me that oss driver is still far behind the proprietary driver, after almost 3 years.

---

### Post by sunil16 on 2016-02-27
how can i get older version of ubuntu?

---

### Post by X-RED_Tech on 2016-02-28
> **sunil16 said:**
> how can i get older version of ubuntu?

You shouldn't.

---

### Post by Bashing-om on 2016-02-28
sunil16; Hello'

Release 12.04.[color=red]1[/color] has support 'till April of next year.
You can get that release from:
[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---


---
title: "converting for windows to ubuntu"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by BlackKnight7891 on 2008-05-27
hello everyone,

i understand i am probably asking questions that every windows convert asks, but here we go,

my main concern is driver support, i primarily play games on my computer and watch video's off it. i would like any advice on how difficult it will be getting ubuntu 8.04 64bit installed on my hardware.

CPU:Q6600
MB: EVGA 750i ftw
ram: 4gb corsair xms2 pc6400
graphics: 2x inno3d 8800gt oc 512mb
Hdd: 1x 500gb seagate sata2(2 partitions ntfs); 1x seagate 80gb ide drive(1 partion ntfs),
pioneer dvd burner
logitech g-15 keyboard (i mention because it comes with windows drivers)

currently loaded windows vista ultimate 64bit on the 500gb drive.

---

### Post by DGortze380 on 2008-05-27
I hate to suggest windows to ANYONE, but if you're playing games, you're going to want to tough it out with windows.  you could dual boot. Download the iso for a live cd, burn it to a disk, and boot with the disk in the drive holding 'c'.  You can test everything out before you install

---

### Post by Samhain13 on 2008-05-27
Playing games will be your biggest concern then.

Have a look at the [Games & Leisure](http://ubuntuforums.org/forumdisplay.php?f=93) section of the forum to get an idea of what games work, might work and don't work at all. :)

Cheers!

---

### Post by BlackKnight7891 on 2008-05-27
if i do eventually go full ubuntu, i usually play COH OF, COD4 a little BF2 eve trinity (has linux intstaller), Could VPC be used to play games. i know it works perfectly well running multple machines at low load.

---

### Post by oedha on 2008-05-27
dual boot then.... :)
you can read on [http://psychocats.net/ubuntu](http://psychocats.net/ubuntu)

---

### Post by ZabiGG on 2008-05-27
And you'll find loads of very convenient information to decide to make the switch or dual installs in the Sticky, on top of the threads page intended for newbies. You might even want to read my Newbie 101... the link is Look here, in my signature below.

Good luck with your decision ;)

Personally, I kept Vista for games and I use Ubuntu as my main operating system.

Z.

---

### Post by BlackKnight7891 on 2008-05-27
well i've got the installer now for 804 so i'll live boot at home tonight and see how much my computer cries (and how much of vista has disappered from the hdd as punishment for thinking about rejecting it)

---

### Post by omi291 on 2008-05-27
I've heard about Cedega ([http://www.transgaming.com/](http://www.transgaming.com/)), which could be a way to play your games on ubuntu, but it costs money

---

### Post by seagullplayer77 on 2008-05-27
Linux in general isn't too terribly good for games. Dual booting probably isn't a bad option, though. I only boot into my Vista partition when I need to do PowerPoint shows (no offense to OpenOffice.org, but PowerPoint is still better than Impress), and that's about it. Other than that, I use Ubuntu all the time--Web browsing, writing papers, all that good stuff. It runs faster and cleaner than Windows, IMO.

As far as drivers, I'm not too sure. Lots of stuff is supported by default in Linux and you don't have to configure it at all, while some things are supported with restricted drivers and also don't require any configuring. There are things, though (just had a massive battle with my Atheros wireless card) that do require some work to get operating properly. 

Just my two cents' worth.

---

### Post by kool_kat_os on 2008-05-27
virtutalbox?

---

### Post by jrusso2 on 2008-05-27
Virtual box won't do direct x.  I think the new vmware does or parallels.

I have a similar pc to yours and I dual boot.  Thats the best for gaming.

---

### Post by BlackKnight7891 on 2008-05-27
alrighty well i've been searching nvidia for drivers (nforce supported natively by "most distributions") the only thing to do is load up the disk yay time to break stuff. i dont use wireless although i have a dlink card i could plug in, and nvidia have 64bit linux drivers which i am assuming will work.

given that i mainly play directx9c/10 games will ubuntu cry? or should support them (even if tweaking is involved)

EDIT:: thanks for the info ZabiGG reading through those links slowly

---

### Post by BlackKnight7891 on 2008-05-28
omi291 thanks for the advice i followed that which led me to winehq  mainly because i dont want to pay a subscription to play games i have already bought. which looks promising even implements DX9c heres a link to the winehq site if anyone is interested (just ignore me if i spitting out old news)

[http://www.winehq.org](http://www.winehq.org)

---

### Post by BlackKnight7891 on 2008-05-28
running Ubuntu now no applications install went off without a hitch. one thing i was wondering if someone could explain it,

after the install i downloaded and enabled the nvidia graphics drivers, then installed the 100mb worth of updates released. rebooted after all was complete.

when i loaded ubuntu again i could only get 640 by 480 resolution. after another reboot it fixed itself. back to 1280by 1024.

anyone know why?

---

### Post by SunnyRabbiera on 2008-05-28
> **BlackKnight7891 said:**
> running Ubuntu now no applications install went off without a hitch. one thing i was wondering if someone could explain it,

after the install i downloaded and enabled the nvidia graphics drivers, then installed the 100mb worth of updates released. rebooted after all was complete.

when i loaded ubuntu again i could only get 640 by 480 resolution. after another reboot it fixed itself. back to 1280by 1024.

anyone know why?

well you could try boosting your resolution by using the screens and graphics application, open up a terminal and type in gksu displayconfig-gtk
it should help

---

### Post by BlackKnight7891 on 2008-05-28
basically i had what ever default driver was running, clicked on the popup notice to install the nvidia driver after which i installed all the ubuntu updates and rebooted

got back into ubuntu.

i found the application but it gave me the choice between the 640/480 resolution and 320 something resolution. I rebooted the computer and on the next load the graphics driver seemed fine resolution defaulted to 1280/1024

not a biggy it fixed itself i was just wondering why it wouldn't load the driver properly on the first reboot(attempting to understand what Linux is actually doing as opposed to thats a nice button syndrome)

---

### Post by DGortze380 on 2008-05-28
I've had it do the same. I believe (and I may be totally wrong) that after the first reboot the driver is installed and working, but xorg gets reconfigured and doesn't take effect until you restart X (reboot or ctrl+alt+bksp).

---


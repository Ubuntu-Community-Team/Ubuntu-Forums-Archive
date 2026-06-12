---
title: "screen problem"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by minhal on 2008-11-02
hi,

i am a new user of ubuntu 8.04

i installed on my desktop pc and i have a problem with the monitor. 

i am gettin a split screen + wierd designs on the screen + i see double cursors and more.

i have tried to change the resolution and refresh rate but no luck. i have also changed about 6 lcd monitors but all have the same problem.

HELP !!!!

---

### Post by overdrank on 2008-11-02
> **minhal said:**
> hi,

i am a new user of ubuntu 8.04

i installed on my desktop pc and i have a problem with the monitor. 

i am gettin a split screen + wierd designs on the screen + i see double cursors and more.

i have tried to change the resolution and refresh rate but no luck. i have also changed about 6 lcd monitors but all have the same problem.

HELP !!!!

Hi and welcome, could you give us some specs on the system, graphics and so on.
Have you tried to boot into recovery mode which is usually the second choice from the grub and use the xfix option to correct the graphics issue.

---

### Post by The Crazy old Gunny on 2008-11-02
> **overdrank said:**
> Hi and welcome, could you give us some specs on the system, graphics and so on.
Have you tried to boot into recovery mode which is usually the second choice from the grub and use the xfix option to correct the graphics issue.

Hi, 
I'm experiencing the same problem on my system, with my attempt to install 8.10.
It's an HP n5495 notebook p3 1.4ghz, with the i830 graphics.

My install was a dual boot, with xp residing on the same hard drive.
This happens with the install screen being "split"  on mine.  I get through the 7 steps, it installs,  and then a frozen YELLOW SCREEN (of death?) upon reboot.  I've installed twice, same story both times. 

Any help would be appreciated.

I was looking into ubuntu cuz it can make old and tired PC's run better. 
Is there a version for humans?:lolflag:

---

### Post by overdrank on 2008-11-02
> **The Crazy old Gunny said:**
> Hi, 
I'm experiencing the same problem on my system, with my attempt to install 8.10.
It's an HP n5495 notebook p3 1.4ghz, with the i830 graphics.

My install was a dual boot, with xp residing on the same hard drive.
This happens with the install screen being "split"  on mine.  I get through the 7 steps, it installs,  and then a frozen YELLOW SCREEN (of death?) upon reboot.  I've installed twice, same story both times. 

Any help would be appreciated.

I was looking into ubuntu cuz it can make old and tired PC's run better. 
Is there a version for humans?:lolflag:

You may choose to try the version Hardy 8.04 as it works well with intel graphics and it is LTS ( long term support). I have not installed Intrepid on a intel graphics system as of yet so I am at a loss.

---

### Post by The Crazy old Gunny on 2008-11-02
Mister Overdrank,

Thank you, I will d/l 8.04 and give it a shot.

Have a great day.

---

### Post by minhal on 2008-11-03
> **overdrank said:**
> Hi and welcome, could you give us some specs on the system, graphics and so on.
Have you tried to boot into recovery mode which is usually the second choice from the grub and use the xfix option to correct the graphics issue.

hi,

thank you for your reply. i could not find my own post so got delayed in replying u.

the vga driver is VIA P4M900M.

Specs are dual core 1.8ghz/1gb ram/built in vga on the motherboard (so maybe around 32MB)

i tried the xfix option but it did not help.

hope u can come back with a solution..

thanks

---

### Post by overdrank on 2008-11-03
> **minhal said:**
> hi,

thank you for your reply. i could not find my own post so got delayed in replying u.

the vga driver is VIA P4M900M.

Specs are dual core 1.8ghz/1gb ram/built in vga on the motherboard (so maybe around 32MB)

i tried the xfix option but it did not help.

hope u can come back with a solution..

thanks

Hi and if you are using 8.04 you may try and use the alt, F2 keys and enter the command ```
gksu displayconfig-gtk
``` and adjust your resolution there along with the driver.

---

### Post by UbuntuKhan on 2008-11-03
I have a Toshiba A60 Pro Laptop with ATI graphics (X700 or 7000 I believe) P4 3 Ghz 1,256 GB RAM and no luck running the live CD. As it started the splash screen is divided (one time the moving orange bar was replicated 3 times over the screen, another time Ubuntu was divided horizontally in two). After approx. 1 minute it freezes. In Qemu I can boot but not directly to X. I have to choose the minimal graphics mode to see anything. For the liveCD I tried the vga=791 option at boot (which I thought shoud have worked as elive had no problems with 16-bit 1024x768) but with no effect. Can you sugest some options that I might try to get the liveCD working. Can the liveCD be remastered to include those options? How? (by the way I am talking about 8.10 liveCD)

---

### Post by UbuntuKhan on 2008-11-03
I booted with "acpi=off nolapic noapic" and finally I have X. Along the way I have seen a message telling me that I should try irqpoll option (it went fast so I don't know if something was wrong). I will try that option too (alone) to see if that is also a solution. I would very much like to know what is the probable cause that keeps me from booting normally. Does anyone know why do I get X with the above options at boot, but not without them? Thanks!

PS: Works with irqpoll option too. Hope it helps others to see the light ;). I'm still waiting for some enlightenment about those options. (By the way the splash screen is still weird with multiple moving bars during boot)

---

### Post by minhal on 2008-11-03
> **overdrank said:**
> Hi and if you are using 8.04 you may try and use the alt, F2 keys and enter the command ```
gksu displayconfig-gtk
``` and adjust your resolution there along with the driver.

hi again,

well thanks alot i managed to get my screen proper.. however i have a few quesions...

1) When i do the hardware test, at screen test i dont c the color bars ... this means my driver is wrong?

2) I tried use the VIA driver available but it wud switch back to vesa.. y?

3) My sound doesnt work :( ... will get you the default driver shortly..

but all in all thanks alot for the screen problem.

---

### Post by minhal on 2008-11-04
> **overdrank said:**
> Hi and if you are using 8.04 you may try and use the alt, F2 keys and enter the command ```
gksu displayconfig-gtk
``` and adjust your resolution there along with the driver.

hi, hope u all good ?

i have a few questions if you can answer....

1) Is there something like Control Panel in Ubuntu? The reason I ask is to know if i can get a list of the components installed and if i cud change the dirvers and have more funtions on it.

2) I have an accounting package software which works well with windows but because its an .exe file it does not install in Ubuntu. Is ther a away I can installl it in ubuntu??

3) Also in terms of programming what language and software is used to program my ubuntu. To what limit I can personalise ubuntu?

hope its not a hassel to reply ... thanks

---

### Post by overdrank on 2008-11-04
> **minhal said:**
> hi, hope u all good ?

i have a few questions if you can answer....

1) Is there something like Control Panel in Ubuntu? The reason I ask is to know if i can get a list of the components installed and if i cud change the dirvers and have more funtions on it.

2) I have an accounting package software which works well with windows but because its an .exe file it does not install in Ubuntu. Is ther a away I can installl it in ubuntu??

3) Also in terms of programming what language and software is used to program my ubuntu. To what limit I can personalise ubuntu?

hope its not a hassel to reply ... thanks

Hi and I will attempt to answer but I am sure there is other answers :)
1. You can use sysinfo
2. You can use windows in a virtual machine with Virtual Box of VMWare
3a.[https://help.ubuntu.com/community/Programming](https://help.ubuntu.com/community/Programming)
3b.That is all up to you the user. You can customize it all you are willing to learn. :)

---


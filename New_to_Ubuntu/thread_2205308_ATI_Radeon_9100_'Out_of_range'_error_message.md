---
title: "ATI Radeon 9100: 'Out of range' error message"
date: 2014-02-13
forum: New to Ubuntu
---

### Post by james89 on 2014-02-13
I can install either Lubuntu or Ubuntu or one of my PC's. 
When I try to do the same on another I get the menu to Try without Installation or Install but when I select one or the other, the white cursor flashes (top left hand corner of the screen) and then the screen goes black with a faint message in orange saying "Out of Range" and then some frequencies quoted.
Some message boards report this with instructions to amend command lines to cure the problem.
My problem is that I don't get as far as an actual installation on that computer. Any advice would be welcome.
I understand that Windows installations carry all the main drivers for various devices so that they will be recognised and supported. What happens on a Linux installation ?
Do I have different driver problems between my two PC's ? Is it a motherboard or processor issue or a Linux issue?
The problem case is on a Sapphire Axion RS300 board with a Celeron 2 GHz processor, Integrated graphs ATA radeon 9100 IGP

Thanks for any help you can give.

James

---

### Post by mastablasta on 2014-02-13
out of range & frequencies is message form monitor not computer. but the fault is that computer is setting wrong parameters for htis card.

unlike in windows in linux drivers are built in kernel (most of them, proprietary drivers are exception). you card is old and will be using opensource drivers. you can read more about them here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

now as for the booting issue - try some of the boot options. i would start with nomodeset. here is how to use them: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

let us know how it worked.

it's not the CPU issue. although it would be good to know exactly what model of the CPU you are using (hopefully it's a dual core one and it support PAE kernels).

---

### Post by james89 on 2014-02-13
Thanks for this initial advice.  Being completely new to Ubuntu I get pretty confused with some of the jargon.  Basically  I will try the links you gave but I can only work in Windows  until  I get a proper installation of  Ubuntu.
I understand a little from some commands  on Lubuntu  on my other PC  but don't see how to get any commands in anywhere before an installation  on this PC.
My monitor works fine in Windows  which must have supplied the drivers for that (I suppose?) as it was "plug and play".

James

---

### Post by Mark Phelps on 2014-02-13
> My monitor works fine in Windows which must have supplied the drivers 

Monitors don't need drivers; it's the video chipsets that use drivers and set the resolutions

---

### Post by mastablasta on 2014-02-13
boot options might solve it. you will can force the graphics chip to show vga mode first.

windows could have some basic drivers for that chip on install CD. but to get the all out of it one has to install ATI (now AMD) drivers.

---

### Post by mörgæs on 2014-02-14
Have you tried to install using the [alternate ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")?

---


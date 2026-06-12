---
title: "SD card reader stopped working."
date: 2012-07-07
forum: New to Ubuntu
---

### Post by whitetop on 2012-07-07
Hi, I am running Ubuntu 12.04 Studio on an Asus V series pc, it has a card reader which suddenly stopped working, I insert the SD card and the light indicates its inserted but the computer does not recognise it, When this problem occurred, I was running Ubuntu 10.04.1
 I had hoped that when I upgraded, it would work with the new system, no such luck.
Can anyone throw any light on this problem please.
Whitetop.

---

### Post by westcoast01 on 2012-07-07
Will the SD card work in other machines? If not this worked for me ...  right click dash select dash home ... start typing usb, select startup  disk creator, (I have a few iso's saved in downloads) if you can see  your SD card listed select erase ... close startup disk creator ... your  SD card should be in listed in the unity bar, right click and select  format. Of course you will lose all the info on the card but at least it  will be usable again. Best of luck.

---

### Post by hypnot0ad on 2012-07-07
> **westcoast01 said:**
> Will the SD card work in other machines? If not this worked for me ...  right click dash select dash home ... start typing usb, select startup  disk creator, (I have a few iso's saved in downloads) if you can see  your SD card listed select erase ... close startup disk creator ... your  SD card should be in listed in the unity bar, right click and select  format. Of course you will lose all the info on the card but at least it  will be usable again. Best of luck.

This worked like a charm.
Thank you
and good luck to you OP.

---

### Post by Futant on 2012-07-07
Not sure if this is helpful but with my laptop (Dell xps l502x, Ubuntu 12.04)) I have to put the card in the reader then restart before it will recognise it. There is apparently a way of sorting it out but I haven't got round to it yet...

---

### Post by mgmiller on 2012-07-07
If you have right clicked the card reader drive and selected "safely remove"  it will turn off power to the card reader and will not see it again unless it is unplugged and replugged into the usb port.  I had this problem with a built in card reader in a desktop.  I had to open the case and unplug the card reader from the motherboard and then plug it back in while the machine was running to get it to see the card reader again.
I only use "eject" to remove cards now and I don't have the problem any more.

---

### Post by marcelo_ni on 2012-07-08
Running 10.04 on Acer 5542 laptop.
My machine can read a 1 Gb SD card, but not one of 4 Gb capacity. In fact, the trouble is the same with two 4 Gb cards. It happens both using an USB multi card reader, and the builtin one. That is why I am blaming the module and not the hardware.
Of course, both 4 Gb cards are perfectly readable on a Acer Aspire One netbook runnning Win XP.
I  can "safely remove drive" once and again using the 1 Gb card, so there is not a matter of current supply. 
The trouble started after some kernel upgrade. 
Could someone help?
TIA

---

### Post by mgmiller on 2012-07-09
I assume the acer aspire has a built in SD card reader and the Ubuntu machine has one that is either plugged into a USB port or was installed in the case and plugged into the USB port on the mobo.

I also had an issue with SD cards larger then 1 Gb until I realized that the card reader must be SDHC compliant or it wont read the larger capacity cards.  In my case, I had to get a new card reader to install in my tower case that was SDHC compliant.  Problem solved.  The older SD card readers cannot read cards larger then 1 or 2 Gb.  The form factor of the SDHC cards is identical to the older SD cards, so they do fit in the older readers, but they won't work.

---

### Post by whitetop on 2012-07-15
Hi to all people who have answered my question on SD card reader not working,

The reader is inbuilt in the Asus computer and at the outset, it did read 128Mb cards, but it suddenly stopped working, and since then I cannot use it, I can however use a USB card reader, I would rather use the inbuilt one.

Whitetop.

---


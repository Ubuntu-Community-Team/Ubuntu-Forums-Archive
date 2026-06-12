---
title: "Okay to use SDHC card instead of USB stick?"
date: 2012-04-11
forum: New to Ubuntu
---

### Post by whatsaterminal on 2012-04-11
sorry if this has been covered before but i searched the ABT forum using search terms 'SD card' and 'SDHC card' with no useful result. 

i notice the official directions on Ubuntu.com and on PendriveLinux.com always refer to using a USB flashdrive (but never a SDHC card) as an alternative to the CD install/liveDrive, but some forum posters occasionally mention using a SDHC card and they never say it does *not* work.
 
can this be made to work  satisfactorily and does it matter what class (R/W speed) it is?

thanks

what's

---

### Post by tea for one on 2012-04-11
__Good evening

As far as I understand, SDHC cards perform like SD cards and I am sure that you will have no problems.

I have used SD cards to move data from one PC to another via Nautilus within Ubuntu and I have also used an SD card to create a "live" Ubuntu image with persistence.

There is one tip that is worth watching - when you unmount the SD card, I have found that it is better to "eject" the media rather than "safely removing the drive" because you sometimes have to reboot in order to re-activate the drive when the drive is an integral built-in card reader.

i.e the card reader is _not_ a USB stick with card reading slots.

---

### Post by anewguy on 2012-04-11
If what you are trying to do is create the bootable live image on a SDHC card, you would need your PC to be able to boot from it.  So, you'll need to check in your BIOS settings for boot options and see if it allows booting from a SDHC card (or any other card) in a card reader.  My bet:  no.  I doubt it will make any difference if the reader is attached via USB.  I just don't think that support will be there as usually these readers require a driver.


Dave ;)

---

### Post by snowpine on 2012-04-11
It depends on your BIOS. I have one netbook that can boot from SD (asus eee) and one that cannot (dell mini).

---

### Post by tea for one on 2012-04-11
SDHC cards are SD cards with HC (higher capacity - up to 32GB).

I only have SD cards in my possession (i.e. 4GB) and I confirm that I have used them with a "live" Ubuntu image booting from an integrated card reader and also from a USB stick with card reading slots.

I will add the caveat that, similar to USB sticks, some brands work better than others. Kingston and Verbatim perform fine.

---

### Post by anewguy on 2012-04-11
> **tea for one said:**
> SDHC cards are SD cards with HC (higher capacity - up to 32GB).

I only have SD cards in my possession (i.e. 4GB) and I confirm that I have used them with a "live" Ubuntu image booting from an integrated card reader and also from a USB stick with card reading slots.

I will add the caveat that, similar to USB sticks, some brands work better than others. Kingston and Verbatim perform fine.

Since most internal readers still connect via USB, you got me curious.  I decided to try it but with an external reader/writer instead of internal one.  unetbootin is indeed burning the ISO to the card as I type this.  This would indicate to me that as long as you can boot from USB it might work as well.  I'll post back with the result.

While simple, I still find the idea of using a card of some type in a card reader/writer quite interesting - no need to carry a CD if you have a small external reader/writer like I picked up for an old laptop and just dug out of the junk box.  The thing is only 1 1/2" x 3" -> small enough to fit in your shirt pocket excluding the cable.  I wonder how much smaller we can make it?  While I am burning in a reader/writer, it's actually a micro-SD in the SD adapter.  So, it is quite small.

Ok, things just finished up - yep, you can even do it from an external reader/writer - never knew that.

Who'd thunk it?

Thanks for the info!

Dave ;)

BTW - that's why I said it didn't matter if SD or SDHC.

---

### Post by tea for one on 2012-04-11
[QUOTE=anewguy;11836635  While I am burning in a reader/writer, it's actually a micro-SD in the SD adapter.  So, it is quite small.

Dave ;)

BTW - that's why I said it didn't matter if SD or SDHC.[/QUOTE]

Hello Dave

I'm pleased that I have provided some useful info.

As you say, micro-SD cards are tiny and easy to lose, so I suggest you buy a USB card reader with a two metre cable.

I use one that doubles up as a belt..............

---

### Post by whatsaterminal on 2012-04-11
okay, thanks everybody. 
now i am looking at my Boot Device priority listing under BIOS and it shows 
'USB DISK 1'
'[ATAPI] CD-ROM'
'[HDD : SM-ASUS-PHISON]

i assume USB means USB, 
and i assume HDD refers to the internal solid state drive (8G SSD in this eee-PC701SD)
but i sure can't figure out what ATAPI CD-ROM means since this little toy has NO optical drive. could it be referring to the SD card slot? i have a usb flashdrive plugged into the port, and i inserted a blank SD card into the slot just in case it needs to sense a card to offer the option. 
thanks for all the advice

what's

---

### Post by snowpine on 2012-04-11
> **whatsaterminal said:**
> okay, thanks everybody. 
now i am looking at my Boot Device priority listing under BIOS and it shows 
'USB DISK 1'
'[ATAPI] CD-ROM'
'[HDD : SM-ASUS-PHISON]

i assume USB means USB, 
and i assume HDD refers to the internal solid state drive (8G SSD in this eee-PC701SD)
but i sure can't figure out what ATAPI CD-ROM means since this little toy has NO optical drive. could it be referring to the SD card slot? i have a usb flashdrive plugged into the port, and i inserted a blank SD card into the slot just in case it needs to sense a card to offer the option. 
thanks for all the advice

what's

When you turn on your EEE, press the Esc key to choose the boot device.
(If you are prevented, then disable Boot Booster in BIOS.)

---

### Post by whatsaterminal on 2012-04-11
**@#!!)++

sorry, having a "Homer moment" here. 
yeh, when i hit <esc>, it's right there...
HDD: SM-ASUS-PHISOM SSD
USB: USB DISK
USB: SINGLE Flash Reader

so i assume USB DISK is referring to the SD card...


my apologies, thanks Snow

---

### Post by snowpine on 2012-04-11
> **whatsaterminal said:**
> hi snow, see above, i assume we crossed in cyberspace.

uh, sorry, what i meant to say was, yeh, i did that, with the result shown above

The "result shown above" is from your BIOS screen.

Try pressing Esc when you turn on the computer. (But it is possible your model EEE is different than my model EEE.)

---

### Post by anewguy on 2012-04-11
> **tea for one said:**
> Hello Dave

I'm pleased that I have provided some useful info.

As you say, micro-SD cards are tiny and easy to lose, so I suggest you buy a USB card reader with a two metre cable.

I use one that doubles up as a belt..............

I've got a short one for it, but unfortunately even a two-meter cable is a little shy of making a belt for me - did I mention that I'm more than a little large?  ;) ;)  Also just found out I'm diabetic - there goes all the things I like, and I get to be like a portion of an old, old George Carlin joke - "it's okay to prick your finger, but....".  I gotta say - still hurts!

Have a good one!

Dave ;)

---

### Post by whatsaterminal on 2012-04-12
Welllllll, i can at least say it worked no worse than the conventional USB flashdrive, for me. so i am going to mark this thread as "SOLVED'. 

however i still had virtually the same undesirable outcome as described in painfully verbose detail under my other thread, 
			 			 			                         [COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[Pendrive Boot hangs eee-PC 701SD (WAS Trojan Virus?)]("http://ubuntuforums.org/showthread.php?t=1955857")

with a couple minor differences. at least this time, i *did * get LAN connectivity, for a few minutes when it booted the first time. however successive boot attempts failed as described in my other thread. i have absolutely no clue why it would boot on the first try and then fail on repeated subsequent attempts. 

ideas anyone? i think i'll try my luck with Kubuntu. after all, this little 701SD is supposedly based on KDE code. about which i know absolutely nothing....

thanks everybody, especially Snow, for your kind suggestions. 

-what's

---


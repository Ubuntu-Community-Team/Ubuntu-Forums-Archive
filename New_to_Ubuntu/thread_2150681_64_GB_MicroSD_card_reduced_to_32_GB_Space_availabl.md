---
title: "64 GB MicroSD card reduced to 32 GB Space available?"
date: 2013-06-01
forum: New to Ubuntu
---

### Post by j814wong on 2013-06-01
**[COLOR=#333333]I have a Sandisk 64Gb MicroSDHC card. I've been using it for sometime on Android and. I've used Android to format it but never to partition it. I've also used Android to wipe data on the card. I've formatted it varous times again on Ubuntu. [/COLOR]**

[COLOR=#333333][FONT=arial]
The card was working fine but today, I decided to format and clear all the data on it. Much to my dismay, after when plugging in the card and formatting it, Windows read it to have only 27.8 GB space even though it was empty. Ubuntu also showed 27.48 GB only.

I've not much problems with the card on Android and Ubuntu but today, this serious problem occured.  Just how does a 64GB card reduce to 27.48GB?  I've formatted the card to FAT32 and EXT4 multiple times to no avail with GParted.

Previously, some time ago, I've formatted the card to FAT32 and because the computer, I forgot if it was Windows or Ubuntu and because the computer read it as having 30GB space, named the card 32GB Volume or something like that (The name has long since changed to one of my choosing).  However, Ubuntu still read the card as having 64GB of space and filling it up with more than 30GB worked just fine.

What happened? How do I resolve this?  I need the card to work on both Ubuntu and Android.

Note: You may wonder why this is on a Ubuntu Forum.  I asked here because I am looking for a Ubuntu based solution and much of my interactions with the card has been through Ubuntu or Android.

[/FONT][/COLOR]This is my card.  [http://www.amazon.com/dp/B005V7WIA2](http://www.amazon.com/dp/B005V7WIA2)  Based on reviews alone, it seems to be very good quality.  I've used the card on Ubuntu, and Motorola Defy (Android), and the Motorola Xoom (Also Android).  Both Android and Ubuntu have worked with the card just fine except for one thing  Occasionally, when copying files to or from the card, I get an error message.  Sorry but I don't recall what the message said.

Also, sorry for this mess of a post.  I'll try to reword it once I have the time or overcome my exaggerated grief for this unexpected tragedy.

---

### Post by Paqman on 2013-06-02
Open up the Disk Utility tool and take a look at the card. Is it just showing as a single partition? Is there free space shown? Using this tool you should be able to either expand an existing partition, delete any extraneous ones, etc. You'll need to unmount the card before making any changes.

---

### Post by j814wong on 2013-06-05
I see a single partition with only approximately 30GB of space.

[IMG]http://i.imgur.com/zbT9mer.png[/IMG]

---

### Post by varunendra on 2013-06-05
May be write a fresh partition table using gparted? This will delete the current partition as well as MBR and will write a fresh MBR (DOS compatible by default).

And what does 'sudo fdisk -l' show? I'm interested in the CHS value, although have no idea if it can even be related. The only other really wild guess I can make is that probably one of two internal flash memory chips got corrupted somehow, leaving the card with only half the capacity 'physically'.

---

### Post by j814wong on 2013-06-06
> **varunendra said:**
> May be write a fresh partition table using gparted? This will delete the current partition as well as MBR and will write a fresh MBR (DOS compatible by default).

And what does 'sudo fdisk -l' show? I'm interested in the CHS value, although have no idea if it can even be related. The only other really wild guess I can make is that probably one of two internal flash memory chips got corrupted somehow, leaving the card with only half the capacity 'physically'.
Thanks for helping out.
```
Disk /dev/sdd: 29.5 GB, 29504831488 bytes

255 heads, 63 sectors/track, 3587 cylinders, total 57626624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ec74a


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048    57626623    28812288   83  Linux

```
GParted shows the SDCard as if it were a 29.5 GB card: A single partition with 29.5 GB available.

---

### Post by varunendra on 2013-06-06
Perhaps I found "why", but not "how" to get the lost capacity back yet. Although you said -
> **j814wong said:**
> I have a Sandisk 64Gb Micro**SDHC** card.
But the link you provided is for an SDXC card :
> **j814wong said:**
> This is my card.  [http://www.amazon.com/dp/B005V7WIA2](http://www.amazon.com/dp/B005V7WIA2)

From [http://panasonic.net/avc/sdcard/information/sdxc_english.html](http://panasonic.net/avc/sdcard/information/sdxc_english.html) :-
> **[COLOR="#FF0000"]SDXC memory cards should not be used in non-compatible host products.[/COLOR]**
further down on the page (in red letters !) -
> **[COLOR="#FF0000"]* When formatted, the card capacity will be reduced to half or less[/COLOR]**, or the SD host product will not be able to recognize the card, making it no longer SDXC compatible.

In compatible OS list, it mentions the big brothers only (MS and Mac), not Linux, but says this :
> When you use your SDXC memory card with your PC, please **confirm if your PC supports exFAT**
Linux does support exFAT, so I think it was some non supporting device or OS where you formatted the card, causing the trouble.

So far, I could find only this much. Will post back if I found some fix to recover its capacity. I suggest you do the same (search), and post back here if you found a fix. I'm sure many users would be affected by this issue and a fix would really help a lot of people.

---

### Post by varunendra on 2013-06-06
Couldn't find a fix in quick search, but noticed something more from the same site : [https://www.sdcard.org/downloads/formatter_3/](https://www.sdcard.org/downloads/formatter_3/)
> The SD/SDHC/SDXC memory cards have a "Protected Area" on the card for the SD standard's security function. The SD Formatter does not format the "Protected Area".
....implying that generic formatting utilities *may* format this "protected area", which I assume can be the reason for the capacity loss (just like the modern HDDs have part of their firmware on the platter itself, containing info about their geometry).

Based on above info, I *assume* that if you have another identical card, then maybe -
```
sudo dd if=/dev/sdb of=/dev/sdc
```
(where sdb is healthy card and sdc is the problematic one) may help, since dd copies every bit from the source device to the destination device, not caring whether the block is empty or occupied. But since the drive would appear to be half the size of the healthy one, I suspect it may return errors and not start copying at all.

Also, be advised that dd is a very slow process and a risky one too if you confused the drive names. Besides, it is just a wild guess, with very little hope of success.

---

### Post by j814wong on 2013-06-06
MY MISTAKE!  My card is MicroSDXC not SDHC.  Sorry.

I have never had any problems with teh card when formatting to FAT32 on Ubuntu.  But recently, I was uysing the card on Android, where it has been working just fine.  However, I then used Android to wipe the card.  That could be the cause of the problem.

---

### Post by varunendra on 2013-06-06
> **j814wong said:**
> ..However, I then used Android to wipe the card.  That could be the cause of the problem.

Most probably. Please let us know if you find a solution, or the result of the dd command thing if you try that. Thanks.

---

### Post by j814wong on 2013-06-09
> **varunendra said:**
> Most probably. Please let us know if you find a solution, or the result of the dd command thing if you try that. Thanks.
Unfortunately, I don't have a identical card to the formerly 64GB one.

---

### Post by peskito on 2013-10-15
Hey,
Had the same issue with this same SDXC card that I formatted with my CyanogenMod that actually doesn't support exFAT.
I don't have access to Windows so I couldn't try the SDFormatter official tool.

I tried to format the card from ClockWorkMod to no avail... still about 30gb.
I tried many times with Ubuntu 13.10 Disk Utility and GParted... still the same.

The magic came from the little free Android app [AParted]("https://play.google.com/store/apps/details?id=com.sylkat.AParted&hl=en") . One click: issue solved. :)

---


---
title: "[SOLVED] Unable to run Ubuntu test demo from boot CD"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by JDtheHutt on 2008-07-25
Hi, I'm completely new to Linux and have finally decided to move off Windows as my daily OS and try something different.

I have downloaded both the 32 bit and 64 bit versions of Ubuntu and thought that first of all I'd run the disc and see what it was like and if it worked on my machine.
However, both the 64 bit and 32 bit fail to load correctly.  I boot up into the menu and select to test Ubuntu.  It then goes to the loading screen and I see the bar going back and forth for a bit, then it starts to fill up from the left and ends up hanging at exactly the same point every single time: just before it fills three blocks on the load bar.

I verified the write of the CD when I burnt the iso on, I have run the CD check utility in the boot menu and I have tested my memory multiple times using the boot menu utility.  All come up as perfect passes.

I have been checking my hardware to see if there are any issues causing it to hang.  Some of it I have located on various websites and hardware lists as cleared, others I cannot find references anywhere for, so do not know whether they are compatible or not.

I list my hardware here and whether I have found any references regarding compatibility.

> Memory (Corsair XMS2 6400) – Compatible

CPU (Intel Core 2 Duo E6600 Socket 775 2.4GHz) – Compatible

Soundgraph iMON VFD Black – Compatible

GPU (MSI RX1950XT-VT2D256E-HD 256MB DDR3 TV PCI-E) – Unknown, although reports seem to indicate the 1950 chipset is compatible.

Motherboard (MSI S775 Intel 975X ATx Audio Lan power Up Edition Platinum) – Unknown

Mouse (Logitech G7) – Unknown

DVD (Samsung Writemaster SH-S183A/BEBN SATA) - Unknown

Does anyone have any idea what might be wrong please?  I am completely new to Linux, so not sure if there are any other tests I can run to check my hardware or common errors I should look for.  I've been browsing around a lot of sites, but have so far been unable to diagnose or solve the issue myself.

Thanks for any advice, it'll be very appreciated!

---

### Post by pedro_orange on 2008-07-25
It is probably a piece of hardware in your machine Ubuntu doesn't like.
I've seen it happen with a few network cards, typically wireless. Try taking it out and see if it boots up.

---

### Post by JDtheHutt on 2008-07-25
Hi Pedro, thanks for replying.  I'm thinking it is a hardware issue, although I don't think I have anything else plugged in other than my listed items.
I did have a Netgear wireless card but it stopped working with XP after a driver update and caused hang-ups there, so I thought I'd removed it.  I'll open up the case and check I did, in case it is still lurking inside.

If my BIOS has its virus protection enabled, could that be an issue for booting Ubuntu?  It only just occurred to me while I was working, but not even sure if it is enabled or not.

---

### Post by philinux on 2008-07-25
I have a feeling it could be the graphics card. 

I cant remember all the options from the livecd menu. Choose the safe graphics mode and see if that will boot.

---

### Post by JDtheHutt on 2008-07-25
> **philinux said:**
> Choose the safe graphics mode and see if that will boot.

Sorry, I should have mentioned that I have already tried all of the available ways to boot from the menu, including the safe modes.  Exactly the same issue.  I also removed all peripherals, including any external drives.

Places I've been reading did mention that the ATI cards were rather more cranky with Linux than Nvidia, so I'm hoping it's not that!

---

### Post by philinux on 2008-07-25
Have you looked under the F6 options too?

What we need is to get it to boot without the quiet option.

Then you'll see the text messages and errors as it tries to boot. Instead of just the loading bar.

---

### Post by JDtheHutt on 2008-07-25
Ah ok, I haven't accessed those!  I'll give that a go tonight and see what it outputs as it loads and post back here with the details.

Thanks philinux!

---

### Post by JDtheHutt on 2008-07-26
Thanks guys, it was the wireless network card.  Should have been the first thing I checked, but I could have sworn I'd taken it out ages ago.

---

### Post by unutbu on 2008-07-26
Thanks for the update JDtheHutt. For future googlers who find their way here, what was the make/brand of the network card?

---

### Post by hyper_ch on 2008-07-26
hmmm, the wireless card shouldn't cause ubuntu to not boot correctly... hmm....

---

### Post by JDtheHutt on 2008-07-26
The card is a Netgear WG311 v2

No idea why it prevents Ubuntu from booting, but it is most definitely the culprit as I'm having a great time playing around with it now.  I'll update my title to SOLVED as well now, I forgot to earlier.

---


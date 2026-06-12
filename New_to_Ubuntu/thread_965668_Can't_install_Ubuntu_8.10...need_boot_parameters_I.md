---
title: "Can't install Ubuntu 8.10...need boot parameters I think."
date: 2008-10-31
forum: New to Ubuntu
---

### Post by Adamantus on 2008-10-31
Hey, I installed Ubuntu 8.10 on my old laptop using an install disk I got from a magazine and it worked. I was able to use it for about a week until my computer was stolen. I got a new computer (HP Pavillion dv5, AMD Turion X2 64-bit, ATI Radeon 3200 Graphics card, Windows Vista SP1) and downloaded and burned the 64 bit version (I checked the hash and it matched up). 

I got to the screen where it has the options to install, try without installing, etc. Every option except "boot from disk" causes the screen to freeze. I've tried changing the boot parameters (deleting hcsplach--, deleting hcsplash and adding irqpoll, and a couple others). None that some website suggested seemed to work. I asked on another forum and some guy said that it probably needed to be a video driver boot parameter or something.

Anyway, I also tried using the alternate text-based install and, when installing, I got like a hundred errors saying some files couldn't be downloaded. I had to eventually abort the installation and was luckily able to still boot from Vista, but I now have a nice partitioned hard drive at least.

I really want to install Ubuntu but want to do it through the graphic based installation (the text based almost destroyed Vista and everything else). What are some boot parameters I could try to install? Are there any other ways around this problem?

---

### Post by spiderbatdad on 2008-10-31
all_generic_ide

---

### Post by Adamantus on 2008-10-31
That didn't work. Just to make sure I'm doing it right, I push F6 to bring up the boot parameter which is a long .gz file with quite splash-- at the end. I delete "quite splash--" and add "all_generic_ide" without the "".

That's what I did and the computer still froze up.

---

### Post by spiderbatdad on 2008-10-31
It sounds like the cd image might be bad. I assume you tried noapic nolapic? Though the kernel doesn't usually need those parameters to boot now...at least not on machines where I previously needed them.

for vga (due to your ati card) maybe vga=792 you can find the array here:[http://en.wikipedia.org/wiki/VGA](http://en.wikipedia.org/wiki/VGA)

---

### Post by Adamantus on 2008-10-31
I tried the VGA=792 and it didn't work.

Also, I've tried burning the two downloaded .iso files on two different disks. how can I make sure it's not a bad image?

---

### Post by Adamantus on 2008-10-31
Does anyone else have any ideas on what to do?

---

### Post by Adamantus on 2008-10-31
One last try at a response: it seems like my I and I alone seem to have these types of problems (i.e. ones where I'm using completely normal hardware and nothing seems to work).

Either way, I'm actually really liking Vista, even more than Ubuntu I think. It's working extremely fast, so maybe going to Linux isn't necessary. But I still would like to be able to dual boot with Linux. Any help?

---


---
title: "RAM issues with MSI netbook"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by notfred87 on 2012-10-07
Ill start by saying that this is my first day with linux...so definitely as new as it gets! 

Installed Ubuntu on a MSI U100 Netbook. I logged in and it is only recognizing just over 400 mb of ram. I have 1.5 GB installed. It is a 32bit version of Ubuntu, any ideas on how to fix it? 

It has an Intel® Atom™ N270 1.6GHz processor. Mobile Intel(R) [9]45 Express Chipset. 1 GB of RAM is built into the mother board. I looked at the details in the settings and it isn't seeing my RAM or my video card driver... 

Any help would be great! I am really really tired of Windows. I want this to work so I can completely be rid of Windows! (its a second computer, first one is a mac for work and other important tasks)

P.S. Please remember I am completely new to linux. Don't confuse me. ;)

P.P.S. Sorry if there is another thread that answers this problem; I searched through other threads but didn't see anything that answered my problem (that I understood). Let me know if this should be moved. Thanks!

---

### Post by Old_Grey_Wolf on 2012-10-07
Open a terminal and enter the command
```
free
```
Paste the output of the command back here in the thread.

---

### Post by mips on 2012-10-07
Also post the output of **sudo dmidecode --type memory** while you are at it.

---

### Post by Old_Grey_Wolf on 2012-10-07
mips, I was thinking possibly miss-matched RAM myself. ;)

---

### Post by notfred87 on 2012-10-08
Thanks for the quick replies! My keyboard is frozen (long story; Manufacturer patch went wrong) so I can't boot into linux. The first option on the boot screen is xp. Since I can't use my keyboard it defaults after a couple seconds to xp. While that is being repaired, do you think a USB keyboard might get around this? My USB mouse does work when booted.*

---

### Post by newb85 on 2012-10-08
I would expect a USB keyboard to do the trick.

Be warned, though, that if the manufacturer has any suspicion that the issue is software-related, they might restore it to factory settings, wiping out your Ubuntu install.  I don't have experience with MSI, but in general, manufacturers don't have a lot of respect for third-party OSes.  The bottom-line: back up everything before sending it in for repairs.

---

### Post by audiomick on 2012-10-08
> **notfred87 said:**
> ...do you think a USB keyboard might get around this? My USB mouse does work when booted.*

If a USB keyboard does not respond during boot up, you might want to look in the BIOS for an option called "legacy USB" or something similar. Some machines need to be told to enable USB support right at the start of boot up.

---


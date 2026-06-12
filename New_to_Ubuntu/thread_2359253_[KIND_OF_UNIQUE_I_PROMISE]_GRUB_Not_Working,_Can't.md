---
title: "[KIND OF UNIQUE I PROMISE] GRUB Not Working, Can't boot"
date: 2017-04-21
forum: New to Ubuntu
---

### Post by ss108 on 2017-04-21
I am having a problem wherein GRUB usually doesn't even appear (my computer usually just hangs on the "press F12 for boot menu" screen when I turn it on), and on the rare occasions when it does cannot load Windows or Ubuntu (got BSOD trying to boot into Windows). I have had this computer for about two years; this problem came out of the blue today.

Selecting the correct boot drive doesn't help at all.

I booted into Ubuntu via USB and tried to run boot-repair, but I don't even get the option to do a "recommended repair". All I could do was generate a report. Here is that report: [https://pastebin.com/nHxeu7eG](https://pastebin.com/nHxeu7eG)

Sometimes booting off the USB doesn't even work. 

What should my next steps be?

---

### Post by oldfred on 2017-04-21
Report shows no drive?
UEFI entry say you had Samsung 850 SSD.

Does BIOS see drive?
Only if BIOS sees drive, then does Disks utility upper right corner icon and Smart Status tell anything about drive?

---

### Post by ss108 on 2017-04-22
Hey, thanks for replying. BIOS can see both of my drives, and the correct one is selected to boot.

> t[COLOR=#000000]hen does Disks utility upper right corner icon and Smart Status tell anything about drive?[/COLOR]

Not sure where I am supposed to be looking for that...?

Also, for what it's worth, from BIOS doing "boot override" to the other SSD, which houses Windows, doesn't help.

---

### Post by shridhar-kapshikar on 2017-04-22
You can take a look to below URL:
[https://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows](https://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows)

This will explain you how to update a grub for multi OS.

---

### Post by oldfred on 2017-04-22
I think my screen shot is older version, but should be similar.

Report did not show a Windows drive either. Did you disconnect it before running report?

---

### Post by ss108 on 2017-04-23
Hi all,

So when I turned on my comp today to try to follow the instructions on shridhar's link, everything worked fine. I did not turn on my computer at all yesterday, so that apparently helped. My computer was not hot at all on Friday when this problem surfaced, so I am not inclined to think that it cooled down over a day and that this is what helped.

I never disconnected a disk. When I look at the disks utility now, it shows both. Should I look into the possibility that a disk may have disconnected on its own in order to avoid this problem in the future?

---


---
title: "eeepc wireless device not managed"
date: 2011-10-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by CaptainMark on 2011-10-01
today ive wiped meego (RIP) off my netbook in favour of OO, however the network manager applet reports that under the wireless heading my device is not managed, ive used ubuntu for several years (including 6 months with this very same netbook on 11.04) and never had wifi issues :confused: so i dont even know where to start diagnosing the problem, could someone with more wifi experience please advise.... 


mark

edit: i have a eeepc 1001px i believe the wifi adapter is an atheros card????

edit edit: however my usb alfa awas036neh adapter works flawlessly

---

### Post by mikewhatever on 2011-10-01
An Atheros card needs the driver, always did. It's not a problem, you just have to install it. Search for the Additional Drivers program.

---

### Post by CaptainMark on 2011-10-02
ive never needed to install additional drivers for it, and i already checked the additional hardware drivers manager and nothing is listed as needing to be installed, i had OO installed on this netbook earlier on in the dev cycle, about mid alpha2 and i didnt have this problem, only has it happened now going back to OO

---

### Post by cariboo on 2011-10-02
I tried a live usb on my Dad's Acer laptop a couple of weeks ago, wireless worked out of the box, so I didn't bother checking what model of Atheros it was using.

@CaptainMark, I had the same problem in Fedora, with a different make of wireless device, what solved it for me, was the instructions in [this]("http://ubuntuforums.org/showthread.php?t=571188") post.

I have an unencrypted access point in my shop, so I used the instruction for an unencrypted connection. Once the device connected to the access point, it all of a sudden became managed.

---

### Post by ft_ on 2011-10-02
maybe your driver is blacklisted in /etc/modprobe.d
Check it in the wireless file and unblacklist it.

---

### Post by mikewhatever on 2011-10-03
Interesting. Perhaps the OP can post the output of lspci.

---

### Post by CaptainMark on 2011-10-03
too late, ive put meego back on the netbook already, i found ubuntu was too heavy going for the netbook, only i dont need it do anything and everything so a small distro works much better, ill have to ditch it when its replacement tizer...somnething comes out next year, alas ubuntu stays firmly established as my desktop os of choice though despite trying experimenting with many others,

---


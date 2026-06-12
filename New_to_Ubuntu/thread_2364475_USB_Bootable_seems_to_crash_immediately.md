---
title: "USB Bootable seems to crash immediately"
date: 2017-06-23
forum: New to Ubuntu
---

### Post by jimip1989 on 2017-06-23
Hi,

I'm trying to install Ubuntu (ubuntu-17.04-desktop-amd64) on my PC:

i5-4690k
4gig ram ddr3
GTX 970
Asus Z97 mobo
750W PSU

I point the system to boot from the USB stick which works fine. It then takes me to:

[http://imgur.com/c6wsJ2A](http://imgur.com/c6wsJ2A)

Hit enter. Next thing I see is the following... for eternity.

[http://imgur.com/XZNA1Wi](http://imgur.com/XZNA1Wi)

I am a total noob in this dimension. Halp pls.

*Edit: Saving file as DD type, see if that makes a difference.

**Edit: No difference. Exactly the same thing on the screen.

Cheers

James

---

### Post by jimip1989 on 2017-06-24
Hello? I literally seem to be unable to install Ubuntu.

Any help at all?

---

### Post by howefield on 2017-06-24
Try using the nomodeset option when booting if you haven't already.

Pressing the letter e key at the grub screen and appending the word nomodeset on the line ending with quiet splash might get it going. This will revert on next boot so you may need to make it permanent if it works.

---

### Post by blarney77 on 2017-10-23
You will have to use the nomodeset option to get into the install, but once you get into the install, just download the latest nvidia driver and you will be fine.   You must replace "quiet splash" with "nomodeset".   It assumes a more generic video driver that will get you past that.  I ran into this problem with my GTX-970 and other Linux distros., like Mint.  (Hmm... Ubuntu based)   anyway, good luck.

---


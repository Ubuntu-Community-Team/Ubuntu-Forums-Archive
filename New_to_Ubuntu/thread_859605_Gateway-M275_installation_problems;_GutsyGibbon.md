---
title: "Gateway-M275 installation problems; GutsyGibbon"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by ibgeorgeb on 2008-07-14
[-o<[-o<E installation from the live CD GRUB menu; and then I 'F6' to the BootOptions, then deleting "quiet splash" and replacing it with "vga=774; then after the two "--" I have put "noapic". I've gotten up to the Ubuntu sound bit (a bit choppy) and then a blank light tan screen (no icons). The HDD is still being accessed and the fan is working.

Nothing more happens after the choppy music, HDD being accessed, and tan screen. The cursor works (intermittently) 

Any assistance will be greatly appreciated.

ibGb

---

### Post by Jim! on 2008-07-14
What are your system specs? If you don't meet the minimum requirements it probably won't even load up as a live CD, let alone install.

---

### Post by ibgeorgeb on 2008-07-14
A friend gave me this "broken" tablet, I installed a new HDD (she lost the recovery disk, etc.) so I'm give you the specs from the Gateway website. She never upgraded it or anything. [http://support.gateway.com/s/Mobile/Gateway/M275/3501734sp3.shtml](http://support.gateway.com/s/Mobile/Gateway/M275/3501734sp3.shtml)

Also, I've tried searching Ubuntu forums; (see [http://ubuntuforums.org/showthread.php?t=488235](http://ubuntuforums.org/showthread.php?t=488235) )

thank you, ibGb

---

### Post by ibgeorgeb on 2008-07-14
I tried another live install:

#1) at the GRUB menu I chose the first line; then
#2) <F6>
#3) I eliminated "splash", added "... vga=774 noapic --" in its place; hit <enter>
#4) black screen came with, "You passed an undefined mode number." I entered 'scan'; I chose #2 0F02 80x43
#5) tapped the <FN> + <F3> keys combination; about 3 minutes later...
#6) the sound bit came on; sounded good (not as choppy)
#7) Then I got the following error about 1 minute later (never got this error menu before): Error Message:

"There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log inz"

Maybe, there ain't enough RAM. The BIOS indicated 256 Mb.Maybe 512Mb will work?

*_In the meantime, the optical drive is working hard, the error menu went away and I'm looking at a light tan screen._* The <FN> + <F3> combination don't turn off the screen anymore.

[B]
Any thoughts? Anyone. Thank you.  ibGb[/B]

---


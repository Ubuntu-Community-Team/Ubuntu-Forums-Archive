---
title: "Booting live CD changes BIOS time"
date: 2018-07-08
forum: New to Ubuntu
---

### Post by orangesky on 2018-07-08
Hi, I would like to use the live CD to boot up and do my internet banking. 
But, every time I boot into Ubuntu (ubuntu-18.04-desktop-amd64.iso),  it changes my BIOS time.  At first when Ubuntu starts up it shows the local time correctly and after a few seconds it changes to UTC. From then on the BIOS time has changed too.
I learnt that there are methods to set to local time from the default UTC, so that BIOS time is not changed after reboot.
 But these methods are only after Ubuntu has loaded up and I have to remember once again to perform some task to change to local time.

Is there a way to boot Ubuntu live CD with the correct timezone? . For instance, in some linux distro the grub2 menu entry can contains the entry  "timezone=Country/City" like the line below:

[COLOR=#24292E][FONT=SFMono-Regular]linux (loop)/live/vmlinuz [/FONT][/COLOR][COLOR=#D73A49][FONT=SFMono-Regular]boot[/FONT][/COLOR][COLOR=#24292E][FONT=SFMono-Regular]=live [/FONT][/COLOR][COLOR=#D73A49][FONT=SFMono-Regular]timezone[/FONT][/COLOR][COLOR=#24292E][FONT=SFMono-Regular]=America/New_York [/FONT][/COLOR]


In such cases, those linux distro will boot up with correct local time (without changing BIOS time) and I could boot the downloaded ISO file as it is (without tampering with the original ISO file).

Is there such a way for me to do that with Ubuntu? I have tried the above (grub2) method with Ubuntu live CD , but it didn't work (maybe cause ubuntu iso is using casper?)

Not sure if I have expressed my problem clearly. If anybody know a solution to load the original live CD as it is with the correct timezone OR a way to stop BIOS time from being changed??  ....would be a great help. THANKS

---

### Post by Geoffrey_Arndt on 2018-07-09
Doing banking/finances (or anything like mission/critical functions) is "problematic" using Live, RO media.   Why do you believe it is a good solution?   Security (largely no), convenience (totally no)??   A couple much better approaches is a full install of CubesOS to usbv3 SSD [https://www.qubes-os.org/](https://www.qubes-os.org/)

Or even any main distro like Ubuntu, Elementary, etc on that external SSD device.

Then, no issues like date, time, persistence, security, updating, etc. etc.

---


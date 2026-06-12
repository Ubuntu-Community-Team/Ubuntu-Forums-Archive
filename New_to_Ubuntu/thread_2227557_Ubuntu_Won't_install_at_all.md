---
title: "Ubuntu Won't install at all"
date: 2014-06-02
forum: New to Ubuntu
---

### Post by Gareth_Newman on 2014-06-02
Hey All,

I had windows 7 on my PC, I upgraded to Windows 8.1 and I am sure like many people my initial reaction was, oh my good this sucks what an absolute waste of time and money...

So after hours of googling I decided to try Ubuntu, however immediately I have an issue, it doesn't seem to matter which one I try and install but I always get similar results, a very unusable machine, like I can't even get to installing it or running it from a live cd. It starts and then I get a purple/fuzzy/stripy screen. I just can't see anything to see what stage I am at. Hopefully this is a common easy fix, picture attached to show what happens.

Specs:

Nvidia 8800 GTX
2 x 2gb ram
AMD Athlon 64 Dual Core Processor
ASUS M2V-MX Motherboard

Hopefully image attached??

Cheers!![ATTACH=CONFIG]253685[/ATTACH]

---

### Post by Gareth_Newman on 2014-06-02
Reminds me of a commodore 64 loading screen!! haha

---

### Post by Duncubuntu on 2014-06-02
Are you running the Live CD from Windows or booting it up?
Does Windows still boot?
Are you trying to dual-boot?
What version of Ubuntu are you trying? Use 14.04 64-bit for compatibilities sake, and figure out what version you like best after a successful install.
Also how far does the CD get if your booting? Do you see anything before the lines?
Depending on your set-up you'll most likely want to search for information on Ubuntu 14.04/13.10 and UEFI installs.

On my machine I couldn't boot anything else (i.e Ubuntu) without disabling UEFI for that drive.

---

### Post by Gareth_Newman on 2014-06-02
Update.... so I unplugged the 8800 GTX and I got a little bit further (Motherboard graphics) I saw a Ubuntu 14.04 loading screen.... but then when that dissapears it just goes all fuzzy and crazy again, so it would appear to be a graphics issue, but I dont know what to do, it doesn't like my graphics card and it doesn't like my motherboeards on board graphics, where from here??

UEFI?? I am guessing thats a BIOS option, I will disable it. FYI currently still runing windows 8, and trying to boot from a Linux Live DVD of 14.04

---

### Post by Gareth_Newman on 2014-06-02
I can't find anything that says UEFI, I see a load of text fly down the screen like drivers and other important looking lines of text I think, and then the screen ends up unusabled :(

---

### Post by Gareth_Newman on 2014-06-02
I think it is working in the background, but I just can't see what it wants me to do. I think I need a non-graphical install?

---

### Post by Vladlenin5000 on 2014-06-02
The "nomodeset" option is required for some nvidia cards. Press any key when the boot starts - keyboard and human logo - and then, in the menu that'll appear, press F6 and select "nomodeset", then proceed to try or install. This should get you going in the installation process with readable video. After the first reboot make sure you select and install the recommended proprietary driver (last tab in System Settings > Software&Updates).

---

### Post by Duncubuntu on 2014-06-02
*EDIT* What Vladlenin5000 said is what I think may help as well, beat me to it ;) *EDIT*

You can try hitting f4 during that splash screen as well to get boot mode options.

---

### Post by Duncubuntu on 2014-06-02
This may also help: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Gareth_Newman on 2014-06-02
I tried this but still no luck, any key or F6 shows me alot more text but in the end I get the same blurry screen where I cannot read anything. :(

---

### Post by Gareth_Newman on 2014-06-02
Ok I tried another distro which said it was compatible with old hardware and that had similar issues, then I tried Mint and I thought it was going to fail as briefly I got a similar screen but then to my amazement in switched to a nice desktop and said running in software rendering mode your graphics are poo in this mode etc etc... but so far so good. Thanks for replies anyway.

---


---
title: "GRUB refuses to load, shows &quot;Error: File not found&quot;"
date: 2013-03-10
forum: New to Ubuntu
---

### Post by ShadowByte on 2013-03-10
This is really agonizing for me.  I was on Windows, when my battery ran out of power. It went into suspend mode, or tried to, but it sort of hanged there for well over 3 minutes, doing nothing. Suspend usually takes seconds. So I did a hard shut down, holding down the power button for a few. I rebooted and it shows the typical "GRUB Loading" screen, and hanged there. It did not change. Normally, it would only flash and then show me my OSes. I have a dual-boot of Windows 7 and Ubuntu 12..04. I tried booting into my Ubuntu Live CD and it would not load the desktop. Just goes blank screen on me.   I am currently on my BackTrack 5R2 live USB. I tried re-installing GRUB through here and it reported "Installation completed successfully. No errors reported." I rebooted and I got a new error - "Error: File not found". It shows it on TWO lines, blanks out, and stays that way.  I am very frustrated. I ran fdisk -l and it shows all of my partitions as normal. I tried grub-update and it acts like it isn't finding any operating systems. I don't understand.

---

### Post by sandyd on 2013-03-10
Moved to absolute beginner section.

Can you run the following on a livecd and post the output/files it generates (should be called output.txt)
```
wget http://superb-dca3.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.61/bootinfoscript-061.tar.gz
tar xvfz bootinfoscript-061.tar.gz
sudo ./bootinfoscript output.txt
```

Also, please see [https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2) for a guide in reinstalling grub

---

### Post by ShadowByte on 2013-03-11
I feel like a total idiot.

All I had to do was boot from an Ubuntu live USB that was the same version as my dual-booted Ubuntu install (12.04). I then ran the same commands I tried in BackTrack and it worked. Looks like there IS a difference between the two, as far as the source of config files, and I didn't notice. For some reason, I kept feeling like I've done it from BT before. Oh well, guess not.

I re-installed GRUB2 from there, rebooted, and it worked perfectly.

In case anyone is wondering, here's the link: [http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)


Oh, and thanks sandyd. I was going to address your request but my curiosity got the better of me. At least that led me to fixing it.

Moral of the story: Don't overlook things. The solution might be simpler than you think. :P

---


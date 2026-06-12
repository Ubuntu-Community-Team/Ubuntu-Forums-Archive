---
title: "Black screen during installation with Radeon HD6450"
date: 2013-09-13
forum: New to Ubuntu
---

### Post by lynx2 on 2013-09-13
I am suffering the black screen phenomenon which seems to be common with modern Radeon HD chips.
The problem is that this is at system install time, so I do not have the option of installing other drivers at this point.

This is a system I'm currently using as a HTPC, but I'm tearing my hair out with WMC and would prefer a Linux solution.
Please note from the hardware that there is no option of changing the graphics chip.

Hardware:
Lenovo Q180 (Intel atom D2700, Radeon HD6450A)
4GB DDR3
Hitachi 120GB HDD

I see the usual three options, Try Ubuntu, Install Ubuntu, Check disk.
After selecting any of these, the screen turns black and that's the end of everything.

At first I thought the problem was related to the USB key I was installing from, so I tried other media.
On about the fourth attempt I got the advances options screen.

I selected Try Ubuntu and everything seemed to work well, so assuming that I had now found working media I proceeded to reboot so that I could follow the Install path.
I got the usual three options again, and once again after selecting any option the screen turned black. Unfortunately, I do not seem to be able to force the system into the  advanced options screen, and the small icon indicating when I should  press a key never appears. Getting there the first time must have been  pure chance.

I have noticed that sometimes, after selecting one of the options, the fan speed increases indicating that the processor is doing something. I suspect that the actual problem is that I'm being asked a question, but that it is in black text on a black background. When I had the advanced options screen, I was able to respond to the questions because the background and text were no longer the same colour.

Can anyone give me a clue on how to
 force the advanced options screen
or
 change the colours so that it is not black on black.

Assuming I need to do something in grub, I know HOW to edit grub.cfg files (or any others for that matter), I'm just not sure what I should put in there.

---

### Post by Jonathan Precise on 2013-09-13
Try to add nomodeset or xforcevesa. Do you have UEFI? If you don't, then please download the ISO again without using bit-torrent (I have had issues with these before).

---

### Post by su:bhatta on 2013-09-13
Follow the instructions in this link and try: [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076#162076](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076#162076)

Then see if it works....
Best of Luck.

---

### Post by ajgreeny on 2013-09-13
> **Jonathan Precise said:**
> Try to add nomodeset or xforcevesa. Do you have UEFI? If you don't, then please download the ISO again without using bit-torrent (I have had issues with these before).
Before you bother to download again, check the current .iso file against the md5sums published at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Personally I would always suggest using a torrent client as it checks the file being downloaded at that time, and if any packet is faulty, it will discard it and get it again.  That, along with potentially increased speed, is the whole point of using torrents.

The nomodeset suggestion is spot-on, however.  Hit F6 after starting the live system, but before it moves from the first screen, to see the boot options.

---

### Post by lynx2 on 2013-09-13
Thanks for those replies, particularly the link from [**[COLOR=#000000]bhattabhishek[/COLOR]**]("http://ubuntuforums.org/member.php?u=1819052")
I knew the iso was ok since it had previously worked, and I had already tried nomodeset.
It seems the problem is UEFI related, I did not realise the screens displayed are different when using UEFI.

I don't remember doing it, but I must have selected the F12 boot menu and chosen Legacy mode on the one occasion I got it to work.
Or perhaps I was just so frustrated I was hitting Function keys at random to see if I could get one to work.

I've chosen that option again (it doesn't appear in BIOS) and my installation is proceeding.
I don't yet understand why it doesn't install in UEFI mode, but for the moment I don't care either, I'll look at that another time.

---

### Post by su:bhatta on 2013-09-14
Glad to be of help & that you got it working! 

Welcome to the world of "Linux for Humans"
Enjoy!

---


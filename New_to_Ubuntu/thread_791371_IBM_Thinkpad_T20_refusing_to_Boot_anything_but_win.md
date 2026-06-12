---
title: "IBM Thinkpad T20 refusing to Boot anything but windows"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Eddie.bear on 2008-05-12
Ok first my sob story. If you don't really care, my actual problem starts at *Problem starts here*. If you really *really* don't care try *bottom line*.

So I recently came into possetion of a (very) old second (or possibly third) hand reconditioned IBM thinkpad T20. (Well, I say old. It's actually 7 years old which I suppose is only a third of my age and I certainly don't tend to think of myself as old. Though I suppose for a computer it's positively methuselan. But I digress...) This is all very well and good except that it has Windows ME installed. Now, naturally, as a cogent human being I find this situation, erm, less than optimal and would *really* like to get rid of it. My preffered option to replace it would be some form of linux, just for the change really having used Windows for all of my comuting life so far. So given this I happily went along and looked at some distros and decided that Xubuntu looked promissing for such an old PC and downloaded and burnt the ISO without too much bother (Hardy Heron 8.04 if you must know). Now my problem is this:

*problem starts here*
When I insert the CD and reboot anything spectacular conspicuously fails to happen, Windows boots as if nothing had happened and I'm left with a joke of an OS. So I tried selecting a tempory boot device to be the CD drive (which shows top of the list so I rather suspect it sould really work without me doing this). Same result. So I tried running the CD from within windows and using Wubi, which gets as far as calculating checksums and then tells me it can't find the CD (despite it having been run from it. So having a poke around in obscure corners of the web I read that Wubi doesn't support ME and so I probably shouldn't have been too suprised. I then tried the option to have the CD "help me to reboot" or some such which, if I understand it correctly, installed grub which should then have given me the option to boot from the CD. The problem is when I reboot nothing happens, I just get dumped straight into windows. I should also probably have mentioned by now that I tried all this on my desktop (running XP I'm afraid) and it works like a charm so I can't see it being a problem with the CD. I also had a go with puppy linux with exactly the same result.

*bottom line*
I can't seem get anything but Windows ME to boot which rather prevents me from installing *any* other OS. Does anybody have the foggiest clue whether there is anything I can do now or am i **shudder** stuck with ME for the forseeable future.

It would really help me if you assume I'm a complete jackass with computers (not really far from the truth) and I certainly have absolutely nill experience with linux up to now.

Thank you all loads in advance

---

### Post by spiderbatdad on 2008-05-12
So after reading your post twice, my question is: when you load the "live cd" are you presented with menu that offers to boot/install Xubuntu?

Let's assume you are. Press the F6 key while at this menu. A line of text will appear below the menu. Use the right arrow key to move to the end of the line, then backspace to delete --quiet splash. Replace --quiet splash with lapic pci=routeirq and boot. If this fail to boot the OS, try again; this time replacing --quiet splash with noapic nolapic vga=791

You can read more about these boot parameters, I believe, by pressing F1 and then F6 after pressing F6 the initial time. If you find some combination of parameters that work for you, once the system has been installed (from the desktop 'install' option, after boot) you will need to edit a file called /boot/grub/menu.lst on the line beginning with the word kernel, to make the same change permanent.

---

### Post by Eddie.bear on 2008-05-12
> **spiderbatdad said:**
> So after reading your post twice, my question is: when you load the "live cd" are you presented with menu that offers to boot/install Xubuntu?

No I'm not. That is, in fact, the nub of my problem. Sorry for not making that very clear.

[EDIT]Ah, sorry, wait. On second reading of *your* post I must ask: are you refering to when I load it within windows or when I try to boot?

Assuming you are reffering to within windows the answer is actually yes and I'll give that a try, thanks. Otherwise see above.

I apologise for being thick and not understanding you.

---

### Post by spiderbatdad on 2008-05-12
Hmmm. sorry for not understanding. You say, "I then tried the option to have the CD "help me to reboot" or some such which, if I understand it correctly, installed grub which should then have given me the option to boot from the CD."

I'm not sure what that means. Is that something from the wubi installer?

Can you try pressing F12 as the machine powers on to select CD as the boot device?

---

### Post by Eddie.bear on 2008-05-12
Sorry what I meant was this:

1) I load windows as normal
2) I "autorun" the live CD
3) I select the run demo\install option
4) I select the help me boot from CD option
5) I then get a wubuildr (I think, something like that anyway) file and a menu.lst file on my C: drive
6) I then reboot and ... nothing, it just loads windows like i'd done nothing

---

### Post by spiderbatdad on 2008-05-12
I'm afraid, and slightly embarrassed, to admit I have not seen the 8.04 live cd release, as I installed it in Alpha stage and upgraded. So I'm not at all familiar with wubi.

My best advice, given the age of your machine, is to download the iso, and burn the image, of an older release, preferably 7.10. It is unlikely the latest kernel, used by 8.04, is going to offer much support for the hardware on that computer. I have a T-30, and the kernel has some hardware detection issues.

Get Xubuntu 7.10 here: [http://cdimage.ubuntu.com/xubuntu/releases/gutsy/release/](http://cdimage.ubuntu.com/xubuntu/releases/gutsy/release/)

You may find the alternate cd will work better, but is a text based installer.
I would try the desktop cd first.

---

### Post by Eddie.bear on 2008-05-12
OK I'll give it a go thanks for all your help

---

### Post by Separ on 2008-05-12
Is the BIOS on the computer set to boot from the CD drive before hard drives/floppy drives? If not, try hitting the "Delete" key multiple times just after you turn the computer on (it may be any one of the F keys also but it depends on your motherboard.)

Once in the BIOS, go to the BOOT section and use the + and - keys to change the order of the drives so that the CD drive comes first.

---

### Post by groupsuser on 2008-06-16
Eddie.Bear -- I just saw your thread. I had a similar problem and resolved it using the "alternate desktop CD" instead of the "Live CD".
Hope this helps...

---

### Post by Bradtek on 2008-06-16
Can you confirm whether you can enter the bios and 
enable the CD Rom drive as the first boot device ?
(not temporary boot)

a quick google wast all that helpful but it seems 
Holding the F1 key should get you there.

Upgrading the BIOS could possibly help (or not)

You said you couldn't boot puppy either but
Have you been able to boot from **any** other CD on this laptop ?
Try downloading some other bootable cd iso

---


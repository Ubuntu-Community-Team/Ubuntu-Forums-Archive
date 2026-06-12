---
title: "ubuntu desktop 11.10 &amp; nvidia geforce 8500gt"
date: 2012-02-22
forum: New to Ubuntu
---

### Post by aztoby on 2012-02-22
HARDWARE OVERVIEW:
Mobo: Gigabyte w/ on-board graphics (up to 256MB shared memory)
Proc: AMD Athlon 64 x2
Mem: 8GB DDR2
PCI-E: EV3A 1GB DDR2 NVIDIA e-GeForce 8500GT
Dual Display: Dell 17" (1280x1024) & Acer 22" (1600x1200)
Dual-boot: Win 7 Prof 64 / Ubuntu Desktop 64 11.10

DESIRED RESULT:
Dell 17" fed video by on-board graphics
Acer 22" fed video by PCI-E card

ISSUE:
- I cannot get video out from the PCI-E card, when booted into Ubuntu 11.10, and cannot take full advantage of graphic capabilities of displays when using only on-board controller for both displays.
- With only 256MB on-board graphics, virtual machines can only be allocated max of 128MB video memory, which means that their operating windows are almost ineffectually small.
- I am too much of a Newbie to attempt to add *.run or *.bin drivers via terminal (its not the "trying" that worries me...its the "fixing" if something goes wrong)
- I've only had 5 scattered months of employment since April of 2009, so buying hardware is not an option. I need to make the hardware I have work, if at all possible.

ATTEMPTS TO CORRECT:
- Using System Settings / Additional Drivers, went down the entire list, one-by-one, restarting and then testing after each = NO CHANGE
- Downloaded Linux 64-bit GeForce 8500GT-specific drivers from NVIDIA's website + UNABLE TO INSTALL AFTER DOWNLOADING
- Desired results above are automatically achieved when booted into  Windows 7 partition, so I know the graphics card and PCI-E slot are  functional

---

### Post by d4m1r on 2012-02-22
Only high end motherboards can run the onboard graphics card AND a dedicated graphics card. This option is usually set in the BIOS (PCI-E = the Nvidia).

You can choose to use one or the other, but not both.

---

### Post by aztoby on 2012-02-23
thanks for the reply, [d4m1r]("http://ubuntuforums.org/member.php?u=1456986"). 

apparently, my mobo  is high-end enough that i don't even have to manually choose... it automatically allows both onboard and pci to work simultaneously. however, bios does have an option to switch between the two as a choice of which one is initialized first. 

As it happens, i tried changing the 1st-init from onboard to pci and suddenly Ubuntu was running on the pci. but then it wouldn't put out to the onboard. so i switched the bios back to 1st-init = onboard, and by fluke forgot to disconnect the 22" display from the pci card and badabing-bam-boom, both video outputs are now working exactly as I'd originally hoped they would.

I'm guessing that I probably would have had no problem at all if the pci had been in the box when I did the initial Ubuntu install.but somehow switching the bios settings back and forth "woke up" something in Ubuntu so that it now sees the card.

just one of life's little head-scratching scenarios, but as long as it works, i don't care. ;)

---

### Post by aztoby on 2012-02-24
okay. i am hereby re-opening this case. there is something definitely amiss with my ubuntu install.

today, i can only get ubuntu to send video through the pci card if i have "init pci 1st" enabled in bios. but then it sends video ONLY through the pci card.

please don't anyone try telling me though, that i am strictly limited to an "either-or" scenario, because all day yesterday ubuntu sent digital video from the onboard to the dell 17" while simultaneously feeding video to the acer 22" via pci digital. (i'm sorry, d4m1r. no offense is intended) 

also, windows 7 has absolutely no issues whatsoever auto detecting and using both video sources simultaneously... so i know its not a hardware issue. I may still only be a beginner with linux, and a total newb with ubuntu, but with 20 years tech experience behind me i do know how to troubleshoot.

what i need to know is...
1. do i need to do a clean reinstall of ubuntu, with the pci card installed from the get-go?
2. if not, is there someone who can walk me through baby-steps of using the command line to try to fix this issue?

---

### Post by grahammechanical on 2012-02-24
Does this motherboard have what is called Optimus technology? 

[http://www.omgubuntu.co.uk/2011/05/bumbleebee-brings-nvidia-optimus-gpu-switching-to-linux-users/]("http://www.omgubuntu.co.uk/2011/05/bumbleebee-brings-nvidia-optimus-gpu-switching-to-linux-users/")

Optimus is a big issue for Linux.

And Yes it would have been better if the Nvidia 8500GT had been in place when Ubuntu was installed as the installation process detects the hardware. But it should not be a big issue because you would still have needed to activate (install) the proprietary drivers after wards.

Regards.

---

### Post by aztoby on 2012-02-24
hey [grahammechanical]("http://ubuntuforums.org/member.php?u=1087323"),

thanks for responding. no. my motherboard is a Gigabyte brand micro-atx desktop model. its maybe 2 or 3 years old. I am really suspecting that I am going to need to do a new OS install, but I'm holding off for a little bit in case I get a response that can save me that trouble. What I am hoping for, is that some sympathetic and patient command line guru will rescue me by giving me a set of instructions to fix something in some configuration file.

---

### Post by gordintoronto on 2012-02-24
Why don't you connect both monitors to the 8500gt?

---

### Post by aztoby on 2012-02-24
that's a good question, gord. i could do that. but at this point its become a matter of principle. if there's no good reason that something that should work but doesn't, then the don quixote just can't resist the urge to charge the windmill.  lol 

then there's always the possibility that solving this conundrum may present an opportunity to learn some practical command line tool(s)

and finally, there's a minor annoyance in that the system to defaults to the dvi port as the primary and the vga as secondary... which doesn't mesh smoothly with my desire to have the smaller display on my left and the larger on m,y right

but as i say... that's just a minor annoyance that i can workaround via display settings.the main reason is that if something is supposed to work, i'm just anal retentive and ocd enough to let it bug the sh*t out of me when it doesn't. lol

---


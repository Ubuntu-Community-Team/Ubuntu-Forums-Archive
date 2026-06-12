---
title: "No video out when booting from disc."
date: 2012-02-20
forum: New to Ubuntu
---

### Post by Dave Daytona on 2012-02-20
Hi, I'm a total newbie with Ubuntu, installed Windows numberous times over the years, but this O/S is utterly new to me. 
I am trying to install Ubuntu 11.10 32-bit, I have checked the ISO with winMD5sum to assure that the download was OK. I have burned the image to disc and can see the files in Windows XP's Explorer. I boot up the PC with the disc in the CD-Rom drive, the BIOS is set for CD first boot. The PC starts up, I get an icon at the bottom of the screen (looks like a keyboard, a = and a figure?), then the screens switches off and goes into sleepmode. The CD continues to spin, the light flashes and it appears to be continuing to load for maybe a further 30 seconds. I presume it has then reached the point where it is waiting for me to input a command, but of course I can't do that as the screen is blank. :(  Help!:)


]Copied from Belarc Advisor:
*MotherBoard: Gigabyte GA-A75M-D2H*[I] - Bus Clock: 100 megahertz
3.00 gigahertz AMD A8-3870 APU with Radeon HD Graphics
256 kilobyte primary memory cache
1024 kilobyte tertiary memory cache
64-bit ready
Multi-core (4 total)
Not hyper-threaded[/i]
[*AMD Radeon HD 6550D [Display adapter]* [COLOR=Blue](Onboard graphics, no separate card)[/COLOR]
I'm using the motherboard's VGA output rather than the DVI one.

---

### Post by cariboo on 2012-02-22
When you see the initial boot screen, press any key to see the menu, select your language, then press F5 and select nomodeset from the menu. Press esc then press Enter to continue booting.

---

### Post by Dave Daytona on 2012-02-22
Hi, thanks for the reply. After some head scratching yesterday I added a spare PCi graphics card I had here and that at least that brought me up a screen which stayed on after BIOS and during Ubuntu's installing. I think the problem *may* lay with no proper video driver installing after BIOS??

The PCi graphics card (Radeon 9250) I installed is letting video play (but very jerkily) and also will only allow allow an identical image on each of my screens (1 x VGA, 1 x DVI ), rather than the 2 separate dual screens that I want. Ideally I would like to use the onboard graphics and not bother with a graphics card (it worked fine under WinXP so I assume it isn't a firmware issue), but I am struggling to find/install the drivers for the onboard graphics or for the graphics card. Am I wasting my time with my current card or onboard graphics in that a different 'Ubuntu friendly' card would be better option?

---

### Post by Dave Daytona on 2012-02-24
Bump.

I've been struggling without success for the last couple of days to fix the graphics problem I'm having, after trying to install drivers for the PCi card I just can't get it to work. Are their any working drivers for Ubuntu 11.10 using a Radeon 9250 card, if so please point me to them (with instructions please:D) I've searched numerous forum posts and don't have a clear answer.

If none are available could someone suggest a graphics card that has good support from Ubuntu, the best available slot is PCI Express x16 on the M/B. My requirements are one VGA and one DVI port, one screen is used for video the other for browsing etc, no games are used. Thanks for any help.:)

---

### Post by mcduck on 2012-02-24
> **Dave Daytona said:**
> Bump.

I've been struggling without success for the last couple of days to fix the graphics problem I'm having, after trying to install drivers for the PCi card I just can't get it to work. Are their any working drivers for Ubuntu 11.10 using a Radeon 9250 card, if so please point me to them (with instructions please:D) I've searched numerous forum posts and don't have a clear answer.

If none are available could someone suggest a graphics card that has good support from Ubuntu, the best available slot is PCI Express x16 on the M/B. My requirements are one VGA and one DVI port, one screen is used for video the other for browsing etc, no games are used. Thanks for any help.:)
There isn't any great drivers for the old graphics card, as Ati/AMD dropped support for legacy cards in their drivers years ago.

You'll most likely get better results using the integrated graphics card, as that *is* well supported by the latest drivers. So I suggest removing the old card and following cariboo907's advice about using the "nomodeset" option to get the system installed. After you get to the desktop you should be able to install the proprietary drivers for your graphics card.

---

### Post by Dave Daytona on 2012-02-24
> **cariboo907 said:**
> When you see the initial boot screen, press any key to see the menu, select your language, then press F5 and select nomodeset from the menu. Press esc then press Enter to continue booting.
Thanks mcduck. This afternoon I followed your and cariboo907's advice and on a freshly formatted h/drive reinstalled a fresh copy of 11.10 using the **nomodeset** command. I removed the graphics card and put the VGA & DVI cable back into the mother board. Unfortunately half way through the Ubuntu install the VGA signal cut out, the DVI stayed on, but after reboot neither worked once Ubuntu started loading.:(

I put the old ATi 9250 graphics card back in and both screens are back on again.

The processor is an APU model (* AMD A8-3870 APU with Radeon HD Graphics*) could that be the problem? Graphics on processor?

Would fitting a popular modern graphics card pick up the drivers automatically in 11.10 or would it still need installing manually?

---

### Post by mcduck on 2012-02-24
The APU should work just fine in Linux, as soon as you get the system and AMD's proprietary drivers installed. (The open-source driver doesn't fully support the APU yet).

...and those AMD driver's can't be installed by default since they are proprietary, not free software. So one you find a way to get to desktop using the APU as your graphics card, you should be prompted if you wish to install the proprietary drivers. This works the same way regardless of how old or new graphics card you have, the proprietary drivers are never installed automatically during Ubuntu install.

Anyway, you need to use the "nomodeset" option *when installing with the APU as your graphics card*. So remove the old card first, then boot the install CD, add "nomodeset" to kernel options, continue the boot and the installer should work fine. After the install you'll need to add "nomodeset" again (since adding it at boot time will not make it permanent option) to get to the desktop of your newly installed system, and then you can install the proprietary drivers.

---

### Post by Dave Daytona on 2012-02-25
Hi Mcduck, thanks again for your time. :-)

To ensure there were are no installation mistakes I reformatted the H/D and reinstalled 11.10 as you described (no graphics card in the PC). The install went OK up until it has finished and updated, it went requests a reboot and removing the CD. I then rebooted and once again the graphics to both the VGA & DVI cut out about 20 seconds after BIOS screen has finished and the Ubuntu mouve screen has appeared. So I'm not certain at what point the second time **nomodeset** is applied? If you mean at sometime once Unbuntu has loaded I never get that far before the signal is cut.:| As for loading any other drivers, again I can't do that whilst using the onboard graphics as it never reaches fully being fully booted up before the screen goes black. Incidentally, Ubuntu seems to be continuing to load normally in the background although the signal to the monitors is cut, you can hear the H/D working as normal and shortly on you hear the start up music play.

---

### Post by mcduck on 2012-02-25
> **Dave Daytona said:**
> Hi Mcduck, thanks again for your time. :-)

To ensure there were are no installation mistakes I reformatted the H/D and reinstalled 11.10 as you described (no graphics card in the PC). The install went OK up until it has finished and updated, it went requests a reboot and removing the CD. I then rebooted and once again the graphics to both the VGA & DVI cut out about 20 seconds after BIOS screen has finished and the Ubuntu mouve screen has appeared. So I'm not certain at what point the second time **nomodeset** is applied? If you mean at sometime once Unbuntu has loaded I never get that far before the signal is cut.:| As for loading any other drivers, again I can't do that whilst using the onboard graphics as it never reaches fully being fully booted up before the screen goes black. Incidentally, Ubuntu seems to be continuing to load normally in the background although the signal to the monitors is cut, you can hear the H/D working as normal and shortly on you hear the start up music play.
You need to add it to kernel options before starting Ubuntu, from the boot loader's menu screen. (If Ubuntu is the only OS on the computer, you may need to hold down Shift while starting the computer to get to the Grub menu).

...and adding the option this way only affects that time, so it's not a permanent change. If you need to add the option permanently you can do that by editing /etc/default/grub once you've successfully booted to the desktop.

---

### Post by Dave Daytona on 2012-02-26
Thanks again.:)

I boot the PC and hold the shift key, the Grub screen loads, at the prompt I type **nomodeset **it then states 'Error no command exists' (or in very similar words). I then press the Tab key to list all the available commands (about a 100 of them I guess) and **nomodeset** is not among them.:confused: 
So I am left with no option other that to continue to boot normally which then turned the screen off 30 seconds later, Ubuntu again sounds like it loaded OK in the background and the start up sound played, at this point there is obviously nothing I can do.

What are the options now?

---

### Post by mcduck on 2012-02-26
You are not supposed to go to Grub command prompt, the "nomodeset" is *added to the kernel options*. So highlight the boot entry you'd like to use, press "e" to edit it, use arrow keys to move to the end of the kernel line (the one starting with "linux /boot/vmlinuz...") and after the existing options ("ro quiet splash") add the "nomodeset". Then hit Ctrl-x to boot.

---

### Post by Dave Daytona on 2012-02-28
Hi Mcduck, sorry for a late reply, I can't tell you how many hours I've spent trying to solve this problem. 
I have tried the **nomodeset** after **quiet splash **asyou suggest but sadly it only part solves the problem of the screen**.** I can get it to boot into 11.10, but the 2 screens are just mirrored, any alteration brings up an error dialogue box (sorry I haven't included it here) or a total lock up requiring a reboot. I also tried the advice offered by another user (shown below), it gave me the drivers and installed them which I hadn't got previously, but the screens would still only mirror and not give an extended desktop/workspace which is what I require.

"*Try booting into your installed system with the nomodeset option editing  the GRUB entry by pressing "e" when selecting Ubuntu 11.10. After  "quiet splash" and before the next thing to it, enter nomodeset.  That will "boot" you into ubuntu, but will actually freeze at the  splash. Press Ctrl + Alt + F1 to drop into a console. Login with your username and your password, and when you're in, type  "sudo apt-get install fglrx". These are the proprietary drivers for ATI  cards  Enter your password and install as required. Reboot and Voilá ... *"


After reading numberous over threads about ATI driver problems I bought a Nvidia GT520 to see if that installs with less problems, sadly not. Here is a link to see what you think if you can spare the time. Regards, David.   [http://ubuntuforums.org/showthread.php?p=11725457#post11725457](http://ubuntuforums.org/showthread.php?p=11725457#post11725457)

---


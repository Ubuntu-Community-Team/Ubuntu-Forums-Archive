---
title: "[SOLVED] Need help with DSL for Flash Drive!"
date: 2008-02-20
forum: Other OS Talk
---

### Post by TheThinker on 2008-02-20
I'm having issues trying to install DSL onto a flash drive from within the Live-CD function. Apparently, the USB HDD install method doesn't work; the terminal closes after everything done, yet I have no way of knowing if it actually did anything! The installation prompts were confusing, so I just went ahead and pressed enter through both of them (before it asks if I want to continue "Last Chance"). Did I screw up here?

 My computer does support USB boots, yet my 128mb flashdrive still doesn't boot the system. In Ubuntu, the flashdrive is read as having 122 of free memory, with no used memory. It looks like the partitioning worked.

Any help would be appreciated. The DSL wiki is not very informative, in my  opinion, about how to use the Live CD tools to create a bootable flashdrive.

---

### Post by smartboyathome on 2008-02-20
I think you want to use the LiveUSB function if there is one rather than USB HDD. Also, I am guessing it didn't install correctly cause it should be at least 50MBs on your USB drive.

---

### Post by TheThinker on 2008-02-21
You're right; the drive should have had at least 50 mb used. Well, I think I was using the latest version of DSL, but I guess I'll to download a different one. I forgot which version number it was.

Now, I'm using Puppy (SeaMonkey), which seems to have a much easier-to-use Flash Drive Installation. Granted, it does take up 100mb on my pendrive but at least it has a more user-friendly interface. 

The good news is that Puppy did successfully partition the drive for sure. Approximately 100mb are used up, and it seems all the necessary files are there (with 20mb to spare). Even better, my system BIOS successfully detected the flashdrive as my LEXMARK JUMPDRIVE (instead of Generic USB SDE). During bootup, the computer attempts to read the drive because I can see its light blink. 

The bad news is that despite being detected, the system still won't boot from it; it just quits after 5 seconds of reading and boots from my hard-drive instead. I tried formatting the pen drive with every FAT file system, from FAT all the way to FAT32. I tried all but one MBR method in the Puppy installation; still no luck (and I somehow doubt the last method will work too). My system BIOS does support booting from USBs, and I even set the priority to USB SDE as #1 on the boot list. (sigh). Also, I don't think the flashdrive itself is to blame; it's VERY reliable.

I'm beginning to suspect that my computer itself is buggy, or that I goofed up on the installation. Is there a particular way to install to a flashdrive that is sure to work, or are these installations just unreliable in general? I would really like to get Puppy or DSL to boot without needing a CD, yet at this point I'm about to give up. With so much work involved, perhaps using a CD and saving the settings to a flashdrive is an easier approach.

---

### Post by TheThinker on 2008-02-21
By the way, my computer is an E-Machine. I don't know if that helps. Perhaps Emachines are picky about booting from pendrives?

---

### Post by TheThinker on 2008-02-21
Oh, and YES, I did remember to use Gparted to set the boot flags.

---

### Post by Bungo Pony on 2008-02-21
I never actually boot into DSL to install it to a flash drive. When you boot off the live CD, you'll get a big splash screen with the Penguin and a prompt underneath. At the prompt, type 'install'. DSL will then configure some of your hardware, then it will go to an all-text menu. Pick "install to USB HDD" and you'll see everything that's happening, without the problem of the terminal closing.

---

### Post by smartboyathome on 2008-02-21
> **TheThinker said:**
> By the way, my computer is an E-Machine. I don't know if that helps. Perhaps Emachines are picky about booting from pendrives?

I have an E-Machine. Sometimes it detects the USB drives as hard drives, so you might have to press F10 while it is booting up to get to a boot device prompt in order to boot it.

---

### Post by TheThinker on 2008-02-21
> **Bungo Pony said:**
> I never actually boot into DSL to install it to a flash drive. When you boot off the live CD, you'll get a big splash screen with the Penguin and a prompt underneath. At the prompt, type 'install'. DSL will then configure some of your hardware, then it will go to an all-text menu. Pick "install to USB HDD" and you'll see everything that's happening, without the problem of the terminal closing.

Thanks Bungo Pony. I appreciate the help. One problem though; I've read the wiki tutorial that USB HDD can be used to install to pendrives, but doesn't USB HDD refer to USB hard-drives and not flash-drives like I'm talking about? Strangely, the USB HDD install option is the only USB install option available in the version I have.

---

### Post by TheThinker on 2008-02-21
> **smartboyathome said:**
> I have an E-Machine. Sometimes it detects the USB drives as hard drives, so you might have to press F10 while it is booting up to get to a boot device prompt in order to boot it.

I already did that before. It detects my USB SDE port as LEXAR JUMPDRIVE in the boot device prompt. I select it, press enter, and the same problem occurs. The USB's light flashes for 5 seconds, then it seems to give up and boot into Ubuntu instead (from my internal hard-drive). That's with Puppy, by the way.

---

### Post by smartboyathome on 2008-02-21
> **TheThinker said:**
> I already did that before. It detects my USB SDE port as LEXAR JUMPDRIVE in the boot device prompt. I select it, press enter, and the same problem occurs. The USB's light flashes for 5 seconds, then it seems to give up and boot into Ubuntu instead (from my internal hard-drive). That's with Puppy, by the way.

Sounds like somehow it is redirecting your machine to boot from the first hard disk instead of from the USB drive.

---

### Post by TheThinker on 2008-02-22
I found the problem. It's my E-Machine. As you've pointed out smartboy, my BIOS were detecting it as a hard-drive (yet with puppy, it also detects it as a USB drive). I tested the FlashPuppy install on my brother's ACER computer, and it worked! Sadly, the DSL I have fails utterly despite the new instructions by Bungo. In fact, it created two partitians on the flash, which ended up having Gutsy see it as two seperate drives mounted in the same port. I guess DSL is out for now.

---


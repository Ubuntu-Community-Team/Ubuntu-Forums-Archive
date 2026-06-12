---
title: "Bios Bug 8254 timer not connected to IO_APIC"
date: 2015-04-27
forum: New to Ubuntu
---

### Post by mrag on 2015-04-27
My pre apologies on this, there are numerous and much older threads that I haven't been able to comprehend for a newbie. I have an 2008 2GB Dell desktop that has been and is quite fine running XP. On trying Ubuntu (off CD, USB, bare HD) I am getting a message about the Bios 8254 Bug that is well described [here]("http://www.linuxquestions.org/questions/linux-hardware-18/mp-bios-bug-8254-timer-not-connected-use-noapic-option-to-boot-591891/"). As explained therein, basically designers made allowances for Windows so it "works," but screwed everyone else. Even if some update is available, I do not want to attempt flashing the BIOS. I first tried a live USB LinuxMint which worked fine on two different laptops. It wouldn't on the Dell desktop. I then went back to Ubuntu 14.04 and saw the APIC issue. I can boot the Dell from a USB although nothing really works. I have no clue what they mean by using F6 or F4, etc. or where I would do what is suggested. Now I have looked at the GRUB cfg file on the USB (hopefully attached) and it seems it already has noapic noacpi. Should I edit that more, do something else?

Now what, stick with XP :p

---


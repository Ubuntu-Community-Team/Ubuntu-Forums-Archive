---
title: "Installing 12.04 on UEFI system"
date: 2014-02-15
forum: New to Ubuntu
---

### Post by LinuxVirgin2000 on 2014-02-15
Im tring to get ubuntu 12.04lts on my ultrabook, i understand there are certain things that need to be disabled as this link says:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

in step 2 it says:
"[COLOR=#333333][FONT=Ubuntu]In your BIOS, [/FONT][/COLOR][disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9")[COLOR=#333333][FONT=Ubuntu] and [/FONT][/COLOR][Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6")[COLOR=#333333][FONT=Ubuntu](SRT). If you have Windows8, also [/FONT][/COLOR][disable FastStartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html")"

I have managed to disable fast start up in the "power options" menu in the control panel
I had a look through the BIOS settings by pressing F12 while PC is booting but I can not see any option to disable quickboot/fastboot in fact the words are not even mentioned
same goes for Intel Smart response technology, I googled how to turn this off and it seems peope are doing it through some intel rapid storage technology control panel but I dont seem to be able to find it in windows. It's frustrating because I can see intel rapid storage technology in the "add or remove programs" but when i search for the software on my computer there is notheing.

Could someone please help me to turn off the [QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and the [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6")[COLOR=#333333][FONT=Ubuntu](SRT) so I can get on with installing ubuntu.

Thanks in advance.

[/FONT][/COLOR]

---

### Post by Psil0cybin on 2014-02-15
Perhaps you can post some images of your bios, directly? What I am getting at, is from my personal experience, you have to look at every single option in your bios...worst case you can always reset, your settings back to default, but playing around always helps plus you will learn something.

If you can provide images, I can attempt to guide you although every Bios is set up differently.

---

### Post by oldfred on 2014-02-15
Post this, if you have a small sdb, and it probably will show unknown as Intel SRT uses RAID and desktop does not include the RAID drivers.

sudo parted -l

  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)

What brand & model system?
See also link in my signature for more info on Ultrabooks in general.

---

### Post by LinuxVirgin2000 on 2014-02-16
Hi, Thanks for the quick response,

I have take a picture of all of the tabs in the bios menu I hope that helps?

apologies for the quality, my cameras not great.

---

### Post by fantab on 2014-02-16
You have [Intel Rapid Start Technology]("http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology"), see your 4th Screenshot. 
More info:
[http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf](http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf)

You don't seem to have 'fastboot' I guess but your have Intel RST which similar to Intel Smart Responce Tech.

---


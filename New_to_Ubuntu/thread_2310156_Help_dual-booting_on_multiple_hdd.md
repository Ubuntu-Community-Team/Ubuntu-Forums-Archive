---
title: "Help dual-booting on multiple hdd"
date: 2016-01-16
forum: New to Ubuntu
---

### Post by gbruer on 2016-01-16
Hello, 

I'm having some difficulty dual-booting [COLOR=#ff0000][/COLOR][COLOR=#a9a9a9](skip to edit #2 for current the problem)[/COLOR][COLOR=#ffa500][/COLOR]
I have three drives, one is a 120GB SSD with ubuntu installed, one is a 1TB HDD for mass storage, and just recently I have attached my old macbook pro hdd via usb3 from an external hard drive enclosure. I am trying to set things up so that I can dual boot with my old mac's hdd on occasion (to access iTunes and OSX only programs) but would like to keep Ubuntu as my main OS. I can look at the files on my mac's old hard drive but can't figure out how to boot from it without changing the boot priorities in the BIOS. I would like to be able to choose which disk I want to boot from on start-up, much as I used to be able to do when holding down the option key during startup on the old mac. Is there any way I can do this? My apologies if I haven't provided the right details, let me know what include and I'll add it right away. Thanks,

**edit:** although I've been having trouble researching this on my own (all my search results seem to end up being guides on how to add ubuntu dual-booting to a windows machine) I have found a few posts that seem to suggest I should in fact be seeing a grub menu during start-up. I have installed Grub Customizer and it seems to recognize OSX as a boot option, but I still do not have that option on start-up.

**edit #2:** I tried using Grub Customizer to customize the appearance of the Grub screen and now the screen does in fact appear. This is fantastic! However I still can't actually boot OSX because I'm receiving an error. When I select OSX 64-bit to boot it returns with "error:hibernation header has incorrect magic number. Press any key to continue". This is troublesome both because I have no clue what a magic number is (let alone a hibernation header) and pressing any key does not actually continue but freezes up the computer (or at least does nothing) so that I have to reboot by holding down the power button (not ideal).

**edit #3:** Hmm, I'm reading up on bootloaders now. Apparently OSX is picky about its bootloader and something about EFI. I don't actually understand what EFI is yet, but it seems to be important. I'm reading some things that seem to suggest I should replace Grub with rEFInd or Chameleon. That seems like something that could really blow up in my face though. Some sources are suggest that Grub2 is simply incapable of launching OSX while others purport that it is.

---

### Post by sandyd on 2016-01-16
Hi,
 We do not support circumventing EULA on the forums, your thread has been closed.
Please see the Ubuntu Forums Code of Conduct at [http://ubuntuforums.org/misc.php?do=showrules](http://ubuntuforums.org/misc.php?do=showrules)

---


---
title: "Reality check: dealing with fresh install and UEFI"
date: 2014-12-29
forum: New to Ubuntu
---

### Post by salsify2 on 2014-12-29
This is kind of backwards from the usual question, in that I don't have a problem...yet. But I don't want to have one because I'm just a simple user and while I can follow clear directions scrupulously, I don't really understand very much of the detail once you get to the terminal. 

So here's the issue. My old desktop, happily running Xubuntu 14.04, is showing its hardware age: lost half my RAM and now one of my hard drives (the one I keep files on) is locking the files intermittantly, which I'm given to understand doesn't bode well for its lifespan (yes, safely backed up now). So it seemed reasonable to shop for a new box and I found a LenovoH50 that seems reasonable: [http://shop.lenovo.com/us/en/desktops/lenovo/h-series/h50-intel/?sb=:000001C9:00012D33:#tab-customize](http://shop.lenovo.com/us/en/desktops/lenovo/h-series/h50-intel/?sb=:000001C9:00012D33:#tab-customize). 


But in reading around to check on potential problems, I see that there's a huge amount of discussion devoted to problems installing the various versions on boxes with UEFI, including with Lenovos. I've read UEFI Installing - Tips  [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295) and [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) seems useful but I'm not sure how updated it is. And of course I realize that internet discussion always biases toward the negative because it is, after all, seeking solutions to problems that brings people to forums. 


Finally, the question: is it realistic to order this box and hope that if I follow the directions cited, I can wipe Windows entirely and have a Xubuntu install? I don't want to ruin the Windows and end up with a box I cannot return because I've broken it and can't use it because Xubuntu won't install and I can't understand all of the complicated instructions on partitions and...things. So does anyone successfully install, *not* to dual-boot, on UEFI boxes? Or is Windows too locked in now and I should just run my old hardware until it dies and then give up on Linux (please don't tell me this: ever since I left XP behind I've been *so* much happier)?

---

### Post by sandyd on 2014-12-29
> **salsify2 said:**
> This is kind of backwards from the usual question, in that I don't have a problem...yet. But I don't want to have one because I'm just a simple user and while I can follow clear directions scrupulously, I don't really understand very much of the detail once you get to the terminal. 

So here's the issue. My old desktop, happily running Xubuntu 14.04, is showing its hardware age: lost half my RAM and now one of my hard drives (the one I keep files on) is locking the files intermittantly, which I'm given to understand doesn't bode well for its lifespan (yes, safely backed up now). So it seemed reasonable to shop for a new box and I found a LenovoH50 that seems reasonable: [http://shop.lenovo.com/us/en/desktops/lenovo/h-series/h50-intel/?sb=:000001C9:00012D33:#tab-customize](http://shop.lenovo.com/us/en/desktops/lenovo/h-series/h50-intel/?sb=:000001C9:00012D33:#tab-customize). 


But in reading around to check on potential problems, I see that there's a huge amount of discussion devoted to problems installing the various versions on boxes with UEFI, including with Lenovos. I've read UEFI Installing - Tips  [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295) and [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) seems useful but I'm not sure how updated it is. And of course I realize that internet discussion always biases toward the negative because it is, after all, seeking solutions to problems that brings people to forums. 


Finally, the question: is it realistic to order this box and hope that if I follow the directions cited, I can wipe Windows entirely and have a Xubuntu install? I don't want to ruin the Windows and end up with a box I cannot return because I've broken it and can't use it because Xubuntu won't install and I can't understand all of the complicated instructions on partitions and...things. So does anyone successfully install, *not* to dual-boot, on UEFI boxes? Or is Windows too locked in now and I should just run my old hardware until it dies and then give up on Linux (please don't tell me this: ever since I left XP behind I've been *so* much happier)?
UEFI and secure boot should be working with recent versions of Ubuntu.
If UEFI does not work, and you want to just wipe Windows, you can simply turn off UEFI by setting the computer to boot in Bios/Legacy mode. Windows will _not_ boot in this mode (Unless both Windows and Ubuntu are installed in BIOS/Legacy mode).

---

### Post by Dennis N on 2014-12-29
> So does anyone successfully install, not to dual-boot, on UEFI boxes?

If you want Linux only (you do say "wipe Windows entirely and have a Xubuntu install") I suggest buying a system without preinstalled Windows -  get a barebones system with most components already assembled,  or else buy the needed components and assemble them. I've done both.

For barebones systems sellers, Google for "barebones kits", or "barebones mini computers" for something small. For example, I recently "assembled" a tiny Zotac ZBOX (build is hardly the right term - you only put in a HDD or SSD and a memory stick of your choice - it's easy) and it's completely compatable with Ubuntu. It's the second one of these I have done - one four years ago that is still going strong.

Worth considering.

---

### Post by salsify2 on 2014-12-29
Thank you Sandy and Dennis. 

Sandy, that sounds encouraging and makes me think I might be able to pull it off noncatastrophically.  

Dennis, I appreciate your thought and the advantages that whole approach would offer,  but my whole focus was on getting a new box in a simple manner, and learning enough to build my own doesn't quite fall within that realm.

---

### Post by salsify2 on 2014-12-29
Thinking further, Sandy, you say
> [COLOR=#000000]If UEFI does not work, and you want to just wipe Windows, you can simply turn off UEFI by setting the computer to boot in Bios/Legacy mode. [/COLOR]

That suggests that I try to install with UEFI on, which is the default I'd get that Lenovo in. And then somehow that fails (I'm not sure what a fail would leave me with). And from that failed point, I assume I've already nuked Windows and now I don't know how one would proceed to change that setting. Is that where the boot repair utilities come in? Or would there be something I would need to do *first*, before I try even a first install, to retain that option? In other words, I want to maximize my chances of being able to dig out of that hole, should it present.

---

### Post by sandyd on 2014-12-29
> **salsify2 said:**
> Thinking further, Sandy, you say


That suggests that I try to install with UEFI on, which is the default I'd get that Lenovo in. And then somehow that fails (I'm not sure what a fail would leave me with). And from that failed point, I assume I've already nuked Windows and now I don't know how one would proceed to change that setting. Is that where the boot repair utilities come in? Or would there be something I would need to do *first*, before I try even a first install, to retain that option? In other words, I want to maximize my chances of being able to dig out of that hole, should it present.

This can be done in the BIOS.

---

### Post by Jonathan Precise on 2014-12-29
[s]@Dennis N: +1

If you're going to end up wiping Windows in the first place, well why not get a barebones kit, where you can choose your own HDD/SSD + RAM, and not have to deal with Windows in the first place?

If you want something more portable, you can also get a barebones laptop. Here's a guide I found on wikiHow on how to assemble a one: [http://www.wikihow.com/Build-a-Laptop-Computer](http://www.wikihow.com/Build-a-Laptop-Computer)[/s]

EDIT: Sorry, took a while to post, should have refreshed.

---

### Post by salsify2 on 2014-12-29
> [COLOR=#000000][FONT=Ubuntubeta]This can be done in the BIOS.[/FONT][/COLOR]

Which should be available to me even from the ashes of whatever destruction a failed install with UEFI might cause?

---

### Post by Jonathan Precise on 2014-12-29
Yes, it should as the BIOS settings are not where Windows is.

---

### Post by oldfred on 2014-12-29
UEFI has some advantages with new hardware. But Since it has more features, it has more settings. With BIOS we often could install without any BIOS changes, or some had to make a few BIOS changes. Now with UEFI many settings may be required. And each vendor has implemented UEFI differently, so the required settings vary by vendor a lot and then even by model.

I just built new system with Asus-AR motherboard and had multiple settings to change to get it to install correctly in UEFI mode and that system had no Windows. It did want to default to BIOS mode until I got all settings correct.

Oldfreds extra info is still good. The only update that I should add is that Boot-Repair is rarely required now with UEFI systems. Grub2's os-prober finds Windows correctly if Ubuntu installed in UEFI mode. All the links are still relevant and they do get updates.
You cannot dual boot from grub menu unless both systems are UEFI or both systems are BIOS boot. If not in same mode you still can dual boot from UEFI/BIOS menu or one time boot key.
Intel graphics chips only have the open source driver, but newer chips often need a boot parameter to boot with correct video.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

    

And of course a good image backup of Windows is required as Vendors do not provide Windows media to reinstall. Some users accidentally overwrite Windows, there is a bug on reinstall of Ubuntu that may totally erase Windows, and some users intentionally erase Windows then later find one game or application they have to have Windows for.

---

### Post by salsify2 on 2014-12-29
Thanks oldfred, but those detailed info posts are exactly the sort of information that totally goes over my head just because of all of the implicit understandings that they contain. But if I take your meaning correctly, you're saying to my original question: no, it's impossible to tell whether it's going to be possible to install a Xubuntu-only OS on a current hardware with UEFI, and if it fails, it is likely to be impossible for me to figure out from resources like this how to fix it.

---

### Post by oldfred on 2014-12-29
You should be able to install in UEFI mode.
You may have to make some settings besides secure boot off, fast boot in Windows and perhaps UEFI, turn on USB ports for booting and maybe other settings.
Some work easier than others, but that is why we are here. Even if you have to post screen shots of UEFI menu, we should be able to help.

---

### Post by salsify2 on 2014-12-29
Okay, thanks for the clarification, oldfred&#8212;I appreciate it. I guess I'll give the order a try and see what happens.

---


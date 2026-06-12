---
title: "Grub not appearing after new Ubuntu install."
date: 2008-09-17
forum: New to Ubuntu
---

### Post by Amablue on 2008-09-17
I just recently got a new computer with windows preloaded on it. I installed a second harddrive in it and just finished putting ubuntu on the second harddrive. However, when I restarted the computer didn't show the Grub menu, it went straight into windows. I tried reloading the MBR but the instructions were a little too vague to help me. Could someone walk me through this?

I've done it before for two partitions on the same drive; I don't know why this isn't working like it should.

---

### Post by northern lights on 2008-09-17
GRUB should have been setup regardless of where you installed Ubuntu.

Anyhow, you might want to check [http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

---

### Post by Pelham123 on 2008-09-17
Just an off-chance...anything to do with your BIOS setup and hard-disk priority for booting?

I have similar setup and if my BIOS is set to the XP HDD it will boot straight into XP bypassing GRUB.

---

### Post by Amablue on 2008-09-17
> **Pelham123 said:**
> Just an off-chance...anything to do with your BIOS setup and hard-disk priority for booting?

I have similar setup and if my BIOS is set to the XP HDD it will boot straight into XP bypassing GRUB.

That may be it. Will the Super Grub Disk handle that, or is there something I else I should be doing instead?

Also, I don't know how relevant it is, but my computer was set up with a SATA harddrive. Not thinking about this at the time, I bought an IDE harddrive. By the time I realized this I had already waited past the return date and opened the packaging, so I just bought an IDE card for my computer. So as it stands now, my windows drive SATA, while the second drive is IDE and hooked in to the motherboard with an IDE card.

---

### Post by northern lights on 2008-09-17
The Disk would be useful if GRUB had not been properly installed.

Should Pelham's suggestion be correct, she Disk would not be of help.

GRUB can be installed to the MBR, but also to a secondary partitions boot sector. If the Windows bootloader (most likely NTLoader) is alone in residing in the MBR and the BIOS is set to boot from it, it not even notice GRUB's presence.

Then, you'd have to tinker with your BIOS settings. Hit 'DEL' (most likely, that's the key) when it says "Press DEL to enter setup" or the like during boot.

---

### Post by Amablue on 2008-09-18
I used the disk and got grub to appear. When I select ubuntu I get 

"Error 17: Cannot mount selected partition"

What now?

---

### Post by hellion0 on 2008-09-18
Just a thought... sometimes GRUB *doesn't* install during an Ubuntu install. Even with Hardy. My desktop's one of those - GRUB failed to install, but LILO's on it.

Doesn't sound like the issue here (mine boots directly to Linux unless I intervene), but just food for thought for the "helpers".

That all said, Error 17 in Grub means it can't ID the partition type.

Start the computer from a LiveCD and run the partitioner. Don't partition anything with it, just observe what's there. If you let Ubuntu install as default, its partition should be ext3.

---

### Post by Amablue on 2008-09-18
I suppose I should've searched before posting. I figured out what to do, I had to swap out hd0 for hd1 since it's the second harddrive that has ubuntu. 

Thanks to all who helped.

---


---
title: "Doesn't start. Reboots after &quot;Starting up..&quot;"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by kparacha on 2008-09-25
I'm using version Ubuntu 8 and it was working perfectly well. Until a power failure last night, the system was forced shut down. In morning when I switch it on, it comes to "Starting up.." and then reboots. This goes on forever! 

I am new to Ubuntu and detailed help will be highly appreciated!

---

### Post by didac on 2008-09-25
After BIOS checkup press any key to enter the GRUB menu. Choose Recovery Mode and post whatever happens.

---

### Post by kparacha on 2008-09-25
> **didac said:**
> After BIOS checkup press any key to enter the GRUB menu. Choose Recovery Mode and post whatever happens.

The last line that comes is:

"Setting up additional PCI resources" 

After this the system reboots. It's on and off, sometimes the system boots fine and sometimes it just continuous to reboot, Help appreciated! Thanks!

---

### Post by halitech on 2008-09-25
do you have a LiveCD kicking around? If you do, try booting from that and see if it reboots as well. If it does, you might have a hardware problem with yor motherboard

---

### Post by kparacha on 2008-09-25
> **halitech said:**
> do you have a LiveCD kicking around? If you do, try booting from that and see if it reboots as well. If it does, you might have a hardware problem with yor motherboard

The live CD boots fine

---

### Post by kparacha on 2008-09-25
> **kparacha said:**
> The live CD boots fine

Sorry, it doesn't book from the Live CD either.

---

### Post by halitech on 2008-09-25
where does the Live CD fail? At about the same time frame?

---

### Post by kparacha on 2008-09-26
> **halitech said:**
> where does the Live CD fail? At about the same time frame?

Yes, at about the same time frame. Strange...

---

### Post by halitech on 2008-09-26
I think we can assume the hard drive itself is fine so we are looking elsewhere for your problems. Try booting the LIve CD again and there should be an option for Memtest, run that and see if there are any issues with your memory. If that works, either looking at the mainboard or the cpu as being the issue.

---

### Post by kparacha on 2008-09-26
> **halitech said:**
> I think we can assume the hard drive itself is fine so we are looking elsewhere for your problems. Try booting the LIve CD again and there should be an option for Memtest, run that and see if there are any issues with your memory. If that works, either looking at the mainboard or the cpu as being the issue.

Thanks, will check and see. Though XP worked perfect on the same machine for over a year and Ubuntu crashed only a few days after installation!

---

### Post by Vince4Amy on 2008-09-26
> Thanks, will check and see. Though XP worked perfect on the same machine for over a year and Ubuntu crashed only a few days after installation!

You can't blame Ubuntu for a possible hardware problem, try resetting the BIOS.

---


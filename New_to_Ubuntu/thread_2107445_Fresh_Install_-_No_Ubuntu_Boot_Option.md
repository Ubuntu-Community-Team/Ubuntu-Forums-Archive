---
title: "Fresh Install - No Ubuntu Boot Option"
date: 2013-01-21
forum: New to Ubuntu
---

### Post by geoffdudds on 2013-01-21
Hello there,

I just installed Ubuntu 12.10 on my lenovo G550. I created a logical partition using Partition Wizard then booted from a USB bootable Ubuntu that I had been trialling. Everything went well, I went with the "other" option when selecting how to install it - i found my partition, then split it into 3. One for /, one for /home, and one for /swap. The installation completed successfully and requested a restart. 

Upon restart, I hit F12 to get to boot option, but here was no Ubuntu option. 

I did a little reading and ran boot-repair. It reinstalled grub2 and gave me this link for this forum: 

[http://paste.ubuntu.com/1557413/](http://paste.ubuntu.com/1557413/)

Any ideas?

One idea I had - the list I get at boot does not look like what I see when I google grub2. Is it possible my lenovo's OEM bootloader is superceding it and not recognizing Ubuntu? Does that even make sense?

thanks in advance,

Geoff

---

### Post by Rubi1200 on 2013-01-22
Hi and welcome to the forums :-)

the link is not working for me. try running and posting again.

One possibility is that GRUB was not correctly installed, but we need to see the results of the script to confirm this.

Thanks.

---

### Post by geoffdudds on 2013-01-22
You know what, I managed to get it figured out. I knew that would happen when I finally broke down and posted. You are correct, grub was not properly installed. I followed [this procedure]("http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/#.UP4y03b0Fok") and it worked like a charm. 

thanks!

Geoff

---

### Post by Rubi1200 on 2013-01-22
Excellent! Glad you got things sorted out.

Please mark this thread Solved using the Thread Tools near the top of the page so others can find a solution too.

Thanks.

---

### Post by audiomick on 2013-01-22
> **geoffdudds said:**
> Hello there,

I just installed Ubuntu 12.10 ...The installation completed successfully and requested a restart. 

Upon restart, [COLOR="Red"]I hit F12 to get to boot option[/COLOR], but here was no Ubuntu option. 

Just for the record, you shouldn't have to do this. When you have set up a dual boot, the computer should boot into grub by itself. You shouldn't have to do anything to make it go there.

F12 is possibly the key to interrupt the boot process and get to the computer's own boot menu, to select which device to boot from. That would explain this

> One idea I had - the list I get at boot does not look like what I see when I google grub2....

If you are having to hit a key to be able to choose the drive that your OS is on to boot, you need to go into BIOS and correct the boot order.

---


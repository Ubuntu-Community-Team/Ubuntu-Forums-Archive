---
title: "Boot issue - fresh install of 18.04.1 over a previous Fedora install - no such device"
date: 2019-01-28
forum: New to Ubuntu
---

### Post by cuhulainn on 2019-01-28
Hello all!
I'm  brand new to Linux and Ubuntu, after having just received this laptop  from a Red Hat developer.  They had Fedora installed. When the computer  boots, there are 3 options to choose from:
> 
Fedora (4.15.4-300. fc27. x86_64) 27 (Workstation Edition)

Fedora (4.13.9-300. fc27. x86_64) 27 (Workstation Edition)

Fedora (0-rescue-*randomcharacterjumble*) 27 (Workstation Edition)



No matter which one I pick, I get the following errors:
> 
error: no such device: *messofcharactersandhyphens*
error: file 'vmlinuz 4.15.4-300. fc27. x86_64' not found.
error: you need to load the kernel first.

Note that the second line does vary depending on which option I choose initially.

I  seemingly successfully performed a clean install of 18.04.1 from a  flash drive, using the delete everything option to wipe the drive and do  the fresh install.  However, the boot screen is unaffected.

I  did some research and found boot-repair.  Used the flash drive to load  Ubuntu, installed and ran boot-repair.  It said it worked ("Boot  repaired successfully"), however the issue persists just as it was  before.

Here's the pastebin that resulted from that attempt:[http://paste.ubuntu.com/p/nq8PyYNDk9/](http://paste.ubuntu.com/p/nq8PyYNDk9/)

Would anyone have any insights they can share?

Let me know if additional info is needed.

Trying to use this laptop to start CS50x and learn me some coding!

---

### Post by cuhulainn on 2019-01-29
I figured it out... I  didn't really solve the issue in an inspiring way, but I did get it to  boot into my Ubuntu install.  Just got into the BIOS and changed the  boot order.   I'd like to understand it better and actually clean up the  MBR, but I'm up and running at least.  If anyone sees this and can help let me know!

---

### Post by oldfred on 2019-01-29
You can delete the /EFI/fedora folder in the ESP.
You can delete the UEFI fedora boot entries.
And Boot-Repair saw all the fedora entries and added them again to grub in 25_custom.

       # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
#to edit or turn off execute bit (as above) to totally remove. 25_custom is only created by Boot-Repair, not part of standard grub.
sudo nano /etc/grub.d/25_custom  
# Then do:
sudo update-grub 
    
       sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

---


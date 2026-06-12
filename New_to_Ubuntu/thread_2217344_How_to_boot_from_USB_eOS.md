---
title: "How to boot from USB eOS"
date: 2014-04-16
forum: New to Ubuntu
---

### Post by Andrew_Sunde on 2014-04-16
Hey, so I have a 2006 model macbook that I installed refit and used that to boot from usb and install linux mint (dual boot SOX and mint).
Then, I decided to try elementary OS, so once again, booted from usb using refit, but decided to remove OSX and mint, so I installed eOS from usb and that worked great.
I no longer have refit, and I would like to boot my computer from USB to install ubunto, but I don't know how to without refit.
Is there anyway to install refit or any starup key I can press to boot from a live USB in eOS?
I dont care about any data on my computer. I would be happy with an install of ubunto and ubunto only.

---

### Post by jmbell on 2014-04-16
I'm not sure if this will work in eOS; however, I've had good luck using this method with other distros to generate a bootable USB. 

First, unmount the USB with ```
 sudo umount /dev/sdb1 
``` where you'll replace sdb1 with whichever device corresponds to your usb. Then, use this command to create a bootable disk ```
 sudo dd if=/full/path/to/some-file.iso of=/dev/sdb bs=1M 
``` where, again, sdb corresponds to the usb drive. You need to be 100% sure that you correctly identify the usb's device label and not use another letter or append a number (for example, sdb1 is not acceptable). If the label isn't correct, you'll erase all data on the drive you reformat. If you use sdb1, your device will not be bootable.

Once you've got the OS onto your USB drive, it should be straightforward to adjust BIOS to boot it first so you can install Ubuntu or any other OS for which you have an .iso file.

If doing this doesn't work, you could try using a program such as unetbootin to create your bootable usb device. Others are also available if you run a search for them, but this one has become my favorite gui for this task.

---


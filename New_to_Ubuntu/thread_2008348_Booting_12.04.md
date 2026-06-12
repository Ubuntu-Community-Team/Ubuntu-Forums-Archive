---
title: "Booting 12.04"
date: 2012-06-22
forum: New to Ubuntu
---

### Post by cdmjjp on 2012-06-22
Hi - I tried to upgrade to 12.04 through the update manager but due to internet problems I changed to the Flash drive ISO option. This worked fine. I downloaded the OS, configured the desktop to the way I like it, etc and shut down for the night. The following day I started the computer with no luck. I could not boot into Windows Vista, Ubuntu 12.04 or the older versions. I only get the message. Error on file .... grub>. However when I boot up using the USB it works and then I can remove the USB drive and carry on as normal. Can anyone solve this issue? I would like to access Windows vista and Ubuntu 12.04 and not just 12.04

---

### Post by oldfred on 2012-06-22
When you say you can boot from USB flash, is that just the liveUSB or the full install on the hard drive.

If you can boot the install on the hard drive, grub2's boot loader may have just installed to the wrong MBR. Grub defaults to sda, but a few BIOS promote a flash drive to sda and grub2's boot loader ends up on the wrong drive.

#If that is the case:
sudo fdisk -lu
# confirm which drive Ubuntu is installed on sda or sdb?
# then install the grub2 boot loader to that drive sda shown use sdb if required.
sudo grub-install /dev/sda

If just booting liveUSB download this into liveCD and run the Boot-Info report:

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---


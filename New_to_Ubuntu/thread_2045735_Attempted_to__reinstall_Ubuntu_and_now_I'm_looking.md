---
title: "Attempted to  reinstall Ubuntu and now I'm looking at grub rescue"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by BTXNick on 2012-08-21
What I've done in the past is just delete the linux partition from windows and then restart the computer. Then I change the boot order so it boots from usb and install ubuntu, which reinstalls grub and then I can get back into windoze again. I swear I've done this on this computer before(not THIS one, writing from a netbook, but the one I just bricked). But now I cannot get into the BIOS. when the ASUS splash screen comes up it doesn't tell me which button to press to get into the BIOS. I've tried F2, F9-F12, the delete and home keys. No idea how the hell I'm supposed to get in there. I know I've done it before though because I installed Ubuntu in the first place! 


So now I'm looking at "error: uknown filesystem. grub rescue>"

The only command that works is ls and it returns (hd0) (hd0, msdos6) (hd0, msdos5) (hd0, msdos1) (hd1) (hd1, msdos1)

I've seen other threads about this but none really amount to my problem. I'm looking for a windows recovery disk because that may help fix my problem according to another thread, but I'm not sure.


If anyone can point me in the right direction I'd be much obliged.



EDIT: FINALLY got into the BIOS with F2 somehow, but now having trouble setting boot order, as it's not very intuitive.

EDIT2: Was able to change boot order to boot from USB first, but it's still going to grub rescue, dammit.

EDIT3: it wants me to set a path for boot option. I have no idea what to even put...

---

### Post by Bashing-om on 2012-08-21
--Nick ; Hi !  Welcome to the forum.

  Try this to boot your system:
from a live CD (or usb source)
```
sudo fdisk -l
``` to find the boot partition.. will be flaged with "*".
```
sudo mkdir /mnt/boot
  sudo mount /dev/sdaY 
  sudo grub-install --root-directory=/mnt/sda
  sudo update-grub

```Note the Y in sdaY..replace Y with the partition NUMBER from the "fdisk" command. This also assumes you only have the one disk installed and it is seen as "sda".
copy and paste (for accuracy) and advise.
[INDENT]regards <==BDQ

[/INDENT]

---

### Post by oldfred on 2012-08-22
A lot of newer users like a gui to fix things:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by Wim Sturkenboom on 2012-08-22
> 
EDIT2: Was able to change boot order to boot from USB first, but it's still going to grub rescue, dammit.

That implies that it can't boot from USB and hence tries to boot from HD. Your usb stick / drive might be corrupted.

> 
EDIT3: it wants me to set a path for boot option. I have no idea what to even put...

Maybe [http://www.troubleshooters.com/linux/grub/grub.htm](http://www.troubleshooters.com/linux/grub/grub.htm) can be of help; not sure if it's for grub or grub2

---


---
title: "boot in recovery mode with read write"
date: 2013-02-09
forum: New to Ubuntu
---

### Post by kanjah on 2013-02-09
Hi guyz, ave installed ubuntu server 12amg64, i need to boot in recovery mode so as to make change on the /etc/default/grub file, but in recovery mode i have only read privileges, i have tried using chmod 777, 775, to no avail, is there a way to go around this?

---

### Post by Cheesemill on 2013-02-09
The following command will remount the root partition with read/write access...
```
mount -o rw,remount /
```

---

### Post by kanjah on 2013-02-09
Hi cheesemill, thanks for the reply, tried the mount -o rw, remount /, the condition is still the same, do i need put another command after this?

---

### Post by brent1975 on 2013-02-09
Try it without the rw.
```
 mount -o remount/
```

Also rebooting will sometimes let rw again.

---

### Post by kanjah on 2013-02-09
Hi brent1975, tried it without the rw, the system is still in read only mode, even after restart

---

### Post by Cheesemill on 2013-02-09
> **kanjah said:**
> Hi cheesemill, thanks for the reply, tried the mount -o rw, remount /, the condition is still the same, do i need put another command after this?
Did you make a typo? There is no space between , and remount.

Also do you have problems booting? If not you can edit /etc/default/grub when booted normally, you don't have to be in recovery mode to edit this file.

---

### Post by kanjah on 2013-02-09
hi chessmill, am tying to add  "quiet drm_kms_helper.poll=0", editing it normall seems hard since i get a continious error message

---

### Post by Cheesemill on 2013-02-09
What error message?

If it's just that you don't have permission then that is to be expected, you can't edit system files as a normal user. To edit the file open a terminal and type...
```
gksudo leafpad /etc/default/grub
```
When you've edited and saved the file then type
```
sudo update-grub
```
to update grub with the new configuration.

---

### Post by kanjah on 2013-02-09
hi chessmill, {drm} nouveau 0000:28:00.0: no native mode, forcing panel scaling
is the error that i get, when i try to edit the GRUB_CMDLINE_LINUX_DEFAULT, the {drm} nouveau 0000:28:00.0: no native mode, forcing panel scaling keeps on pasting itself, so i opted to edit the grub from the Recovery mode root terminal

---

### Post by grahammechanical on 2013-02-09
May I make a suggestion? I have not tried this on a server. I have no experience of servers. I can get to a Root shell prompt from Recovery Mode and with the files system in read/write mode.

I first go into Failsafe mode and than back out at the screen that appears. I think we press Esc to get back to the Recovery Mode screen options.

Now I select Root = Drop to root shell prompt. You will find that you now have a file system that you can write to as well as read.

Because Failsafe is going to load the OS it puts the file system into read/write mode. Do not follow through into boot into failsafe mode. Back out to the recovery mode options and select Root.

Regards.

---

### Post by kanjah on 2013-02-09
Hi grahammechanical, thanks for the reply, how do i log on into fail safe?

---


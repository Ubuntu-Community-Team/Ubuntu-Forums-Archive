---
title: "Unable to boot into ubuntu  [Kinit : No resume image found"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by rraj.be on 2008-06-23
when i boot into my ubuntu its displaying the progress screen.

Then its displaying the following
```

Kinit : name_to_dev_t(/dev/disk/by-uuid/64190218-2559-41ac-b167-a09920fbee4) = sda(8,6)
kinit : trying to resume from /dev/disk/by-uuid/64-190218-2959-41ac-b167-a099207fbee4
Kinit : No resume image , doing normal boot ...

ubuntu 8.04 raj_desktop tty1

raj-desktop login
```

I have attached a screen shot too.

What should i do now.

---

### Post by Yuki_Nagato on 2008-06-23
This internet user seems to have stumbled across a solution on launchpad.  I cannot say if this works or not, as I have not used it myself.

[The Article]("http://mowyourlawn.com/blog/?p=73")

[The Launch Pad]("https://bugs.launchpad.net/ubuntu/+bug/103148")

---

### Post by rraj.be on 2008-06-23
Any help please.Sorry for the bump.

---

### Post by aysiu on 2008-06-24
It's not really a problem, actually.

If you want the message to go away, though, you can try this.

Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo nano -B /boot/grub/menu.lst
``` This will open the boot configuration file in the text editor Nano while also making a backup copy. In the file, find your kernel line. Mine, for example, is ```
title           Ubuntu 7.10, kernel 2.6.22-15-generic
root            (hd0,0)
**kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=3ad3b81e-7391-4721-a6f9-b38e50a0f9da ro quiet**
initrd          /boot/initrd.img-2.6.22-15-generic
quiet
``` Since you're using 8.04, your line will look slightly different. That's okay. Append the word *noresume* the line. For example: ```
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=3ad3b81e-7391-4721-a6f9-b38e50a0f9da ro quiet **noresume**
``` Then save (Control-X, Y, Enter).

---


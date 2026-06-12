---
title: "Kernel 2.6.24.17"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by EvilBro on 2008-05-26
Today I updated my installation and one of the updates was 'kernel 2.6.24.17'. During the update I was asked the question whether I wanted to keep my menu.lst (for grub) and for some reason I decided to reply to this question by pressing 'yes'. Now my setup obviously doesn't get that there is a newer kernel on the system it can use. Would copying an entry in menu.lst and changing 2.6.24.16 to 2.6.24.17 rectify this problem?

---

### Post by Eisenwinter on 2008-05-26
Check your /boot folder, there should be initrd-2.6.24.17, and a vmlinuz-2.6.24.17 files in there.

Just change your GRUB menu.lst entries to include those boot files, instead of the ones for 2.6.24.16.

I still recommend leaving an option for 2.6.24.16 just in case something has gone wrong with the new kernel.
When I compiled my first kernel it took me 2 menu.lst configuration tries to get it to boot, I left the older one though, which is how I was able to get into the system the second time, heh.

---

### Post by drs305 on 2008-05-26
Backup existing menu.lst:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.list-'date %F'
```

Then run this. It should update grub:
```
sudo update-grub
```

There is also an option in StartUp-Manager to select the kernel to use.

---


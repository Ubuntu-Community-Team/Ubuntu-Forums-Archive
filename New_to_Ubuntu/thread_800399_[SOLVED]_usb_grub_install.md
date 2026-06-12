---
title: "[SOLVED] usb grub install"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by noorez on 2008-05-19
I tried to install grub to a usb device using these instructions:

1. format usb disk to FAT.
2. copy /usr/lib/grub/i386-pc/stage* /media/disk/boot/grub/
3. grub > root (hd1,0)
4. grub > setup (hd1)
5. quit

to test it i booted from the usb disk (note: hd1 is now the hard drive on my computer, hd0 is the usb disk since i booted from it)

to boot into ubuntu i did this:

grub> root (hd1,4)
grub> kernel /boot/vmlinz....  root=/dev/sda5 ro quiet splash
grub> initrd /boot/initrd...  
grub> boot

this worked.

when i tried to boot into windows xp i did this:

grub> root (hd1,0)
grub> makeactive
grub> chainloader +1
grub> boot

this hands on the "Starting up..."

---

### Post by meierfra. on 2008-05-19
try

grub> root (hd1,0)
grub> makeactive
grub> map (hd0) (hd1)
grub> map (hd1) (hd0)
grub> chainloader +1
grub> boot

(actually you can skip the "makeactive", since I'm sure the Windows partition already has a boot flag)

---

### Post by noorez on 2008-05-19
ok....looking at the map command on grub commands, you need that when chainloading os's on a non-first drive. however looking at the two map commands, i'm a bit confused...

map (hd0) (hd1)
  this would make the usb disk map to (hd1)
but then it looks like map (hd1) (hd0) just maps (hd0) back to itself ?...

or did i miss something?

also, would this be possible to pre-configure so that this always happens ?

---


---
title: "Can't dtect CDRom"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by jamil_1 on 2008-07-16
Ubuntu is not detecting my newly installed CDROM. I have restarted PC many times but still nothing has changed. I have CDROM as slave device bcz I have only one IDE port but two IDE devices: HDD and CDROM.

U can find lspci result at: [http://paste.ubuntu.com/27709/](http://paste.ubuntu.com/27709/)
and lshw -C disk -C storage at : [http://paste.ubuntu.com/27707/](http://paste.ubuntu.com/27707/)
and dmesg output at: [http://paste.ubuntu.com/27711/](http://paste.ubuntu.com/27711/)

---

### Post by philinux on 2008-07-16
Whats happens if you put the live cd in and boot up, does the bios see the drive.

---

### Post by jamil_1 on 2008-07-16
I haven't tried the LiveCD but I can see CDROM in bios

---

### Post by philinux on 2008-07-16
Well try the livecd to make sure that you know the cdrom works for sure.

---

### Post by rraj.be on 2008-07-16
What happens when you run this command
```

sudo mkdir /media/cdrom1

sudo mount /dev/src1 /media/cdrom1
```

---


---
title: "Can i install HH without burning it to cd?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by sharks on 2008-04-27
I ahve downloaded HH and Can i install HH without burning it to cd?

---

### Post by Google Spider on 2008-04-27
I think you need to burn the cd even if you want to install it in windows using wubi. Why do you want to do this? Problem burning the iso?

---

### Post by jimv on 2008-04-27
You can try it from a thumbdrive.  That's how I got it onto my laptop (for some reason the CD wouldn't work).

[http://learn.clemsonlinux.org/wiki/Ubuntu:Install_from_USB_drive](http://learn.clemsonlinux.org/wiki/Ubuntu:Install_from_USB_drive)

---

### Post by benhur99ph on 2008-04-28
I did it using Wubi. I just placed the Ubuntu ISO file on C:\ubuntu\install then run Wubi. It recognized my ISO and the install went on for about 10 mins or so.

---

### Post by talsemgeest on 2008-04-28
Or you can mount the iso and then run wubi from it. In ubuntu you can mount it with gmount-iso: ```
sudo apt-get install gmount-iso
```

---


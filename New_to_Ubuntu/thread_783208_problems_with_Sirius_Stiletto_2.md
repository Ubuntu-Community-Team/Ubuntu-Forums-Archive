---
title: "problems with Sirius Stiletto 2"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by drascus on 2008-05-05
I have been trying to connect my new Sirius Stiletto 2 to my ubuntu machine and it doesn't seem to work. For some reason my computer won't mount it at all. no disk Icon appears on the desktop and under places->computer nothing appears. Any ideas as to what could be wrong it should work under Gnomad according to things I have looked up.

---

### Post by mustang on 2008-05-05
I'll get the ball rolling. Plug it in, run "dmesg" in the terminal, paste the results here.

---

### Post by drascus on 2008-05-05
OK I am at work right now I will do it when I get home.

---

### Post by drascus on 2008-05-05
OK here is what I get I pretty much only included the USB entries because I thought they would be the most relevant let me know if you need more to helo figure it out. 

  409.562697 audit(1210038836.121:3): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=7868 profile="/usr/sbin/cupsd" namespace="default"
  411.493189 usb 2-1: new full speed USB device using uhci_hcd and address 2
  411.503910 usb 2-1: configuration #1 chosen from 1 choice
  411.680486 usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0x7E04
  411.681113 usbcore: registered new interface driver usblp
  413.444907 usblp0: removed
  720.772997 usb 5-4: new high speed USB device using ehci_hcd and address 7
  720.906692 usb 5-4: configuration #1 chosen from 1 choice
  722.267224 usb 5-4: USB disconnect, address 7
  722.639504 usb 5-4: new high speed USB device using ehci_hcd and address 8
  722.773380 usb 5-4: configuration #1 chosen from 1 choice

---

### Post by drascus on 2008-05-06
Bump...

---

### Post by wimac on 2011-08-02
The stilletto 2 uses mtp you could use a program like gnomad2 or just mount it using mtpfs.


```

$ sudo apt-get install mtpfs
$ sudo mkdir /media/stilletto
$ sudo sudo mtpfs /media/stilletto

```

---


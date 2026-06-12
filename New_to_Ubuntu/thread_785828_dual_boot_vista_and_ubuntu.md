---
title: "dual boot vista and ubuntu"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by cartesian on 2008-05-07
Hope I can get some help here in this forum, so thanks in anticipation!

I have a laptop with vista installed. I shrank one partition using vista's own tool and installed ubuntu.

The installation appeared to go well. The problem is when I reboot.  I get the grub menu and if I select vista, it boots into vista no problem. If I leave it to boot into ubuntu I get the error "Error 17: cannot mount selected partition". I can't access ubuntu at all unless I use the live cd.

I would be grateful for any help pitched to a beginner in linux.

Thanks again

---

### Post by briandu on 2008-05-07
Do not know if you have given up.


May i suggest the following:   (note hda is your first hard drive assuming the drive is IDE/SATA and not SCSI)
Easiest is to boot up from live cd and open terminal then

sudo grub-install /dev/hda

and this should pickup your win and Linux

---

### Post by cartesian on 2008-05-08
Thanks briandu,

I've tried that and got this result:

ubuntu@ubuntu:- $ sudo grub-install /dev/hda
Probing devices to guess BIOS drives. This may take a long time.
/dev/hda: Not found or not a block dvice.
ubuntu@ubuntu:- $

I hope you can have another think.

Thanks

---


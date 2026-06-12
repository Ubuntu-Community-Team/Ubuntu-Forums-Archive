---
title: "USB mounting issues - hit and miss!!"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by beerguzzler on 2008-06-23
Like the title suggests, my usb mounting since the last set of updates has become very strange.

USB devices such as keyboard, mouse, printer, webcam all start and are usable

My problem lies with memory sticks and my camera (Nikon D40). Up until the last security updates they worked fine. If I plug one of the sticks in it will automount and then die completely after a few mins (somewhat annoying when your in the middle of data transfer!). It'll come back with "media: /dev/sdb1 is not a valid block device

The only way I can then get the stick to mount is if I reboot with the stick still attached. If I then unmount and try and remount, it will sometimes mount but mostly I'm back with the error message.

The stick itself is fine and works ok on Microsh@ft systems. I do not just unplug the stick from MS either, I do the safe eject procedure.

Any advise offered is greatly appreciated. Without USB mounting I'm afraid I'm gonna have to switch back to MS and that I do not want, but it may have to be a necessary evil unless/until this bug(?) is corrected.

Thanks.

---

### Post by ajgreeny on 2008-06-23
Are your sockets on the machine OK?  Try a different socket just in case.

---

### Post by beerguzzler on 2008-06-23
I've tried them in different ones with the same problems

---

### Post by spiderbatdad on 2008-06-23
There is a program called usbmount in synaptic. It may resolve the problem.

---

### Post by beerguzzler on 2008-06-23
Think I've solved it.

Booted up with the memory stick in the m'board usb and it's not failed. Previously I'd been using the built in ones with the monitor for ease of use.

Seem to remember a while ago there was a problem with usb hubs and the like. Guess that's still an issue. Just a bit weird that it used to work

---

